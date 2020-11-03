# Exercise Session 6, Solutions

## Question 1.1

```scala
// For equivalent cycles, we decide to return the cycle
// with the smallest element first.
def triangles(edges: DirectedGraph): List[(NodeId, NodeId, NodeId)] =
  for {
    e1 <- edges

    // The first node is the smallest of the cycle.
    if (e1._1 < e1._2)

    e2 <- edges

    // The two edges are connected and
    // there exists an edge between the two other end points.
    if (e1._2 == e2._1 && edges.contains((e2._2, e1._1)))

    // The first node is the smallest of the cycle.
    if (e1._1 < e2._2 && e2._1 != e2._2)

  } yield (e1._1, e1._2, e2._2)
```

## Question 1.2

```scala
def triangles(edges: DirectedGraph): List[(NodeId, NodeId, NodeId)] =
  edges.filter { e1 =>
    e1._1 < e1._2
  }.flatMap { e1 =>
    edges.filter { e2 =>
      e1._2 == e2._1 && edges.contains((e2._2, e1._1))
    }.filter { e2 =>
      e1._1 < e2._2 && e2._1 != e2._2
    }.map { e2 =>
      (e1._1, e1._2, e2._2)
    }
  }
```

## Question 2.

*Identity.*

```scala
   m.map(x => x)
== m.flatMap(x => unit((x => x)(x))) // Monad/Functor Consistency
== m.flatMap(x => unit(x))           // Simplification
== m.flatMap(unit)                   // Simplification
== m                                 // Right unit
```

*Associativity.*

```scala
   m.map(h).map(g)
== m.flatMap(x => unit(h(x))).flatMap(x => unit(g(x))) // M/F Consistency
== m.flatMap(x => unit(h(x)).flatMap(x => unit(g(x)))) // Associativity
== m.flatMap(x => unit(g(h(x))))                       // Left unit
== m.map(x => g(h(x)))                                 // M/F Consistency
```
