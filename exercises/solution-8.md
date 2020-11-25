# Exercise Session 8, Solutions

## Question 1

1. Write a `given` definition to create `Eq[List[T]]` from a `Eq[T]`.

```scala
given EqList[T](using Eq[T]) as Eq[List[T]] {
  extension (x: List[T])
    def === (y: List[T]): Boolean =
      (x, y) match
        case (hx :: tx, hy :: ty) => hx === hy && tx === ty
        case (Nil, Nil) => true
        case _ => false
}
```

2. Write a `given` definition to create `Eq[(T, U, S)]` from `Eq[T]`, `Eq[U]` and `Eq[S]`.

```scala
given EqTriple[T, U, S](using Eq[T], Eq[U], Eq[S]) as Eq[(T, U, S)] {
  extension (x: (T, U, S))
    def === (y: (T, U, S)): Boolean =
      x._1 === y._1 && x._2 === y._2 && x._3 === y._3
}
```

3. Write `given` definitions to create `Eq[Person]`. Make use of both the definitions you have written previously.

```scala
given EqString as Eq[String] {
  extension (x: String)
    def === (y: String) = x == y
}

given EqInt as Eq[Int] {
  extension (x: Int)
    def === (y: Int) = x == y
}

given EqPerson(using Eq[(String, Int, List[String])]) as Eq[Person] {
  extension (a: Person)
    def === (b: Person) =
      (a.name, a.age, a.neighbours) === (b.name, b.age, b.neighbours)
}
```

4. Explicitly write the `given` argument to `summon` (you may need to assign names to your `given` definitions):

```scala
summon[Eq[Person]](using
  EqPerson(using
    EqTriple(using
      EqString,
      EqInt,
      EqList(using EqString)
    )
  )
)
```

## Question 2

1. Write explicitly the `given` argument to `add` (it may help to write all type parameters explicitly):

```scala
add(S(Z), S(S(Z)))(using
  sumS(using
    sumZ(using S(S(Z)))
  )
)
```

2. Similarly to `Sum`, write `given` definitions that create an instance of the
`Product[N, M, R]` type-class, representing the evidence that `N * M = R`.

```scala
given [N <: Nat] as Prod[Z, N, Z] = Prod(Z)
given [N <: Nat, M <: Nat, R1 <: Nat, R2 <: Nat](using
  prod: Prod[N, M, R1],
  sum: Sum[R1, M, R2]
) as Prod[S[N], M, R2] =
  Prod(sum.result)

def prod[N <: Nat, M <: Nat, R <: Nat](n: N, m: M)(
  using prod: Prod[N, M, R]
): R = prod.result
```
