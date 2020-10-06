# Exercise Session 2, Solutions

## Question 3.1

```scala
def curry2(f: (Double, Int) => Boolean): Double => (Int => Boolean) =
  (x1: Double) => (x2: Int) => f(x1, x2)
```

## Question 3.2

```scala
def uncurry2(f: Double => Int => Boolean): (Double, Int) => Boolean =
  (x1: Double, x2: Int) => f(x1)(x2)
```

## Question 4.

```scala
def fixedPoint(f: Int => Int): Int => Int = {

  @tailrec
  def rec(x: Int): Int = {
    val y = f(x)
    if x == y then x else rec(y)
  }

  rec
}
```
