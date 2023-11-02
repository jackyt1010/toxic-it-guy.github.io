---
layout:post
title:"TheoreticalPhysics[IntroductiontoQuantumnMechanics]Chapter1:TheWaveFunction(Part2)"
subtitle:""
description:""
date:2023-01-07
published:true
author: JackyTang
categories:["Physics","Mathematics"]
tags:
-TheorticalPhysics
-QuantumnMechanics
URL:"/2023/01/07/intro-quantumn-mechanics-ch1-part2/"
katex:true
---

<!--more-->
![Coverpage](/img/intro-quantumn-mechanics/cover.png)
##1.4Normalization
![1.4](/img/intro-quantumn-mechanics/1-4.png)
Problem1.4

(a)
Let$$\int_{a}^{b}{|Ψ(x,t)|^{2}}dx=1$$
$$\int_{0}^{a}{|A|^{2}}\frac{x^{2}}{a^{2}}dx+\int_{a}^{b}{|A|^{2}}\frac{(b-x)^{2}}{(b-a)^{2}}dx=1$$
$$=\frac{A^{2}}{a^{2}}\frac{a^{3}}{3}+\frac{A^{2}}{(b-a)^{2}}\int_{a}^{b}(b-x)^2dx$$
$$=\frac{A^{2}}{a^{2}}\frac{a^{3}}{3}+\frac{A^{2}}{(b-a)^{2}}[-\frac{(b-x)^{3}}{3}]\rvert_{a}^{b}$$
$$=\frac{A^{2}a}{3}+\frac{A^{2}(b-a)}{3}$$
=>$$A=\sqrt{\frac{3}{b}}$$

(b)
![1.4b](/img/intro-quantumn-mechanics/1-4b.png)

(c)
Atx=a

(d)
$$P=\int_{0}^{a}A^{2}\frac{x^{2}}{a^{2}}dx=\frac{A^{2}}{a^{2}}(\frac{x^{3}}{3})\rvert_{0}^{a}=\frac{A^{2}a}{3}=(\sqrt(\frac{3}{b}))^{2}\frac{a}{3}=\frac{a}{b}$$

When$$b=a,P=1$$
When$$b=2a,P=\frac{1}{2}$$

(e)
$$\<x\>=\int_{a}^{b}{x|Ψ(x,t)|^{2}}dx=\int_{0}^{a}{x\frac{A^2x^2}{a^2}}dx+\int_{a}^{b}{x\frac{A^2(b-x)^2}{(b-a)^2}}dx$$
$$=\frac{A^{2}}{a^{2}}\frac{x^{4}}{4}\rvert_{0}^{a}+\frac{A^{2}}{(b-a)^{2}}\int_{a}^{b}x(b-x)^{2}dx=\frac{3a^2}{4b}+\frac{3}{b(b-a)^2}\int_{a}^{b}(xb^{2}-2bx^{2}+x^{3})dx$$
$$=\frac{3a^2}{4b}+\frac{3}{b(b-a)^2}(\frac{b^{2}x^{2}}{2}-\frac{2bx^{3}}{3}+\frac{x^{4}}{4})\rvert_{a}^{b}=\frac{b+2a}{4}$$
Q.E.D


![1.5](/img/intro-quantumn-mechanics/1-5.png)
Problem1.5
(a)
Let$$\int^{\infty}_{-\infty}{|Ψ|^{2}}dx=1$$
![1.5c_2](/img/intro-quantumn-mechanics/1-5c_2.png)

(b)
$$\<x\>=\int_{-\infty}^{\infty}x\lambdae^{-2\lambda|x|}dx=0,\text{asitsoddfunction}$$
$$\<x^{2}\>=\int_{-\infty}^{\infty}x^{2}\lambdae^{-2\lambda|x|}dx$$
$$=2\lambda\int_{0}^{\infty}x^{2}e^{-2\lambda|x|}dx$$
Bytheformulaofexponentialintegral,
$$=2\lambda(2!(\frac{1}{2\lambda})^{3})=\frac{1}{2\lambda^{2}}$$

