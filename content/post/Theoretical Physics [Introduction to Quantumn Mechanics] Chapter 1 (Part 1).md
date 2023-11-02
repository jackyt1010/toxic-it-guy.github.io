---
layout:post
title:"TheoreticalPhysics[IntroductiontoQuantumnMechanics]Chapter1:TheWaveFunction(Part1)"
subtitle:""
description:""
date:2022-10-09
published:true
author: JackyTang
categories:["Physics","Mathematics"]
tags:
-TheorticalPhysics
-QuantumnMechanics
URL:"/2022/10/09/intro-quantumn-mechanics-ch1/"
katex:true
---

<!--more-->
![Coverpage](/img/intro-quantumn-mechanics/cover.png)
##1.1TheSchrödingerEquation
Imagineaparticleofmassm,constrainedtomovealongthex-axis,subjecttosomespecifiedforceF(x,t).Theprogramofclassicalmechanicsistodeterminethepositionoftheparticleatanygiventime:x(t).
Onceweknowthat,wecanfigureoutthevelocity(v=dx/dt),themomentum(p=mv),thekineticenergy$$(T=(l/2)mv^{2}),$$oranyotherdynamicalvariableofinterest.Andhowdowegoaboutdeterminingx(t)?
WeapplyNewton'ssecondlaw:F=ma.This,togetherwithappropriateinitialconditionsdeterminesx(t).<br/>
Quantummechanicsapproachesthissameproblemquitedifferently.Inthiscasewhatwe'relookingforistheparticle'swavefunction,Ψ(x,t),andwegetitbysolvingtheSchrodingerequation:
$$i\hbar\frac{\partialΨ}{\partialt}=-\frac{\hbar^{2}}{2m}\frac{\partial^{2}Ψ}{\partialx^{2}}+VΨ$$
Hereiisthesquarerootof-1,and$$\hbar$$isPlanck'sconstant.
TheSchrodingerequationplaysarolelogicallyanalogoustoNewton'ssecondlaw.

##1.2Thestatsticalinterpretation
Butwhatexactlyisthis"wavefunction,",aparticle,byitsnature,islocalizedatapoint,whereasthewavefunctionisspreadoutinspace.Howcansuchanobjectrepresentthestateofaparticle?Theanswer
isprovidedbyBorn'sstatisticalinterpretationofthewavefunction,whichsaysthat$$|Ψ(x,t)|^{2}$$givestheprobabilityoffindingtheparticleatpointx,attimet-or,
moreprecisely,
$$\int_{a}^{b}{|Ψ(x,t)|^{2}}dx$$={theprobabilityoffindingtheparticlebewteenaandbattimet}<br/>
Probabilityistheareaunderthegraphof$$|Ψ(x,t)|^{2}.$$
Thestatisticalinterpretationintroducesakindofindeterminacyintoquantummechanics,forevenifyouknoweverythingthetheoryhastotellyouabout
theparticle,stillyoucannotpredictwithcertaintytheoutcomeofasimpleexperimenttomeasureitsposition-anquantummechanicshastoofferisstatisticalinfom1ationaboutthepossibleresults.Thisindetenninacy
hasbeenprofoundlydisturbingtophysicistsandphilosophersalike,anditisnaturaltowonderwhetheritisafactofnature.

##1.3Probability
Forcontiuousvariablex,ifwelettheprobabilitydensityfunctionbep(x),thentheprobabilitythatanindividual(chosenatrandom)liesbetweenxandx+dxisequaltop(x)dx.
Theprobabilitythatxliesbetweenaandb(a.finiteinterval)isgivenbytheintegralofp(x):$$P_{ab}=\int_{a}^{b}{p(x)}dx$$andwehavethefollowingequationsforstatistics:
$$1=\int_{-\infty}^{+\infty}{p(x)}dx$$
$$\text{Theexpectationvalue}\<x\>=\int_{-\infty}^{+\infty}{xp(x)}dx$$
$$\text{Theexpectationvalue}\<f(x)\>=\int_{-\infty}^{+\infty}{f(x)p(x)}dx$$
$$\text{Thevariance}\sigma^{2}=<x^{2}>-\<x\>^{2}$$

Example1.1SupposeIdroparockoffacliffofheighth.Asitfalls,Isnapamillionphotographs,atrandomintervals.OneachpictureImeasuretheaveragedistancetherockhasfallen.Question:Whatistheaverageofallthesedistances?
Thatistosay,whatisthetimeaverageofthedistancetraveled?

Solution:Solution:Therockstartsoutatrest,andpicksupspeedasitfalls;itspendsmoretimenearthetop,sotheaveragedistancemustbelessthanh/2.Ignoringairresistance,thedistancexattimetis
$$x(t)=\frac{1}{2}gt^{2}$$

