---
title: "Monte Carlo simulations of 2D Ising model"
description: "Visualizing the 2D Ising model by performing Metropolis-Hastings Algorithm to study phase transitions and critical phenomena in magnetic systems."
dateString: June 2024- July 2024
draft: false
tags: ["Monte Carlo", "MCMC", "Markov Chains", "Metropolis-Hastings", "Statistical Physics"]
showToc: false
weight: 205
cover:
    image: "projects/isingmodel/cover.png"
--- 
<!-- ### 🔗 [Colab Notebook](https://colab.research.google.com/drive/1TOw7W_WU4oltoGZfZ_0krpxmhdFR2gmb) -->

## Description

**Self-Guided Project**

This project simulates a 2D Ising model to study the behaviour of some observables, like the magnetisation m, the specific heat C_V and the magnetic susceptibility χ . The simulation is performed using the Metropolis-Hastings algorithm, a type of Markov Chain Monte Carlo (MCMC) method.

# Ising Model

<p>
The <strong>Ising model</strong> is a theoretical model in statistical physics originally developed to describe <strong>ferromagnetism</strong>. It models a system of magnetic particles arranged either as a <strong>1D chain</strong> or a <strong>2D lattice</strong>, with one atom or molecule located at each lattice site <em>i</em>.
</p>

<p>
Each molecule or atom is assigned a <strong>magnetic moment</strong>, represented in the model by a discrete variable called a <strong>spin</strong>, denoted <strong>s<sub>i</sub></strong>, which can take on values of <strong>&plusmn;1</strong>. The two possible values indicate whether two spins <strong>s<sub>i</sub></strong> and <strong>s<sub>j</sub></strong> are:
<ul>
  <li><strong>Parallel (aligned):</strong> &nbsp; s<sub>i</sub> &middot; s<sub>j</sub> = +1</li>
  <li><strong>Antiparallel (opposed):</strong> &nbsp; s<sub>i</sub> &middot; s<sub>j</sub> = −1</li>
</ul>
</p>

<p>
A system of two spins is considered to be in a <strong>lower-energy state</strong> when the magnetic moments are aligned. If the magnetic moments point in opposite directions, the system is in a <strong>higher-energy state</strong>. As a result, the system tends to align all magnetic moments in the same direction to minimize its total energy. When most of the spins are aligned, the collection of atoms behaves like a <strong>macroscopic magnet</strong>.
</p>

<div style="display: flex; justify-content: flex-start; gap: 10px;">
  <figure style="margin: 0;">
    <img src="/projects/isingmodel/spins.png" style="width: 100%;">
  </figure>
</div>

<br>
<p>
A <strong>phase transition</strong> in the context of the Ising model refers to the transition from an <strong>ordered state</strong> to a <strong>disordered state</strong>. Above the <strong>critical temperature</strong> (<strong>T<sub>c</sub></strong>), a ferromagnet is in a disordered phase, which corresponds to a random distribution of spin values. Below <strong>T<sub>c</sub></strong>, the system becomes ordered - nearly all spins align, even in the absence of an external magnetic field <strong>H</strong>.
</p>

<p>
When a cooled ferromagnet is heated back up, the net magnetization vanishes at <strong>T<sub>c</sub></strong> and the system transitions from the ordered to the disordered phase. This behavior characterizes a <strong>second-order phase transition</strong>, where magnetization vanishes continuously.
</p>

# 2D Ising Model

<p>
We consider a 2-dimensional nearest neighbour Ising Model with:
</p>
<ul>
  <li><strong>N<sup>2</sup></strong> = total number of sites on the lattice</li>
  <li><strong>&sigma;<sub>k</sub> &isin; {+1, -1}</strong> = individual spin site on the lattice</li>
</ul>

<div style="display: flex; justify-content: flex-start; gap: 10px;">
  <figure style="margin: 0;">
    <img src="/projects/isingmodel/lattice.png" style="width: 50%;">
  </figure>
</div>



<p>
The Hamiltonian is:
</p>
<p style="text-align: center;">
  <strong>H(<b>&sigma;</b>) = - &sum;<sub>&lt;ij&gt;</sub> J<sub>ij</sub> &sigma;<sub>i</sub> &sigma;<sub>j</sub> - &sum;<sub>i</sub> h<sub>i</sub> &sigma;<sub>i</sub></strong>
</p>

<p>
where <strong>J<sub>ij</sub></strong> is the interaction strength and <strong>h<sub>i</sub></strong> is the external local magnetic field.
</p>

<p>
In this system, a particular configuration <strong>&sigma;</strong> has the following probability:
</p>

