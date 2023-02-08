---
title:  "Графы. Обход в глубину. Топологическая сортировка"
date:   2022-02-08 00:00:00 +0000
categories: algorithms
---

Саммари

# Table of contents
1. [Motivation](#Motivation)


# Графы

_Оринентированные_ графы направленные ребра и используются для задания двунаправленных связей.

![](../assets/images/algorithms/mavrin/s3/l1/graph.webp)

Ряд упрощений в оценки сложности алгоритмов на графах

![](../assets/images/algorithms/mavrin/s3/l1/analysis-simplification.webp)

## Способы хранения графа

* Матрица связности

![](../assets/images/algorithms/mavrin/s3/l1/adjacency-matrix.webp)

* Лист связности

![](../assets/images/algorithms/mavrin/s3/l1/adjacency-list.webp)



## Обход в глубину (DFS)

Алгоритм находит компоненты связности в алгоритме.

![](../assets/images/algorithms/mavrin/s3/l1/graph-connectivity-components-dfs.webp)

```python
dfs(x): # пометитть все вершины достижимые из Х
    mark(x) = True
    for (xy) in E[x]:
        if not mark[y]:
            dfs(y)
```

![](../assets/images/algorithms/mavrin/s3/l1/dfs-proof.webp)

## Обход в глубину для ориентированного графа

![](../assets/images/algorithms/mavrin/s3/l1/dfs-directed-graph.webp)

# Links
* [АиСД S03E01. Графы. Обход в глубину. Топологическая сортировка](https://www.youtube.com/watch?v=RPIE0lXAIv4&list=PLrS21S1jm43ie9vkDOu3zZqlTtPd1pd0t)
* [Использование обхода в глубину для поиска компонент сильной связности](https://neerc.ifmo.ru/wiki/index.php?title=%D0%98%D1%81%D0%BF%D0%BE%D0%BB%D1%8C%D0%B7%D0%BE%D0%B2%D0%B0%D0%BD%D0%B8%D0%B5_%D0%BE%D0%B1%D1%85%D0%BE%D0%B4%D0%B0_%D0%B2_%D0%B3%D0%BB%D1%83%D0%B1%D0%B8%D0%BD%D1%83_%D0%B4%D0%BB%D1%8F_%D0%BF%D0%BE%D0%B8%D1%81%D0%BA%D0%B0_%D0%BA%D0%BE%D0%BC%D0%BF%D0%BE%D0%BD%D0%B5%D0%BD%D1%82_%D1%81%D0%B8%D0%BB%D1%8C%D0%BD%D0%BE%D0%B9_%D1%81%D0%B2%D1%8F%D0%B7%D0%BD%D0%BE%D1%81%D1%82%D0%B8)

