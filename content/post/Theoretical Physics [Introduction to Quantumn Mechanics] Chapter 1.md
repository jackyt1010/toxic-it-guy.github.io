---
layout:     post
title:      "Theoretical Physics [Introduction to Quantumn Mechanics] Chapter 1: The Wave Function"
subtitle:   ""
description: ""
date:     2022-10-09
published: true
author:  Jacky Tang
categories: [ "Physics", "Mathematics"]
tags:
    - Theortical Physics
    - Quantumn Mechanics
URL: "/2022/10/09/intro-quantumn-mechanics-ch1/"
katex: true
---

<!--more-->
![Coverpage](/img/intro-quantumn-mechanics/cover.png)
  ##  1.1 The Schrödinger Equation
Imagine a particle of mass m, constrained to move along the x-axis, subject to some specified force F (x, t). The program of classical mechanics is to determine the position of the particle at any given time: x(t).
Once we know that, we can figure out the velocity (v = dx/dt), the momentum (p = mv), the kinetic energy $$(T = (l/2)mv^{2}),$$ or any other dynamical variable of interest. And how do we go about determining x(t)?
We apply Newton's second law: F = ma. This, together with appropriate initial conditions determines x(t).<br/>  
Quantum mechanics approaches this same problem quite differently. In this case what we're looking for is the particle's wave function, Ψ(x, t), and we get it by solving the Schrodinger equation: 
$$i\hbar \frac{\partial Ψ }{\partial t} = -\frac{\hbar^{2}}{2m}\frac{\partial^{2} Ψ }{\partial x^{2}}+VΨ$$
Here i is the square root of -1, and Ii is Planck's constant.
The Schrodinger equation plays a role logically analogous to Newton's second law.

  ## 1.2 The statstical interpretation
But what exactly is this "wave function,", a particle, by its nature, is localized at a point, whereas the wave function is spread out in space.How can such an object represent the state of a particle?The answer
is provided by Born' s statistical interpretation of the wave function, which says that $$|Ψ(x, t)|^{2}$$ gives the probability of finding the particle at point x, at time t-or,
more precisely, 
$$\int_{a}^{b}{|Ψ(x, t)|^{2}} dx$$ = {the probability pf finding the particle bewteen a and b. at time t}<br/>  
Probability is the area under the graph of $$|Ψ(x, t)|^{2}$$.

The statistical interpretation introduces a kind of indeterminacy into quantum mechanics, for even if you know everything the theory has to tell you about
the particle, still you cannot predict with certainty the outcome of a simple experiment to measure its position-an quantum mechanics has to offer is statistical infom1ation about the possible results. This indetenninacy
has been profoundly disturbing to physicists and philosophers alike, and it is natural to wonder whether it is a fact of nature.
  
