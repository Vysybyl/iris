+++
title = 'Topological limits of finite space transformations and their implications on general-purpose models'
date = 2024-10-26
image = '/iris/images/2023-05-20_amsterdam_nxt_museum.jpg'
categories = ['mathematics']
tags = ['machine-learning']
languages = ['en']
draft = true
+++

# Abstract

# Introduction

# Models as transformations

## Transformations
I am using the term *transformation* (t) as synonym of *map*, *mapping* or *function*, and 
the terms *input set* (A), *target set* (B) and *transformed set* (Y)  as synonyms of *domain*, *codomain* and *image*, respectively.

## Cost functions
A cost function can be defined as a map from AxB to an abelian totally ordered group (typically R).
(It should be clear that this definition of cost function encompasses also the idea of 
training data).

## Models
An (abstract) model is any transformation. 

## Pointwise model ordering
Given:
- two transformations t' and t'' applicable on the same input set A, with values on the same
target set B
- a cost function C from AxB
They entails a pointwise model ordering such that t'P(a)t'' iff t'(a) <= t''(a)

## Random models
A random model is NOT a model. It is a random variable.
Nevertheless, the expected value of a random model is a model (it is a transformation).

# Computable models
A computable model is a computable transformation.

## Total model ordering
Given:
- two computable models t' and t'' applicable on the same finite input set A, with values on the same
finite target set B
- a cost function C from AxB
They entails a total model ordering such that t'P(A)t'' iff SUM_on_B t'(a) <= SUM_on_B t''(a).

Two models are equal iff t'P(A)t'' and t'P(A)t''.

This implies that if two models are NOT equal, there must exist a such that t'(a) != t''(a)

# Model stability
If A is a group, alpha an element of A, a model is alpha-stable if
t(a) == t(a+alpha) for all a in A.

If A is a normed space with norm || . ||, t is epsilon-stable if it is alpha-stable for all alpha's s.t. ||alpha|| < epsilon.

# Model versatility
If A is a normed space, B is a group and beta is an element of B, a model t has beta-versatility v if 
for each a there exists an alpha such that t(a + alpha) = t(a) + beta and ||alpha|| < v.

If B is a normed space, t has mu-versatility v if it has beta-versatility v for all beta s.t. ||beta|| < mu.