Thevelocityisdx/dt=gt,andthetotalflighttimeis$$T=\sqrt{2h/g}$$Theprobabilitythatthecameraflashesintheintervaldtisdt/T,sotheprobabilitythatagivenphotographshowsadistanceinthecorresponding
rangedxis$$\frac{dt}{T}=\frac{dx}{gt}\sqrt{\frac{2h}{g}}=\frac{1}{2\sqrt{hx}}dx$$
Evidentlytheprobabilitydensityis
$$p(x)=\frac{1}{2\sqrt{hx}}$$
Thus,theaveragedistanceis$$\<x\>=\int_{0}^{h}{x\frac{1}{2\sqrt{hx}}}dx=\frac{1}{2\sqrt{h}}(\frac{2}{3}x^{3/2})\rvert_{0}^{h}=h/3$$<br/>
whichissomewhatlessthanh/2,asanticipated.
<br/>
Problem1.2
(a)	FindthestandarddeviationofthedistributioninExample1.1.
(b)	Whatistheprobabilitythataphotograph,selectedatrandom,wouldshowadistancexmorethanonestandarddeviationawayfromtheaverage?<br/>
(a)
$$\sigma^{2}=<x^{2}>-\<x\>^{2}$$=>
$$<x^{2}>=\int_{0}^{h}{x^{2}\frac{1}{2\sqrt{hx}}}dx=\int_{0}^{h}\frac{x^{3/2}}{2\sqrt{h}}dx=\frac{1}{2\sqrt{h}}(\frac{x^{2/5}}{2.5})\rvert_{0}^{h}=\frac{1}{5\sqrt{h}}h^{2.5}=\frac{h^{2}}{5}$$
$$\sigma=\sqrt{\frac{h^{2}}{5}-(\frac{h}{3})^{2}}=\frac{2}{\sqrt{45}}h=0.2981h$$
<br/>
(b)
$$P=1-\int_{x_{-}}^{x_{+}}p(x)dx=1-\int_{x_{-}}^{x_{+}}\frac{1}{2\sqrt{hx}}dx=1-\frac{1}{2\sqrt{h}}\int_{x_{-}}^{x_{+}}x^{-\frac{1}{2}}dx=1-\frac{1}{2\sqrt{h}}(2x)^{\frac{1}{2}}\rvert_{x_{-}}^{x_{+}}=1-\frac{1}{\sqrt{h}}(\sqrt{x_{+}}-\sqrt{x_{-}})$$
$$x_{+}=\<x\>+\sigma=0.3333h+0.2981h=0.6315h$$
$$x_{-}=\<x\>-\sigma=0.3333h-0.2981h=0.0352h$$
$$P=1-\sqrt{0.6135}+\sqrt{0.0352}=0.393$$<br/>
<br/>
Problem1.3
Considerthegaussiandistribution<br/>
$$p(x)=Ae^{-\lambda(x-a)^{2}}$$
where$$A,a,\text{and}\lambda$$
arepositiverealconstants.(Lookupanyintegralsyouneed.)<br/>
(a)	UsethestatisticalequationtodetermineA.<br/>
(b)	Find$$\<x\>,\<x^{2}\>,A.$$<br/>
(c)	Sketchthegraphofp(x).<br/>
<br/>
<br/>
(a)
Let$$\int_{-\infty}^{+\infty}p(x)dx=1,\int_{-\infty}^{+\infty}Ae^{-\lambda(x-a)^{2}}dx=1$$
=>$$A\int_{-\infty}^{+\infty}e^{-\lambda(x-a)^{2}}dx=1$$
Letu=x-a,du=dx,$$\int_{-\infty}^{+\infty}e^{-\lambda(u)^{2}}du=1$$
By[IntegralofGaussian](https://quantummechanics.ucsd.edu/ph130a/130_notes/node87.html),<br/>
$$A\sqrt{\frac{\pi}{\lambda}}=1$$=>$$A=\sqrt{\frac{\lambda}{\pi}}$$
(b)
$$\<x\>=\int_{-\infty}^{+\infty}xp(x)dx=\sqrt{\frac{\lambda}{\pi}}\int_{-\infty}^{+\infty}xe^{-\lambda(x-a)^{2}}dx$$
Letu=x-a,du=dx,
$$\<x\>=\sqrt{\frac{\lambda}{\pi}}\int_{-\infty}^{+\infty}(u+a)e^{-\lambda(x-a)^{2}}du$$
$$\sqrt{\frac{\lambda}{\pi}}(\int_{-\infty}^{+\infty}ue^{-\lambda(x-a)^{2}}du+a\int_{-\infty}^{+\infty}e^{-\lambda(x-a)^{2}}du)$$
As$$ue^{-\lambda(x-a)^{2}}$$isoddfunction,
$$\<x\>=\sqrt{\frac{\lambda}{\pi}}(0+a\sqrt{\frac{\pi}{\lambda}})=a$$
<br/>
$$\<x^{2}\>=\int_{-\infty}^{+\infty}x^{2}p(x)dx=\sqrt{\frac{\lambda}{\pi}}\int_{-\infty}^{+\infty}x^{2}e^{-\lambda(x-a)^{2}}dx$$
Letu=x-a,du=dx,
$$\<x^{2}\>=\sqrt{\frac{\lambda}{\pi}}\int_{-\infty}^{+\infty}(u+a)^{2}e^{-\lambda(x-a)^{2}}du$$
$$=\sqrt{\frac{\lambda}{\pi}}\int_{-\infty}^{+\infty}(u^{2}+2ua+a^{2})e^{-\lambda(x-a)^{2}}du$$
$$=\sqrt{\frac{\lambda}{\pi}}((\int_{-\infty}^{+\infty}u^{2}e^{-\lambda(x-a)^{2}})du+0+a^{2}\sqrt{\frac{\pi}{\lambda}})$$
By[theformulaofGaussianIntegral](http://www.hep.upenn.edu/~johnda/Papers/GausInt.pdf),
$$=\sqrt{\frac{\lambda}{\pi}}(\frac{1}{2\lambda}\sqrt{\frac{\pi}{\lambda}}+a^{2}\sqrt{\frac{\pi}{\lambda}})=\frac{1}{2\lambda}+a^{2}$$
<br/>
$$\sigma=\sqrt{\<x^{2}\>-\<x\>^{2}}=\sqrt{\frac{1}{2\lambda}+a^{2}-a^{2}}=\frac{1}{\sqrt{2\lambda}}$$
![1.3cAns](/img/intro-quantumn-mechanics/1-3c.png)
