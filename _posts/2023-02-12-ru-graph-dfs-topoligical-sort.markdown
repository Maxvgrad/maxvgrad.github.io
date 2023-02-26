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
dfs(x): # пометить все вершины достижимые из Х
    mark(x) = True
    for (xy) in E[x]:
        if not mark[y]:
            dfs(y)
```

![](../assets/images/algorithms/mavrin/s3/l1/dfs-proof.webp)

## Обход в глубину для ориентированного графа

![](../assets/images/algorithms/mavrin/s3/l1/dfs-directed-graph.webp)
![](../assets/images/algorithms/mavrin/s3/l1/edge-types.webp)

![](../assets/images/algorithms/mavrin/s3/l1/classify-edge.webp)

Поиск цыкла в графе. Обратное ребро пораждает цыкл.
Время входа и выхода работает для определения цикла, но это сложно.
Чтобы определить предка, можно хранить метку-предка.

![](../assets/images/algorithms/mavrin/s3/l1/search-graph-cycle.webp)

```python
dfs(x): 
    mark[x] = 1
    for (x,y) in E[x]:
        if mark[y] == 0:
            dfs(y)
        if mark[y] == 1:
            FindCicle(x,y) # выводим цыкл от y до x
    mark[x] = 2    
```

# Топологическая сортировка

Не ориентированный граф без циклов - это дерово.
Ориентированный граф без циклов обладает более сложной структурой и называется _ацикличный граф_.

Топологическая сортировка важна для загрузки графа зависимостей, 
перед загрузкой зависимости нужно убедиться, что все зависимые зависимости  уже подгружены.

## Топологическая сортировка без DFS

![](../assets/images/algorithms/mavrin/s3/l1/topological-sort.webp)

```python
q = queue()

# n - число вершин
for x = 1..n: 
    if in[x] == 0:
        q.add(x)

for i = 1..n :
    # in(x) - сколько ребер входит в x
    # x = вершина в которую не входят ребра
    # самое неприятное это время работы данной функции в очереди in[x]
    # x : in[x] = 0 # найдем такой x что in on x равен 0
    x = q.remove()
    p[i] = x # массив вершин топологической сортировки
    
    # пересчитаем входы ребер после удалення x
    # дынный цыкл работает за O(m), где m это число ребер
    for (x,y) in E[x]:
        in[y]--
        if in[y] == 0:
            q.add(y)
```

Суммарное время работы O(m + n) или O(m) если вы лентяй.

## Топологическая сортировка с помощью DFS

![](../assets/images/algorithms/mavrin/s3/l1/topological-sort-with-dfs.webp)

Если отсортировать вершины по времени выхода, то получится топологическая сортировка.
Это можно доказать, что каждое ребро ведет из вершины с большим временем выхода в вершину с меньшим временем.

```python
topsort(x)
    mark[x] = 1
    for (x,y) in E[x]:
        if mark[y] == 0:
            topsort(y)
    
    p[i] = x
    i --
```

# Links
* [АиСД S03E01. Графы. Обход в глубину. Топологическая сортировка](https://www.youtube.com/watch?v=RPIE0lXAIv4&list=PLrS21S1jm43ie9vkDOu3zZqlTtPd1pd0t)
* [Использование обхода в глубину для поиска компонент сильной связности](https://neerc.ifmo.ru/wiki/index.php?title=%D0%98%D1%81%D0%BF%D0%BE%D0%BB%D1%8C%D0%B7%D0%BE%D0%B2%D0%B0%D0%BD%D0%B8%D0%B5_%D0%BE%D0%B1%D1%85%D0%BE%D0%B4%D0%B0_%D0%B2_%D0%B3%D0%BB%D1%83%D0%B1%D0%B8%D0%BD%D1%83_%D0%B4%D0%BB%D1%8F_%D0%BF%D0%BE%D0%B8%D1%81%D0%BA%D0%B0_%D0%BA%D0%BE%D0%BC%D0%BF%D0%BE%D0%BD%D0%B5%D0%BD%D1%82_%D1%81%D0%B8%D0%BB%D1%8C%D0%BD%D0%BE%D0%B9_%D1%81%D0%B2%D1%8F%D0%B7%D0%BD%D0%BE%D1%81%D1%82%D0%B8)

