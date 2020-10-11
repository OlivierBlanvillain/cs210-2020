# Exercise Session 4

Variance and Pattern Matching

This week, we will work on the idea of variance, and on pattern matching. Recall that

- Lists are covariant in their only type parameter.
- Functions are contravariant in the argument, and covariant in the result.

## Question 1

Consider the following hierarchies:

```scala
abstract class Fruit
class Banana extends Fruit
class Apple extends Fruit
abstract class Liquid
class Juice extends Liquid
```

Consider also the following typing relationships for `A`, `B`, `C`, `D`: `A <: B` and `C <: D`.

Fill in the subtyping relation between the types below. Bear in mind that it might be that neither type is a subtype of the other.

| Left hand side             | ?:  | Right hand side              |
|                       ---: | --- | :---                         |
| List[Banana]               |     | List[Fruit]                  |
| List[A]                    |     | List[B]                      |
| Banana => Juice            |     | Fruit => Juice               |
| Banana => Juice            |     | Banana => Liquid             |
| A => C                     |     | B => D                       |
| List[Banana => Liquid]     |     | List[Fruit => Juice]         |
| List[A => D]               |     | List[B => C]                 |
| (Fruit => Juice) => Liquid |     | (Banana => Liquid) => Liquid |
| (B => C) => D              |     | (A => D) => D                |
| Fruit => (Juice => Liquid) |     | Banana => (Liquid => Liquid) |
| B => (C => D)              |     | A => (D => D)                |

## Question 2

The following data types represent simple arithmetic expressions:

```scala
abstract class Expr
case class Number(x: Int) extends Expr
case class Var(name: String) extends Expr
case class Sum(e1: Expr, e2: Expr) extends Expr
case class Prod(e1: Expr, e2: Expr) extends Expr
```

Define a function `deriv(expr: Expr, v: String): Expr` returning the expression that is the partial derivative of `expr` with respect to the variable `v`.

```scala
def deriv(expr: Expr, v: String): Expr = ???
```

Here's an example run of the function:

```scala
> deriv(Sum(Prod(Var("x"), Var("x")), Var("y")), "x")
Sum(Sum(Prod(Var("x"), Number(1)), Prod(Number(1), Var("x"))), Number(0))
```

## Question 3

Write an expression simplifier that applies some arithmetic simplifications to an expression. For example, it would turn the above monstrous result into the following expression:

```scala
Prod(Var("x"), Number(2))
```
