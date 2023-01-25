---
layout:     post
title:      "Theoretical Physics [Introduction to Quantumn Mechanics] Chapter 1: The Wave Function (Part 2)"
subtitle:   ""
description: ""
date:     2023-01-07
published: true
author:  Jacky Tang
categories: [ "Physics", "Mathematics"]
tags:
    - Theortical Physics
    - Quantumn Mechanics
URL: "/2023/01/07/intro-quantumn-mechanics-ch1-part2/"
katex: true
---

<!--more-->
![Coverpage](/img/intro-quantumn-mechanics/cover.png)
  ##  1.4 Normalization
![1.4](/img/intro-quantumn-mechanics/1-4.png)
Problem 1.4

(a)
Let $$\int_{a}^{b}{| Ψ (x, t)|^{2}} dx = 1$$
$$\int_{0}^{a}{| A |^{2}} \frac{x^{2}}{a^{2}} dx + \int_{a}^{b}{| A |^{2}} \frac{(b-x)^{2}}{(b-a)^{2}} dx = 1$$
$$=\frac{A^{2}}{a^{2}} \frac{a^{3}}{3} + \frac{A^{2}}{(b-a)^{2}} \int_{a}^{b}(b-x)^2dx $$
$$=\frac{A^{2}}{a^{2}} \frac{a^{3}}{3} + \frac{A^{2}}{(b-a)^{2}}[-\frac{(b-x)^{3}}{3}] \rvert_{a}^{b}$$
$$=\frac{A^{2}a}{3} + \frac{A^{2}(b-a)}{3}$$
=> $$A = \sqrt{\frac{3}{b}}$$

(b)
![1.4b](/img/intro-quantumn-mechanics/1-4b.png)

(c)
At x=a

(d)
$$P = \int_{0}^{a} A^{2} \frac{x^{2}}{a^{2}} dx=\frac{A^{2}}{a^{2}}(\frac{x^{3}}{3})\rvert_{0}^{a}=\frac{A^{2}a}{3}=(\sqrt(\frac{3}{b}))^{2}\frac{a}{3} = \frac{a}{b}$$

When $$b=a, P=1$$
When $$b=2a, P=\frac{1}{2}$$

(e)
$$\<x\> = \int_{a}^{b}{x| Ψ (x, t)|^{2}} dx=\int_{0}^{a}{x \frac{A^2x^2}{a^2}} dx + \int_{a}^{b}{x\frac{A^2(b-x)^2}{(b-a)^2}} dx$$
$$=\frac{A^{2}}{a^{2}}\frac{x^{4}}{4}\rvert_{0}^{a} + \frac{A^{2}}{(b-a)^{2}}\int_{a}^{b}x(b-x)^{2}dx = \frac{3a^2}{4b} + \frac{3}{b(b-a)^2} \int_{a}^{b} (xb^{2} - 2bx^{2} + x^{3})dx$$
$$= \frac{3a^2}{4b} + \frac{3}{b(b-a)^2} (\frac{b^{2}x^{2}}{2}-\frac{2bx^{3}}{3} + \frac{x^{4}}{4})\rvert_{a}^{b} =\frac{b+2a}{4}$$
Q.E.D

  
  

