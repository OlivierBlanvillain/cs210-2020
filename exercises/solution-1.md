# Exercise Session 1, Solutions

## Question 3: Fast exponentiation

```scala
def fastExp(base: Int, exp: Int): Int = {
  require(exp >= 0)

  @tailrec
  def go(base: Int, exp: Int, acc: Int): Int = {
    if (exp == 0)
      acc
    else if ((exp % 2) != 0)
      go(base, exp - 1, base * acc)
    else
      go(base * base, exp / 2, acc)
  }
  go(base, exp, 1)
}
```

## Question 4: Tail recursive Fibonacci

```scala
def fibonacci(n: Int): Int = {
  require(n >= 0)

  @tailrec
  def go(k: Int, previous: Int, current: Int): Int =
    if (k == n) current
    else go(k + 1, current, previous + current)

  if (n == 0) 1 else go(1, 1, 1)
}
```
