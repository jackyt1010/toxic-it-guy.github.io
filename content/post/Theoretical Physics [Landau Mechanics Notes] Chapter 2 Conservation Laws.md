---
layout:     post
title:      "Self-Education Theoretical Physics [Landau Mechanics Notes] Chapter 2: Conservation Laws"
subtitle:   ""
description: ""
date:     2022-09-07
published: true
author:  Jacky Tang
categories: [ "Physics"]
tags:
    - Theortical Physics
    - Classical Mechanics
URL: "/2022/08/28/landau-mechanics-ch2/"
katex: true
---

<!--more-->
![Coverpage2](/img/landau-mechanics-ch1/landau.jpg)
In mechanical systems, the origin and physical significance of conservation laws are very profound, and are closely related to the symmetry exhibited by the system.

The general logic is (detailed derivation needs to wait until quantum field theory and Noether's theorem): when a mechanical system exhibits a certain symmetry, the system should be transformed from this symmetry. Before and after the transformation, a certain function describing the mechanical properties is unchanged. This invariance leads to the conservation of a certain "physical quantity". Whether it is the conservation of energy, momentum, angular momentum, etc., its essence comes from the inherent symmetry of the system.

These symmetries and conservation laws will be derived in turn.
 ## 6. Energy 
  
During the motion of a mechanical system, the 2s quantities 
$$q_i$$ and $$\dot{q}_i$$ which specify the state of the system vary with time. 
There exist, however, functions of these quantities whose values remain constant during the motion, and depend only on the initial conditions.
Such functions are called integrals of the motion.

First, let's consider  the conservation laws that arise from the homogeneity of time. Due to this homogeneity, the closed-system Lagrangian  does not explicitly depend  on time. Therefore, the Lagrangian total time derivative  can  be written as:
$$\dv{L}{t}=\sum_i \pdv{L}{q_i}\dot{q_i} + \sum_i \pdv{L}{\dot{q_i}}\ddot{q_i}$$

As $$\dv{L}{t}= \sum_i \dot{q_i}\dv{}{t}(\pdv{L}{\dot{q_i}}) + \sum_i \pdv{L}{\dot{q_i}}\ddot{q_i}\\= \sum_i \dv{}{t}(\dot{q_i}\pdv{L}{\dot{q_i}})$$
or
$$\dv{}{t} (\sum_i (\dot{q_i}\pdv{L}{\dot{q_i}})-L)=0$$
Hence we see that the quantity
$$E=\sum_i (\dot{q_i}\pdv{L}{\dot{q_i}})-L$$
remains constant during the motion of a closed system, i.e. it is an integral
of the motion and E is called the energy of the system.
  ## 7. Momentum 
  
  
  ## 8. Centre of mass 
  
  
  ## 9. Angular momentum 
  
  
  ## 10. Mechanical similarity
 