(c)
$$\sigma^{2}=\<X^{2}\>-\<X\>^{2}=\frac{1}{2\lambda^{2}}-0=\frac{1}{2\lambda^{2}}$$
$$\sigma=\frac{1}{\lambda\sqrt{2}}$$
![1.5c](/img/intro-quantumn-mechanics/1-5c.png)
Q.E.D
##1.5Momentumn
![1.7](/img/intro-quantumn-mechanics/1-7.png)
Problem1.7
$$\<p\>=m\frac{d\<x\>}{dt}$$
$$\frac{d\<p\>}{dt}=\frac{d^{2}\<x\>}{dt^{2}}=-i\hbar\int{\frac{\partial}{\partialt}(Ψ\frac{\partialΨ}{\partialx})}dx$$
$$=-i\hbar\int{\frac{\partialΨ\*}{\partialt}\frac{\partialΨ}{\partialx}+Ψ\*\frac{\partial^{2}Ψ}{\partialt\partialx}}dx$$
BySchrodingerequation,
$$\frac{\partialΨ\*}{\partialt}=-i\frac{\hbar}{2m}\frac{\partial^{2}Ψ\*}{\partialx^{2}}+\frac{i}{\hbar}VΨ\*$$
$$=-i\hbar\int{(-i\frac{\hbar}{2m}\frac{\partial^{2}Ψ\*}{\partialx^{2}}+\frac{i}{\hbar}VΨ\*)\frac{\partialΨ}{\partialx}+Ψ\*\frac{\partial}{\partialx}(i\frac{\hbar}{2m}\frac{\partial^{2}Ψ}{\partialx^{2}}-\frac{i}{\hbar}VΨ)}dx$$
$$=-i\hbar\int{(-i\frac{\hbar}{2m}\frac{\partial^{2}Ψ\*}{\partialx^{2}}\frac{\partialΨ}{\partialx}+i\frac{\hbar}{2m}\frac{\partial^{3}Ψ}{\partialx^{3}})+(\frac{i}{\hbar}VΨ\*\frac{\partialΨ}{\partialx}-\frac{i}{\hbar}Ψ\*\frac{\partial}{\partialx}(VΨ))}dx$$
As$$-i\hbar(\int{-i\frac{\hbar}{2m}\frac{\partial^{2}Ψ\*}{\partialx^{2}}\frac{\partialΨ}{\partialx}}dx+\frac{i\hbar}{2m}(Ψ\*\frac{\partial^{2}Ψ}{\partialx^{2}}-\int{\frac{\partial^{2}Ψ}{\partialx^{2}}\frac{\partialΨ\*}{\partialx}}dx))$$
$$=-i\hbar(\int{-i\frac{\hbar}{2m}\frac{\partial^{2}Ψ\*}{\partialx^{2}}\frac{\partialΨ}{\partialx}}dx+0-\frac{i\hbar}{2m}(\frac{\partialΨ\}{\partialx}\frac{\partialΨ\*}{\partialx}\rvert_{-\infty}^{\infty}-\int{\frac{\partial^{2}Ψ\*}{\partialx^{2}}\frac{\partialΨ}{\partialx}}dx))$$
$$=-i\hbar(0+0)=0$$
$$\frac{d\<p\>}{dt}=-i\hbar\int{\frac{i}{\hbar}VΨ\*\frac{\partialΨ}{\partialx}-\frac{i}{\hbar}VΨ\*Ψ\frac{\partialV}{\partialx}-\frac{i}{\hbar}VΨ\*\frac{\partialΨ}{\partialx}}dx$$
$$=-i\hbar\int{(-\frac{i}{\hbar}|Ψ|^{2}\frac{\partialV}{\partialx})}dx$$
$$=\<-\frac{\partialV}{\partialx}\>$$
Q.E.D
##1.6TheUncertaintyPrinciple
![1.9](/img/intro-quantumn-mechanics/1-9.png)
Problem1.9
(a)
$$Let\int_{-\infty}^{+\infty}|Ψ(x,t)|^{2}dx=1$$
$$\int_{-\infty}^{+\infty}A^{2}(e^{-a(\frac{mx^{2}}{h}+it)}e^{-a(\frac{mx^{2}}{h}-it)})dx=1$$
$$\int_{-\infty}^{+\infty}A^{2}e^{-2a(\frac{mx^{2}}{h})}dx=1$$
BytheformulaofGuassianIntegral,
$$A^{2}\sqrt{\frac{h\pi}{2am}}=1$$
$$A=(\frac{2am}{h\pi})^{\frac{1}{4}}$$
(b)
$$\frac{\partialΨ}{\partialt}=\frac{\partial}{\partialt}(Ae^{-a(\frac{mx^{2}}{\hbar}+it)})$$
$$=Ae^{-a(\frac{mx^{2}}{\hbar}}\frac{\partial}{\partialt}(e^{-iat})$$
$$=Ae^{-a(\frac{mx^{2}}{\hbar}}(e^{-iat})(-ia)=-iaΨ$$

$$\frac{\partialΨ}{\partialx}=\frac{\partial}{\partialx}(Ae^{-a(\frac{mx^{2}}{\hbar}+it)})$$
$$=A\frac{\partial}{\partialx}(e^{-a(\frac{mx^{2}}{\hbar})})(e^{-iat})$$
$$=Ae^{-iat}e^{-a(\frac{mx^{2}}{\hbar})}(-\frac{2xma}{\hbar})$$
$$=-\frac{2xma}{\hbar}Ψ$$

$$\frac{\partial^{2}Ψ}{\partialx^{2}}=-\frac{2ma}{\hbar}(Ψ+x\frac{\partialΨ}{\partialx})$$
$$=-\frac{2ma}{\hbar}(Ψ-\frac{2max^{2}}{\hbar}Ψ)$$
$$=-\frac{2ma}{\hbar}(1-\frac{2max^{2}}{\hbar})Ψ$$
BytheSchrodingerEquation,
$$i\hbar(-aiΨ)=-\frac{\hbar^{2}}{2m}(-\frac{2ma}{\hbar}(1-\frac{2max^{2}}{\hbar})Ψ)+VΨ$$
$$a\hbar=a\hbar-2ma^{2}x^{2}+V$$
$$V=2ma^{2}x^{2}$$
(c)
$$<x>=\int{-\infty}^{+\infty}x|Ψ|^{2}dx=0$$(OddIntegrand)


##FurtherProblemsForChapter1
![1.14](/img/intro-quantumn-mechanics/1-14.png)$

![1.15](/img/intro-quantumn-mechanics/1-15.png)