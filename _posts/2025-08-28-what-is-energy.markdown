---
layout: post
title:  "What is meant by \"energy\" in the calculus of variations"
date:   2025-08-28 16:08:50 -0400
---

# Introduction
Hi, and thanks for taking a look at the first post in my blog! I had originally started this blog with the intention of writing about gradient descent methods in the calculus of variations, but I ultimately decided that I would like to start my blog somewhere more accessible.

What follows here is an answer to a simple question I was too afraid to ask when I started work in this field, along with some of the connections I've made between research-level problems in the calculus of variations and physical concepts which are (hopefully) easily understandable to a general audience. A fair disclaimer that what follows is mostly based on my own personal understanding of the physical and mechanical processes described below, and I'm by no means an expert in physics or mechanics.


# What do we mean by \"energy\"?
In the calculus of variations, we are often interested in integral functionals that look like

$$
\mathcal{I}(u)= \int_\Omega f(x,u)~dx
$$

or

$$
\mathcal{E}(u)= \int_\Omega f(x,u,Du)~dx$$

defined on some suitable function space (usually something like $L^2(\Omega)$ or $W^{1,2}(\Omega)$) and a smooth enough (usually Lipschitz) domain $\Omega\subset \mathbb{R}^n$. Either one of these functions above can be called the \"energy\" associated to the function $u$. By \"energy\", we do literally mean *energy*. In most high school physics classes, we learn about *potential energy* $PE$, the stored energy of an object, and *kinetic energy* $KE$, the energy of the object's motion. We then usually learn that the total mechanical energy ($ME$), is written as the sum of potential and kinetic energy: 

$$
ME = PE + KE. \tag{1}
$$

Usually this culminates in some kind of conservation law, which states that the total energy of a closed system is conserved: 

$$
PE_1 + KE_1 = PE_2 + KE_2. 
$$

Indeed, the quantity which appears in (1) is called the *Hamiltonian*, measured in units of energy, commonly joules (J). It represents the total energy of a system. But in mechanics there is another construction of energy called the *Lagrangian*, also measured in units of energy. It is defined as the *difference* between an object's kinetic and potential energies: 

$$
L = KE - PE.
$$

This is also the notion of energy that is used in the calculus of variations.


# Why the Lagrangian?
The simple answer is so that all the machinery behind the calculus of variations works. Suppose that we can represent the Lagrangian of a system can written as 

$$
L(t,u(t),Du(t)) \tag{2}
$$

where 
$L\in C^2(\Omega\times \mathbb{R}\times \mathbb{R}^n;\mathbb{R})$. Then we may define the *action* of the system between time $t_1$ and $t_2$ as the definite integral of the Lagrangian over the interval $[t_1,t_2]$: 

$$
\mathcal{S}(u)= \int_{t_1}^{t_2} L(t,u(t),Du(t))~d{t}. \tag{3}
$$

The action is commonly measured in units of joule-seconds ($J\cdot s$). Think about it as the total accumulation of all the energies $L(t,u(t),Du(t))$ throughout the interval $[t_1,t_2]$. 

Now the reason for this Lagrangian framework comes from another fundamental concept in physics: the *principle of least action*. Roughly, what this says is that physical systems will take the trajectory that will minimize their action. You might have heard somewhere that nature is lazy: what this means in this context is that whatever mechanical system we are dealing with, it wants to take the most efficient path between time $t=t_1$ and $t=t_2$.

Think about it this way: you are on your drive home after a long day at work. You have a choice between two paths: one is a route with few turns where you are on the highway most of the time, and the other takes you 20 miles out of the way and takes you through various school zones, construction zones, etc., so you will be making quite a few speed changes as well. Of course, it's absurd to think of taking this second route, and it's exactly because you would waste a lot of energy needlessly by going this way. Nature thinks the same way in determining the behavior of mechanical systems. 

Back to the mathematics at hand here, what this means is that in the calculus of variations we are interested in problems of the form 

$$
\inf_{u\in X} \mathcal{S}(u) = \inf_{u\in X}\int_{t_1}^{t_2} L(t,u(t),Du(t))~dt, \tag{4}
$$

where $X$ is some appropriate function space for the problem at hand. Again, remember here that for every $t$ in $[t_1,t_2]$, the Lagrangian $L(t,u(t),Du(t))$ just tells us the difference between the system's kinetic and potential energies at time $t$. As this system travels from time $t=t_1$ to $t=t_2$, remember that it wants to take the most efficient path, and this efficiency is measured by the action. When we integrate over $[t_1,t_2]$, we are adding up the contributions of the energies encoded by $L(t,u(t),Du(t))$ for all time $t$ in this interval, and it is this accumulated energy in bulk that we would like to minimize.

How so-called \"variational problems\" like (4) are analyzed depends heavily on the problem itself, and are the subject of future blog posts. Notice that in (4) \"inf\" is used and not \"min\"; in fact, for most interesting variational problems, establishing even the *existence* of a minimizer to a given energy functional (i.e., *action*) is a tricky matter. We only briefly illustrate some of the concepts above with the example below.


# An example: mass-spring system
Consider an object with mass $m$ attached to a spring with spring constant $k$ that slides without friction along a horizontal surface. Let us denote by $x(t)$ the displacement of the object from equilibrium after $t$ seconds. According to Newton's second law of motion, which states that an object's acceleration is directly proportional to the force acting on it and inversely proportional to its mass, so

$$
    F = ma = m\ddot{x}. \tag{5}
$$

On the other hand, Hooke's Law says that the force needed to extend or compress a spring is directly proportional to its displacement, so 

$$
    F = -kx.\tag{6}
$$

Combining (5) and (6), we arrive at the familiar ordinary differential equation describing a simple harmonic oscillator: 

$$
m\ddot{x}+kx=0\tag{7}.
$$

Now multiplying each of these forces by $\dot{x}$ and integrating wrt $t$ from $0$ to $s$, we find 

$$
\begin{align*}
    \int_0^s m\ddot{x}\dot{x}~dt &= \int_0^s m\frac{\text{d}}{\text{d}t}\left(\frac{1}{2}\dot{x}^2\right)~dt \\
        &= \frac{1}{2}m\dot{x}(s)^2
\end{align*}
$$

and 

$$
\begin{align*}
    \int_0^s k{x}\dot{x}~dt &= \int_0^s k\frac{\text{d}}{\text{d}t}\left(\frac{1}{2}{x}^2\right)~dt \\
        &= \frac{1}{2}k{x}(s)^2.
\end{align*}
$$

Now recalling that potential energy is the energy contribution from displacement and kinetic energy is the contribution from velocity, we have 

$$
    PE = \frac{1}{2}kx^2\quad\text{and}\quad KE = \frac{1}{2}m\dot{x}^2. 
$$

Consequently we have for the Hamiltonian

$$
H(x,\dot{x}) = KE + PE = \frac{1}{2}m\dot{x}^2 + \frac{1}{2}kx^2
$$

and for the Lagrangian

$$
L(x,\dot{x}) = KE-PE = \frac{1}{2}m\dot{x}^2-\frac{1}{2}kx^2. 
$$


# References
1. [Feynman lectures, Principle of least action](https://www.feynmanlectures.caltech.edu/II_19.html)



