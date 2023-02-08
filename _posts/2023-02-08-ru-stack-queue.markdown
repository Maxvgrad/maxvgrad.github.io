---
title:  "АиСД S01E06. Стеки, очереди. Амортизированное время"
date:   2022-02-08 00:00:00 +0000
categories: algorithms
---

Саммари

# Table of contents
1. [Стек](#Стек)
1. [Очередь](#Очередь)
1. [Расширяющийся стек](#Расширяющийся стек)
1. [Амортизационный анализ](#Амортизационный анализ)


# Стек

```
def push(x):
   return a[n++] = x

def pop(x):
   return a[--n]
```

# Очередь

Эдементы заходят в tail, а выходять из head.

![](../assets/images/algorithms/mavrin/s1/l6/queue.webp)
 
```
def add(x):
   return a[tail%n++] = x

def remove(x):
   return a[head%n++]
```

Проблема очереди в том, что она растет, но данную проблему можно решить, если задано максимальное значение 
элементов n.

# Расширяющийся стек

![](../assets/images/algorithms/mavrin/s1/l6/extend-stack.webp)

При заполнении массива, выполняем копирование элементов в массив размера 2n.
```
def push(x):
   if n == len(a):
     a' = new int[2*n]
     copy(a[0, n-1], a'[0,n-1])
     a = a'

   return a[n++] = x
```

![](../assets/images/algorithms/mavrin/s1/l6/shrink-stack.webp)

Сужаем массив при числе элементов в 4 раза меньше чем размер массива.
```
def pop(x):
   if n <= len(a)/4:
     a' = new int[n]
     copy(a[0, n-1], a'[0,n-1])
     a = a'

   return a[--n] = x
```

# Амортизационный анализ

Амортизрованное время операции - времен берется из головы, но амортизированное время является хорошим,
если выполняется такое условие.

![](../assets/images/algorithms/mavrin/s1/l6/amortized-time-definition.webp)

Техники доказательства правильности ВА
1. Оценка в лоб (тупая)
2. Метод потенциалов
3. Бугалтерский метод

## Оценка в лоб (тупая)

Взять код и посчитать количество операция, на основании которого  и определение и доказазать.

![](../assets/images/algorithms/mavrin/s1/l6/amortized-analysis-method-1.webp)

## Метод потонциалов

Берем структуру данных и присваиваем ей потенциал.

![](../assets/images/algorithms/mavrin/s1/l6/amortized-analysis-aggregate-method.webp)

## Метод бухгалтерского учета (метод с монетками)

![](../assets/images/algorithms/mavrin/s1/l6/amortized-analysis-banker-method.webp)

# Амортизационный анализ стека методом бухгалтерского учета

![](../assets/images/algorithms/mavrin/s1/l6/amortized-analysis-banker-method-stack.webp)


# Ссылки
* [Амортизационный анализ](https://neerc.ifmo.ru/wiki/index.php?title=%D0%90%D0%BC%D0%BE%D1%80%D1%82%D0%B8%D0%B7%D0%B0%D1%86%D0%B8%D0%BE%D0%BD%D0%BD%D1%8B%D0%B9_%D0%B0%D0%BD%D0%B0%D0%BB%D0%B8%D0%B7)
* [Амортизационный анализ](https://neerc.ifmo.ru/wiki/index.php?title=%D0%90%D0%BC%D0%BE%D1%80%D1%82%D0%B8%D0%B7%D0%B0%D1%86%D0%B8%D0%BE%D0%BD%D0%BD%D1%8B%D0%B9_%D0%B0%D0%BD%D0%B0%D0%BB%D0%B8%D0%B7)

