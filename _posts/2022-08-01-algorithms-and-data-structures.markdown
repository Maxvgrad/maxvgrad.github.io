---
title:  "Algorithms and data structures"
date:   2022-08-01 21:18:58 +0200
categories: course
---
Algorithms and data structures

# Table of contents
1. [Introduction](#Introduction)
   1. [Correctness](#Correctness)
   1. [Why learn algorithms?](#Why learn algorithms?)
1. [Asymptotic notation](#Asymptotic notation)
1. [Sorting and searching](#Sorting and searching)
1. [Resources](#Resources)

# Introduction

Algorithm has to solve a general, specified problem. We seek algorithms which _correct_ and _efficient_.
Correct - algorithm gives always a correct answer for all input.
Efficient - is measured by asymptotic notation. User can see results with a blink of an eye.
A faster algorithm running on slower machine would always win for sufficiently large instances.

## Correctness

For any algorithm we must prove that it always returns a desired output for all legal instances of the problem.
Algorithm problem should be carefully defines to allow provably correct algorithm to exist.
Algorithm correctness is not obvious in many optimization problems.
Algorithm without a proof of correctness is probably wrong. Searching for counterexample is the best way to disprove 
correctness of algorithm.

# Asymptotic notation

Random access machine (RAM) - theoretical model of a computer allows to analyse algorithm in machine independent way.

RAM assumptions:
* Each simple operation takes 1 step;  
* Loops and subroutines are not simple operations;
* Each memory access takes 1 step.

We measure the run time of the algorithm by counting number of steps. 
RAM is as useful as flat-earth model, because in sneaker shop we don't look for curved sole.

## Complexity analysis

Two ideas from the lecture:

1. Ways of counting the complexity of an algorithm (best, worst and average case);
2. Learning a language to talk about functions big O notation (asymptotic notations). 

![](../assets/images/algorithms/skiena/alg_skiena-lecture-2-worst-case.webp)
Each of those complexities defines a numerical function: time vs size.
What would the reasoning be on buying a lottery on the bases of worth, best and average-case complexities?

Reason on value of buying a lottery ticket.
You learn nothing from looking at best-case.

Exact analyses is hard. Best, average and worst are difficult to deal with 
because precise function details are complicated. It is easier to talk about lower and upper bounds, 
which brings us into asymptotic notations.

When we ara talking about big Oh we are talking about properties of the function not meaning (???).
![](../assets/images/algorithms/skiena/alg_skiena-lecture-2-upper-lower-bounds.webp)
![](../assets/images/algorithms/skiena/alg_skiena-lecture-2-upper-lower-bound-graph.webp)
![](../assets/images/algorithms/skiena/alg_skiena-lecture-2-upper-lower-bounds-formal-definition.webp)


# Resources

1. The Algorithm Design Manual by Steven S. Skiena
1. [Analysis of Algorithms Lectures by S. Skiena](https://www3.cs.stonybrook.edu/~skiena/373/videos/)
1. [Алгоритмы и структуры дыннх семестр 1 2020 лектор Павел Маврин](https://www.youtube.com/playlist?list=PLrS21S1jm43jz48qjdfYNpuIPgL3lNJ_o)
