---
title:  "Sets"
date:   2022-03-17 00:00:00 +0000
categories: mathematics discrete-mathematics
---

Discrete Mathematics

# Table of contents
1. [Set](#Set)
1. [Subsets](#Subsets)

# Discrete mathematics

A recent hot topic is mathematical cryptography, which is based on number theory (the study of positive
integers 1,2,3,...), and is widely applied, among others, in computer security and electronic
banking. Other important areas in applied mathematics include linear programming, coding
theory, theory of computing. The mathematics in these applications is collectively called
discrete mathematics. (“Discrete” here is used as the opposite of “continuous”; it is also
often used in the more restrictive sense of “finite”.)

At the same time, it is important to realize that mathematics cannot be done without
proofs. Merely stating the facts, without saying something about why these facts are valid,
would be terribly far from the spirit of mathematics and would make it impossible to give
any idea about how it works.

# Set

The usual tool in mathematics to do so is the notion of a set. Any collection of things, called elements, is a set.

If A is a set and b is an element of A, we write b ∈ A. The number of elements of a set A (also called the cardinality of A) is denoted by |A|.

A set A is called a subset of a set B, if every element of A is also an element of B.
The relation that A is a subset of B is denoted by A ⊆ B.

The intersection of two sets is the set consisting of those elements that elements of both sets. The intersection of two sets A and B is denoted by A ∩ B.
Two sets whose intersection is the empty set (in other words, have no element in common) are called disjoint.

# Subsets

**Theorem:** A set with n elements has 2^n subsets

A correspondence with these properties is called a one-to-one correspondence (or bijection). 
If we can make a one-to-one correspondence between the elements of two sets, then they have the same number of elements.

# Sequences

**Theorem:** The number of strings of length n composed of k given elements is k^n

**Theorem:** Suppose that we want to form strings of length n so that we can use any of
a given set of k<sub>1</sub> symbols as the first element of the string, any of a given set of k2 symbols
as the second element of the string, etc., any of a given set of kn symbols as the last element
of the string. Then the total number of strings we can form is k<sub>1</sub> · k<sub>2</sub> · ... · k<sub>n</sub>.

# Permutations

If we have an ordered list of n objects, and we rearrange them so that they are in another order, 
this is called permuting them, and the new order is also called a permutation of the objects.

**Theorem:** The number of permutations of n objects in n!

# Links
* [Discrete Mathematics Lecture Notes, Yale University, Spring 1999 L. Lov´asz and K. Vesztergombi](https://cims.nyu.edu/~regev/teaching/discrete_math_fall_2005/dmbook.pdf)

