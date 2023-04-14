---
title:  "Graph search and connectivity"
date:   2022-02-08 00:00:00 +0000
categories: algorithms
---

Саммари

# Table of contents
1. [Motivation](#Motivation)
1. [Motivation](#Motivation)


# Generic graph search method

## Motivation

1. Network is connectivity
2. Driving direction
3. Formulate a plan 

## Generic graph search

Goals:
1. Find everything findable from a given source vertex
2. Don't visit vertex twice

Different strategies of picking a next unexplored node can lead to different algorithm properties.

![](../assets/images/algorithms/tim-roughgarden/stanford/course2/w1/graph-search.webp)

## BFS vs DFS

Breadth-first-search
- can compute shortest path
- can compute a connected components of undirected graph

Depth-first-search
- compute topological ordering of directed acyclic graph
- compute connected components in directed graph

## BFS

## Undirected connectivity

### Connected components via BFS

```python
all nodes unexploterd
for i = 1 to n:
    if i not yet explored:
        BFS(G, i)

```

## DFS

BFS turns in DFS by changing queue to stack. Another way of implementing DFS by using recursion.

## Topological sort

Definition: 
A topological ordering of directed G is labelling f of G's nale such that:
1. the f(v) are the set {1,2,..,n}
2. (u,v) ∈ G => f(u) < f(v)

_Motivation:_ sequence tasks while respecting all precedence constraints.

_Note:_ G has directed cycle => no topological ordering.

_Theorem:_ no directed cycle => can compute topological ordering in O(m + n) time.

### Straightforward solution



# Computing Strong Components

Strongly connected components (SCCs) of a graph G are the equivalence classes of the relation
u~v <=> ∃ path u -> v and a path v -> u in G 

![](../assets/images/algorithms/tim-roughgarden/stanford/course2/w1/strongly-connected-components.webp) 

# Links
* [Использование обхода в глубину для поиска компонент сильной связности](https://neerc.ifmo.ru/wiki/index.php?title=%D0%98%D1%81%D0%BF%D0%BE%D0%BB%D1%8C%D0%B7%D0%BE%D0%B2%D0%B0%D0%BD%D0%B8%D0%B5_%D0%BE%D0%B1%D1%85%D0%BE%D0%B4%D0%B0_%D0%B2_%D0%B3%D0%BB%D1%83%D0%B1%D0%B8%D0%BD%D1%83_%D0%B4%D0%BB%D1%8F_%D0%BF%D0%BE%D0%B8%D1%81%D0%BA%D0%B0_%D0%BA%D0%BE%D0%BC%D0%BF%D0%BE%D0%BD%D0%B5%D0%BD%D1%82_%D1%81%D0%B8%D0%BB%D1%8C%D0%BD%D0%BE%D0%B9_%D1%81%D0%B2%D1%8F%D0%B7%D0%BD%D0%BE%D1%81%D1%82%D0%B8)
* [Амортизационный анализ](https://neerc.ifmo.ru/wiki/index.php?title=%D0%90%D0%BC%D0%BE%D1%80%D1%82%D0%B8%D0%B7%D0%B0%D1%86%D0%B8%D0%BE%D0%BD%D0%BD%D1%8B%D0%B9_%D0%B0%D0%BD%D0%B0%D0%BB%D0%B8%D0%B7)

