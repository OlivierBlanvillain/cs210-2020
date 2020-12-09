# Exercise Session 10, Solutions

## Question 1

```scala
def succ = (n => f => x => f(n(f)(x)))
```

## Question 2

```scala
def add = (n => m => n(succ)(m))
```

## Question 3

```scala
def size = (l => l(zero)( h => t => succ(size(t)) ))
```

## Question 4

```scala
def map = (f => l =>
           l(nil)( h => t => cons( f(h) )( map(f)(t) ) ))
```
