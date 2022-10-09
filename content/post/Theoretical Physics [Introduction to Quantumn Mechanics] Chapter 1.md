---
layout:     post
title:      "Self-Education Theoretical Physics [Introduction to Quantumn Mechanics] Chapter 1: The Wave Function"
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
$$\int_{a}^{b}{|Ψ(x, t)|^{2}} dx$$ = {the probability of finding the particle bewteen a and b at time t}<br/>  
Probability is the area under the graph of $$|Ψ(x, t)|^{2}.$$
The statistical interpretation introduces a kind of indeterminacy into quantum mechanics, for even if you know everything the theory has to tell you about
the particle, still you cannot predict with certainty the outcome of a simple experiment to measure its position-an quantum mechanics has to offer is statistical infom1ation about the possible results. This indetenninacy
has been profoundly disturbing to physicists and philosophers alike, and it is natural to wonder whether it is a fact of nature.

  ## 1.3 Probability
For contiuous variable x, if we let the probability density function be p(x), then the probability that an individual(chosen at random) lies between x and x+dx is equal to p(x)dx.
The probability that x lies between a and b (a .finite interval) is given by the integral of p(x): $$P_{ab}=\int_{a}^{b}{p(x)} dx$$ and we have the following equations for statistics:
$$1=\int_{-\infty}^{+\infty}{p(x)} dx$$
$$\text{The expectation value} \<x\>=\int_{-\infty}^{+\infty}{xp(x)} dx$$
$$\text{The expectation value} \<f(x)\>=\int_{-\infty}^{+\infty}{f(x)p(x)} dx$$
$$\text{The variance }  \sigma^{2} = <x^{2}> - \<x\>^{2} $$

Example 1.1 Suppose I drop a rock off a cliff of height h. As it falls, I snap a million photographs, at random intervals. On each picture I measure the average distance the rock has fallen. Question: What is the average of all these distances?
That is to say, what is the time average of the distance traveled?

Solution: Solution: The rock starts out at rest, and picks up speed as it falls; it spends more time near the top, so the average distance must be less than h /2. Ignoring air resistance, the distance x at time t is 
$$x(t) = \frac{1}{2}gt^{2}$$

The velocity is dx / dt = gt, and the total flight time is $$T = \sqrt{2h / g}$$ The probability that the camera flashes in the interval dt is dt / T, so the probability that a given photograph shows a distance in the corresponding 
range dx is $$\frac{dt}{T} = \frac{dx}{gt}\sqrt{\frac{2h}{g}}=\frac{1}{2\sqrt{hx}}dx$$
Evidently the probability density is
$$p(x) = \frac{1}{2\sqrt{hx}}$$
Thus, the average distance is $$ \<x\> = \int_{0}^{h} {x \frac{1}{2\sqrt{hx}}} dx =\frac{1}{2\sqrt{h}}(\frac{2}{3} x^{3/2})\rvert_{0}^{h} = h/3$$ <br/>  
which is somewhat less than h /2, as anticipated.