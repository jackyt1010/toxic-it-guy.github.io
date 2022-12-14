---
layout:     post
title:      "Theoretical Physics [Landau Mechanics Notes] Chapter 2: Conservation Laws(Part 1)"
subtitle:   ""
description: ""
date:     2022-09-08
published: true
author:  Jacky Tang
categories: [ "Physics"]
tags:
    - Theortical Physics
    - Classical Mechanics
URL: "/2022/09/08/landau-mechanics-ch2/"
katex: true
---

<!--more-->
![Coverpage2](/img/landau-mechanics-ch1/landau.jpg)
In mechanical systems, the origin and physical significance of conservation laws are very profound, and are closely related to the symmetry exhibited by the system.

The general logic is (detailed derivation needs to wait): when a mechanical system exhibits a certain symmetry, the system should be transformed from this symmetry. Before and after the transformation, a certain function describing the mechanical properties is unchanged. This invariance leads to the conservation of a certain "physical quantity". Whether it is the conservation of energy, momentum, angular momentum, etc., its essence comes from the inherent symmetry of the system.

These symmetries and conservation laws will be derived in turn.
 ## 6. Energy 
  
During the motion of a mechanical system, the 2s quantities 
$$q_{i}$$ and $$\dot{q_{i}}$$ which specify the state of the system vary with time. 
There exist, however, functions of these quantities whose values remain constant during the motion, and depend only on the initial conditions.
Such functions are called integrals of the motion.

First, let's consider  the conservation laws that arise from the homogeneity of time. Due to this homogeneity, the closed-system Lagrangian  does not explicitly depend  on time. Therefore, the Lagrangian total time derivative  can  be written as:
$$\frac{dL}{dt} = \sum_i\frac{\partial L}{\partial q_{i}}\dot{q_{i}}+\sum_i\frac{\partial L}{\partial \dot{q_{i}}}\ddot{q_i}$$

As $$\frac{dL}{dt} = \sum_i\dot{q_{i}}\frac{d}{dt}(\frac{\partial L}{\partial \dot{q_{i}}})+\sum_i\frac{\partial L}{\partial \dot{q_{i}}}\ddot{q_i}=\sum_i \frac{d}{dt}(\dot{q_i}\frac{\partial L}{\partial \dot{q_{i}}})$$
or
$$\frac{d}{dt}(\sum_i\dot{q_i}\frac{\partial L}{\partial \dot{q_{i}}}-L)=0$$
Hence we see that the quantity
$$E=\sum_i\dot{q_i}\frac{\partial L}{\partial \dot{q_{i}}}-L   \text{       (6.1)} $$   
remains constant during the motion of a closed system, i.e. it is an integral
of the motion and E is called the energy of the system.

As we see in [Chapter 1](https://jackyt.netlify.app/2022/08/23/landau-mechanics-ch1/), the Lagrangian of a closed system is of the form $$L = T(q, \dot{q})— U(q)$$ where T is a quadratic
function of the velocities.By [Euler’s theorem on homogeneous functions](https://en.wikipedia.org/wiki/Homogeneous_function), we have $$\sum_i\dot{q_i}\frac{\partial L}{\partial \dot{q_{i}}}=\sum_i\dot{q_i}\frac{\partial T}{\partial \dot{q_{i}}}=2T$$

Substituting this in (6.1) gives $$E = T(q, \dot{q})+ U(q)$$
  ## 7. Momentum 
A second conservation law follows from the homogeneity of space. By virtue of this homogeneity, the mechanical properties of a closed system are unchanged by any parallel displacement of the entire system in space.
The mechanical system should have spatial translation symmetry, that is, the coordinates of all particles in the system are translated

When $$r - > r +  \varepsilon $$ the Lagrangian function is invariant

Before and after the translation, the amount of change in the Lagrangian function is $$\delta L = \sum_a \frac{\partial L}{\partial \textbf{r}_a}.\delta\textbf{r}_a = \varepsilon.\sum_a \frac{\partial L}{\partial \textbf{r}_a}$$
Since $$\varepsilon$$ is arbitrary, the condition $$\delta L = 0$$ is equivalent to $$\sum_a \frac{\partial L}{\partial \textbf{r}_a} = 0  \text{       (7.1)}$$
From Lagrange's equations, we have $$\sum_a \frac{d}{dt}(\frac{\partial L}{\partial \textbf{v}_a}) = \frac{d}{dt}(\sum_a \frac{\partial L}{\partial \textbf{v}_a}) = 0$$
![Paragraph](/img/landau-mechanics-ch2/3.png)
![Paragraph](/img/landau-mechanics-ch2/4.png)