<p style="text-align: center;">
  <strong>P(<b>&sigma;</b>) = (1/Z) &times; e<sup>-&beta;H(<b>&sigma;</b>)</sup></strong>
</p>

<p>
where
</p>

<p style="text-align: center;">
  <strong>Z = &sum;<sub>{<b>&sigma;</b>}</sub> e<sup>-&beta;H(<b>&sigma;</b>)</sup></strong>
</p>

<p>
is the partition function with <strong>&beta; = 1/(k<sub>B</sub>T)</strong>, and the sum is over all possible spin configurations of the system.
</p>

<p>
For <strong>h = 0</strong>, if the number of dimensions is larger than one, the Ising model exhibits a second-order phase transition.
Below a certain critical temperature, spontaneous magnetization occurs.
For <strong>d = 2</strong>, the transition temperature was calculated analytically by <strong>Onsager</strong>:
</p>

<p style="text-align: center;">
  <strong>T<sub>C</sub> = 2 / ln(1 + √2)</strong>
</p>

<p>
In our simulation, for simplicity, we choose a uniform ferromagnetic medium (i.e., <strong>J<sub>ij</sub> = J = 1</strong>) and no external field (i.e., <strong>h<sub>i</sub> = h = 0</strong>). We also fix the Boltzmann constant <strong>k<sub>B</sub> = 1</strong>.
</p>

<p>
With these assumptions, the Hamiltonian simplifies to:
</p>

<p style="text-align: center;">
  <strong>H(<b>&sigma;</b>) = - &sum;<sub>&lt;ij&gt;</sub> &sigma;<sub>i</sub> &sigma;<sub>j</sub></strong>
</p>

<p>
Finally, we apply periodic boundary conditions, ensuring that all spins have the same number of neighbours.
</p>
We start with a random configuration,
<div style="display: flex; justify-content: flex-start; gap: 10px;">
  <figure style="margin: 0;">
    <img src="/projects/isingmodel/image1.png" style="width: 100%;">
  </figure>
</div>

# Metropolis-Hastings Algorithm
<div style="display: flex; justify-content: flex-start; gap: 10px;">
  <figure style="margin: 0;">
    <img src="/projects/isingmodel/image2.png" style="width: 200%;">
  </figure>
</div>

The main steps for the implementation of Metropolis algorithm are:

1) Prepare an initial configuration of N spins
2) Flip the spin of a randomly chosen lattice site.
3) Calculate the change in energy dE.
4) If dE < 0, accept the move. Otherwise accept the move with probability exp^{-dE/T}. This satisfies the detailed 
   balance condition, ensuring a final equilibrium state.
5) Repeat steps 2-4.

# Snapshots of the configuration
We start with a random initial condition and then plot the instantaneous configurations, as the system coarsens to its equilibrium state.

<div style="display: flex; justify-content: flex-start; gap: 10px;">
  <figure style="margin: 0;">
    <img src="/projects/isingmodel/image3.png" style="width: 200%;">
  </figure>
</div>

Time evolution of the 2D Ising model at low temperature, illustrating domain coarsening. The simulation begins with a random configuration of spins (red = +1, blue = −1) at time 𝑡=0. As time progresses, energetically favorable spin alignments form and grow. By 𝑡=1000, the system reaches near-complete magnetic order, with spins predominantly aligned, indicating a transition to a ferromagnetic phase.

<div style="display: flex; justify-content: flex-start; gap: 10px;">
  <figure style="margin: 0;">
    <img src="/projects/isingmodel/ising_simulation.gif" style="width: 200%;">
  </figure>
</div>

# Analysis
We now proceed with the analysis of the behaviour of the different observables as functions of the temperature T and of the size of the system N. The expressions are given as:

<div style="display: flex; justify-content: flex-start; gap: 10px;">
  <figure style="margin: 0;">
    <img src="/projects/isingmodel/image4.png" style="width: 200%;">
  </figure>
</div

<div style="display: flex; justify-content: flex-start; gap: 10px;">
  <figure style="margin: 0;">
    <img src="/projects/isingmodel/image5.png" style="width: 200%;">
  </figure>
</div>

The Ising model is a paradigmatic model of statistical mechanics that allows us to observe some very interesting phenomena like the **phase transition**. In particular, from the plot of the magnetisation m, it is clear how, going through the critical point, the systems changes from a paramagnetic phase (with no magnetisation) to a ferromagnetic phase (in which a spontaneous magnetisation emerges). This effect is one of the simplest examples of the **symmetry breaking**.

<br>


# Ergodicity Breaking

