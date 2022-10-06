---
layout:     post
title:      "Self-Education Theoretical Physics [Introduction to Quantumn Mechanics] Chapter 1: The Wave Function"
subtitle:   ""
description: ""
date:     2022-10-07
published: true
author:  Jacky Tang
categories: [ "Physics", "Mathematics"]
tags:
    - Theortical Physics
    - Quantumn Mechanics
URL: "/2022/10/07/intro-quantumn-mechanics-ch1/"
katex: true
---

<!--more-->
![Coverpage](/img/intro-quantumn-mechanics/cover.png)
##  1.1 The Schrödinger Equation
Imagine a particle of mass m, constrained to move along the x-axis, subject to some specified force F (x. t). The program of classical mechanics is to determine the position of the particle at any given time: x(t).
Once we know that, we can figure out the velocity (v = dx/dt), the momentum (p = mv), the kinetic energy $$(T = (l/2)mv^{2})$$, or any other dynamical variable of interest. And how do we go about determining x(t)?
We apply Newton's second law: F = ma. This, together with appropriate initial conditions determines x(t).<br/>  
Quantum mechanics approaches this same problem quite differently. In this case what we're looking for is the particle's wave function, Ψ(x. t), and we get it by solving the Schrodinger equation: 
$$i\hbar \frac{\partial Ψ }{\partial t} = -\frac{h^{2}}{2m}\frac{\partial^{2} Ψ }{\partial x^{2}}+VΨ$$
Here i is the square root of -1, and Ii is Planck's constant.
The Schrodinger equation plays a role logically analogous to Newton's second law.