---
layout:     post
title:      "Self-Education-Theoretical Physics [Landau Mechanics Notes]  Chapter 1: The Equation of Motion"
date:     2022-08-23
author:  Jacky Tang
categories: [ "Physics"]
tags:
    - Physics
URL: "/2022/08/23/landau-mechanics-ch1/"
---
![Coverpage](/img/landau-mechanics-ch1/landau.jpg)
 ## 1. A generalized coordinate

In mechanics, objects of negligible size in motion are usually treated as mass points, its position is determined by r(x, y, z), abbreviated as r.

Its velocity and acceleration are 

![公式](/img/landau-mechanics-ch1/1.png)


For a system, if it contains N particles, in order to uniquely determine the positions of all particles, 3N coordinates are required, which are called degrees of freedom.

In a system with a degree of freedom s, the coordinates of a particle in a system are abstracted, called generalized coordinates

![公式](/img/landau-mechanics-ch1/2.png)

These are limited to traditional coordinates such as x, y, z, but also angles, distances (polar coordinates, spherical coordinates). Correspondingly, the generalized velocity can also be defined:

![公式](/img/landau-mechanics-ch1/3.png)

 ## 2.  The principle of least action

With ![公式](/img/landau-mechanics-ch1/4.png), a system ![公式](/img/landau-mechanics-ch1/5.png) can be determined, L is called Lagrangian function, but its form is not arbitrary and needs to meet the following conditions:

At time t1 and t2, the movement of the system during this time period makes the integral  ![公式](/img/landau-mechanics-ch1/6.svg) get the minimum value, this integral is called the action, and this requirement is called the principle of least action ![公式](/img/landau-mechanics-ch1/7.svg)

So, we can deduce L that satisfies the principle of least action. What properties will it have? 

For convenience, it is assumed that the system has only one degree of freedom, that is, a one-dimensional problem, and only one coordinate q(t) needs to be known. If the motion q(t) is the function that minimizes the action S, then adding any non-zero function to q to get the ![公式](/img/landau-mechanics-ch1/8.svg), the action S cannot be minimized. ![公式](/img/landau-mechanics-ch1/9.svg)Of course, in order to ensure that the particle is still in its original position at time t1 and t2, the boundary conditions must be satisfied

S thus increases by an amount ![公式](/img/landau-mechanics-ch1/10.svg)  

 

By Expansion and keeping only the first-order terms, we get

![公式](/img/landau-mechanics-ch1/11.svg)  

According to the definition of ![公式](/img/landau-mechanics-ch1/12.svg), we then get ![公式](/img/landau-mechanics-ch1/13.svg)  and substitute it into  ![公式](/img/landau-mechanics-ch1/14.svg)

 Now we need to deal with the second term, which happens to be integral by parts: ![公式](/img/landau-mechanics-ch1/15.svg)  

 Due to the existence of the boundary condition ![公式](/img/landau-mechanics-ch1/16.svg), the first term must be 0, and only the second term is retained, so the change of action is

![公式](/img/landau-mechanics-ch1/17.svg)  

 Since ![公式](/img/landau-mechanics-ch1/18.svg) is an arbitrary function, for this integral to hold, the interior must always be 0, so![公式](/img/landau-mechanics-ch1/19.svg) , this equation is the differential equation of motion of the system, also known as the Lagrange equation For systems with multiple degrees of freedom s, the equations become a system of equations ![公式](/img/landau-mechanics-ch1/20.svg) 

 When solving this second-order differential equation system with s equations, 2s initial values (that is, s generalized positions and s generalized velocities)are needed to be given, and all subsequent evolutions of the system can be uniquely determined.

-Some Properties

The Lagrangian quantities of two independent physical systems can be expressed as two separate sums ![公式](/img/landau-mechanics-ch1/21.svg). If there is an interaction relationship, they cannot be added together.

The Lagrangian of a system can be multiplied by any non-zero constant without changing the properties of the system. ![公式](/img/landau-mechanics-ch1/22.svg) describes the same system

 