<br>
<p>
In addition to exhibiting a second-order phase transition, the Ising model is also an ideal system for studying <strong>ergodicity breaking</strong> - the transition in which the system loses its ability to explore the entire configuration space.
</p>
<br>
<p>
In our simulation, we observe that <strong>above the critical temperature</strong> (i.e., <strong>T &gt; T<sub>c</sub></strong>), the system is <strong>ergodic</strong>: it explores many different configurations <strong>{&sigma;<sub>⃗</sub>}</strong>, and the magnetization fluctuates around zero over time. However, <strong>below the critical temperature</strong> (i.e., <strong>T &lt; T<sub>c</sub></strong>), the system becomes <strong>non-ergodic</strong>, remaining trapped in one of the two ordered states. This means it explores only a <strong>limited region of phase space</strong> during the simulation.
</p>
<br>
<p>
To study this behavior, we analyze three temperature regimes:
</p>

<ol>
  <li>For <strong>T &gt; T<sub>c</sub></strong>, the free energy <strong>f(m)</strong> exhibits a single minimum at <strong>m = 0</strong>, corresponding to the disordered (paramagnetic) phase.</li>
  <li>For <strong>T = T<sub>c</sub></strong>, the free energy shows two coinciding minima at <strong>m = 0</strong>, indicating criticality and maximal susceptibility to fluctuations.</li>
  <li>For <strong>T &lt; T<sub>c</sub></strong>, the free energy develops a double-well structure with minima at <strong>m = &plusmn;m<sup>*</sup></strong>, indicating spontaneous symmetry breaking and ergodicity breaking.</li>
</ol>

<p>
The critical temperature for the 2D Ising model is approximately <strong>T<sub>c</sub> &asymp; 2.269</strong>.
</p>

<p>
The figure below illustrates this transition using magnetization time series and histograms for each regime:
</p>

<br>

<div style="display: flex; justify-content: flex-start; gap: 10px;">
  <figure style="margin: 0;">
    <img src="/projects/isingmodel/image6.png" style="width: 200%;">
  </figure>
</div>
<br>
<p>
The top row displays the <strong>magnetization per spin</strong> as a function of Monte Carlo (MC) steps, while the bottom row shows the corresponding <strong>histograms</strong> of sampled magnetization values over time.
</p>
<br>
<ul>
  <li>
    <strong>For T &gt; T<sub>c</sub> , &beta; = 0.35</strong>:<br>
    In the high-temperature (disordered) phase, the magnetization fluctuates rapidly around zero, and the histogram is approximately Gaussian, centered at <strong>m = 0</strong>. This confirms that the system is <strong>ergodic</strong>, exploring the full configuration space over time.
  </li>
  <br>
  <li>
    <strong>For T &asymp; T<sub>c</sub> , &beta; = 0.44</strong>:<br>
    Near the critical temperature, the magnetization exhibits long-lived excursions between positive and negative states. The histogram becomes <strong>bimodal</strong>, indicating two competing phases. The system starts to show <strong>partial ergodicity breaking</strong> due to critical slowing down - transitions between phases are rare but still occur.
  </li>
  <br>
  <li>
    <strong>For T &lt; T<sub>c</sub> , &beta; = 0.5</strong>:<br>
    In the low temperature (ordered) phase, the system becomes trapped in a strongly magnetized state and does not switch to the opposite phase. The histogram has a single sharp peak far from zero. This behavior shows clear <strong>ergodicity breaking</strong>: the system explores only one of the two symmetry-broken minima.
  </li>
</ul>
<br>
<p>
Together, these plots demonstrate how the Ising model transitions from an ergodic to a non-ergodic system as temperature decreases past the critical point <strong>T<sub>c</sub> &asymp; 2.269</strong>.
</p>
<br>

# References
<ol>
  <li>
    <a href="https://www.thphys.uni-heidelberg.de/~wolschin/statsem21_3s.pdf" target="_blank">
      One and two dimensional Ising model: Statistical Physics Seminar by Prof. Wolschin
    </a>
  </li>
  <li>
    <a href="https://itp.uni-frankfurt.de/~mwagner/teaching/C_WS19/projects/Ising_proj.pdf" target="_blank">
      Final Project: The 2D Ising Model, Author – Laurin Pannullo
    </a>
  </li>
  <li>
    <a href="http://rajeshrinet.github.io/blog/2014/ising-model/" target="_blank">
      Ising Model Blog by Rajesh Singh
    </a>
  </li>
  <li>
    Mehran Kardar, <em>Statistical Physics of Particles</em>, Cambridge University Press, 2007.
  </li>
  <li>
    R.K. Pathria and Paul D. Beale, <em>Statistical Mechanics</em>, 3rd Edition, Elsevier, 2011.
  </li>
</ol>
