# Lab 8: Type-Directed Programming (Codecs)

You can use the following commands to make a fresh clone of your repository:

```shell
git clone -b codecs git@gitlab.epfl.ch:lamp/students-repositories-fall-2020/cs210-GASPAR.git cs210-codecs
cd cs210-codecs
```

You can always refer to:
  * [the example guide](https://gitlab.epfl.ch/lamp/cs210/blob/master/labs/example-lab.md) on the development workflow.
  * [this guide](https://gitlab.epfl.ch/lamp/cs210/blob/master/labs/grading-and-submission.md) for details on the submission system.
    **Make sure to submit your assignment before the deadline written in [README.md](/README.md)**
  * [The documentation of the Scala standard library](https://www.scala-lang.org/files/archive/api/2.13.3)
  * [The documentation of the Java standard
    library](https://docs.oracle.com/en/java/javase/15/docs/api/index.html)


## Overview

The goal of this assignment is to implement a type-directed serialization library: it uses
type-directed operations to combine serializers for values of simpler types to construct
serializers for values of more complex types.

The serialization format is [JSON](https://www.json.org). Make sure to be familiar with
this format.

To make things easier,
the encoders and decoders implemented in this assignment don’t directly work with
JSON blobs, but they work with an intermediate `Json` data type:

~~~
sealed trait Json
object Json {
  /** The JSON `null` value */
  case object Null extends Json
  /** JSON boolean values */
  case class Bool(value: Boolean) extends Json
  /** JSON numeric values */
  case class Num(value: BigDecimal) extends Json
  /** JSON string values */
  case class Str(value: String) extends Json
  /** JSON objects */
  case class Obj(fields: Map[String, Json]) extends Json
  /** JSON arrays */
  case class Arr(items: List[Json]) extends Json
}
~~~

Here is an example of JSON value:

~~~
{
  "foo": 0,
  "bar": [true, false]
}
~~~

It can be represented as follows with the `Json` data type:

~~~
Json.Obj(Map(
  "foo" -> Json.Num(0),
  "bar" -> Json.Arr(Json.Bool(true), Json.Bool(false))
))
~~~

With this `Json` type being defined, **encoding** a value of type `A` consists
in transforming it into a value of type `Json`:

~~~
trait Encoder[-A] {
  def encode(value: A): Json
}
~~~

Unlike arbitrary JSON values, JSON objects have the special property that
two objects can be combined to build a bigger JSON object containing both
objects’ fields. We use this combining property of JSON objects to define
the `zip` method on `Encoder` returning JSON objects. We do so in a
subclass of `Encoder` called `ObjectEncoder`:

~~~
trait ObjectEncoder[-A] extends Encoder[A] {
  // Refines the encoding result to `Json.Obj`
  def encode(value: A): Json.Obj

  def zip[B](that: ObjectEncoder[B]): ObjectEncoder[(A, B)] = ...
}
~~~

Conversely, **decoding** a value of type `A` consists in transforming
a value of type `Json` into a value of type `A`:

~~~
trait Decoder[+A] {
  /**
    * @param data The data to de-serialize
    * @return The decoded value wrapped in `Some`, or `None` if decoding failed
    */
  def decode(data: Json): Option[A]
}
~~~

Note that the decoding operation returns an `Option[A]` instead of just
an `A` because the decoding process can fail (`None` means that it was
impossible to produce an `A` from the supplied JSON data).

Given instances of encoders and decoders are defined in the `GivenEncoders`
and `GivenDecoders` traits, respectively. These traits are inherited by the `Encoder`
and `Decoder` companion objects, respectively. By doing so, we make the given
instances automatically available, removing the need for explicitly importing them.

We provide you a `parseJson` function that parses a JSON blob in a `String` into
a `Json` value, and a `renderJson` function that turns a `Json` value into a JSON
blob in a `String`. You can use them to play with the encoders and decoders that
you write.

## Your Task

Your work consists in writing codec instances that can be combined together to build
codec instances for more complex types. You will start by writing instances for basic
types (such as `String` or `Boolean`) and you will end up writing instances for
case classes.

At any time, you can follow your progress by running the `test` sbt task.

### Basic Codecs

Start by implementing the given `Encoder[String]` and `Encoder[Boolean]` instances,
and the corresponding given `Decoder[Int]`, `Decoder[String]` and `Decoder[Boolean]`
instances.

Hint: use the provided methods `Encoder.fromFunction`, `Decoder.fromFunction`, and
`Decoder.fromPartialFunction`.

Make sure that your `Int` decoder rejects JSON floating point numbers.

### Derived Codecs

The next step consists in implementing a codec for lists of elements of type `A`, given
a codec for type `A`. The encoder instance for lists is already implemented. Fill in
the definition of the corresponding decoder.

Once you have defined the encoder and decoder for lists, you should be able to
**summon** them for any list containing elements that can be encoded and decoded.
You can try, for instance, to evaluate the following expressions in the REPL:

~~~
summon[Encoder[List[Int]]]
summon[Decoder[List[Boolean]]]
~~~

### JSON Object Codecs

Next, implement codecs for JSON objects. The approach consists in defining codecs
for JSON objects having a single field, and then combining such codecs to handle
JSON objects with multiple fields.

For example, consider the following JSON object with one field `x`:

~~~
{
  "x": 1
}
~~~

An encoder for this JSON object can be defined by using the provided
`ObjectEncoder.field` operation, which takes the field name as a parameter and
a given `Encoder` for the field value:

~~~
val xField = ObjectEncoder.field[Int]("x")
~~~

To define an encoder producing a JSON object with more than one field, you can
combine two `ObjectEncoder` instances with the `zip` operation. This operation
returns an `ObjectEncoder` producing a JSON object with the fields of the two
combined encoders. For instance, you can define an encoder producing an object
with two fields `x` and `y` as follows:

~~~
val pointEncoder: ObjectEncoder[(Int, Int)] = {
  val xField = ObjectEncoder.field[Int]("x")
  val yField = ObjectEncoder.field[Int]("y")
  xField.zip(yField)
}
~~~

Implement a `Decoder.field` operation corresponding to the `ObjectEncoder.field`
operation.

### Codecs for Case Classes

The `zip` operation mentioned in the previous section only returns codecs for tuples.
It would be more convenient to work with high-level data types (for instance, a
`Point` data type, rather than a pair of coordinates).

Both encoders and decoders have a `transform` operation that can be used to transform
the type `Json` values are encoded from, or decoded to, respectively. You can
see in the assignment how it is used to define a given `Encoder[Person]`.

Define a corresponding `Decoder[Person]`, and then define a given `Encoder[Contacts]`
and a given `Decoder[Contacts]`.

## Bonus Questions

- Can you **explicitly** write the value inferred by the compiler when it summons
  the `Encoder[List[Person]]`?
- Would it be possible to define codecs for optional fields?
- Would it be possible to define a function that provides a given instance of
  `Encoder[Option[A]]` for any type `A` for which there is a given `Encoder[A]`
  (like we do with `Encoder[List[A]]`)?
- Would it be possible to define codecs for sealed traits in addition to case
  classes?