Simple Application: Deriving Newton's Law of Inertia
Given a system that contains only one free mass point, coordinates ![公式](/img/landau-mechanics-ch1/23.svg), mass m, and initial velocity is ![公式](/img/landau-mechanics-ch1/24.svg), moving in three dimensions; there is no external force.

The Lagrangian is a ![公式](/img/landau-mechanics-ch1/25.svg),  So ![公式](/img/landau-mechanics-ch1/26.svg)

then ![公式](/img/landau-mechanics-ch1/27.svg), bringing into the equation of motion

![公式](/img/landau-mechanics-ch1/28.svg)

which is ![公式](/img/landau-mechanics-ch1/29.svg)

Since L does not contain xyz, so ![公式](/img/landau-mechanics-ch1/30.svg)

Bring in ![公式](/img/landau-mechanics-ch1/31.svg) , which is the conservation of momentum

In fact, it is describing ![公式](/img/landau-mechanics-ch1/32.svg).Therefore, the coordinates of the free particle can only be expressed as: ![公式](/img/landau-mechanics-ch1/33.svg) , it is moving in a straight line; if the initial velocity is 0, it will remain at rest.



## 3. Galileo’s relativity principle

In the generalized coordinate q, q is only an abstract reference, and its specific value can only be uniquely determined by relying on the determination of the reference frame; in different reference systems, the real value of q will be different to some extent.

The inertial reference frame is a special reference frame, in which the space is isotropic and uniform, and the time is also passing uniformly; in this frame of reference, the object has inertia, that is, a stationary object without external force, which remains at rest forever.

Between different reference frames, Galileo transformation can be done to transform the description q in one reference frame K to the description q' in another reference frame K', satisfying (assuming that the reference frame K' moves at a velocity V relative to K) :

![公式](/img/landau-mechanics-ch1/34.svg)
The latter t'=t is the time concept of classical mechanics, that is, in any frame of reference, the passage of time is uniform.

Inevitably, the laws of mechanics must remain unchanged in different reference frames, which is called Galileo's principle of relativity, that is, the laws of mechanics are invariant under Galilean transformation.



## 4. The Lagrangian for a system of particles

By considering a system of particles which interact with one another but with no other bodies, it is called a closed system. It is found that the interaction between the particles can be described by adding to the Lagrangian for non-interacting particles a certain function of the co-ordinates, which depends on the nature of the interaction.t Denoting this function by -U, we have

![公式](/img/landau-mechanics-ch1/35.png)
where r is the radius vector of the particle. This is the general form of the Lagrangian for a closed system.!
 The 
![公式](/img/landau-mechanics-ch1/36.png)


is called the kinetic energy, and U the potential energy, of the system.Knowing the Lagrangian, we can derive the equations of motion:
 
 ![公式](/img/landau-mechanics-ch1/37.png)

 Substitution of  this  gives

![公式](/img/landau-mechanics-ch1/38.png)


In this form the equations of motion are called Newton’s equations and form the basis of the mechanics of a system of interacting particles. The vector
                                                         
![公式](/img/landau-mechanics-ch1/39.png)



which appears on the left-hand side of equation is called the force on the a th particle.
 

## 5. Problems

Find the Lagrangian for each of the following systems when placed in a uniform gravitational field (acceleration g)
![公式](/img/landau-mechanics-ch1/40.png)
My Answer:
![公式](/img/landau-mechanics-ch1/41.png)
![公式](/img/landau-mechanics-ch1/42.png)

My Answer:
![公式](/img/landau-mechanics-ch1/43.png)
![公式](/img/landau-mechanics-ch1/44.png)
![公式](/img/landau-mechanics-ch1/45.png)

My Answer:
3(a)
![公式](/img/landau-mechanics-ch1/46.png)

3(b)
![公式](/img/landau-mechanics-ch1/47.png)

3(c)
![公式](/img/landau-mechanics-ch1/48.png)
