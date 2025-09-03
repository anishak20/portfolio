---
title: "Neutron star as a signal for quark-gluon plasma formation"
description: "Master's Thesis"
dateString: Aug 2024- Dec 2025
draft: false
tags: ["Neutron stars", "QGP", "QCD", "Numerical Methods"]
weight: 103
cover:
    image: "/blog/thesis/cover.png"
---

# Description

**Supervisor:** **Prof. S. Somorendro Singh** (Professor, Dept. of Physics and Astrophysics, University of Delhi) 

In this study, I conducted an in depth literature review of **Quantum Chromodynamics** (QCD) focusing on the quark-gluon plasma phase and the MIT Bag Model. I implemented the [paper](https://iopscience.iop.org/article/10.1086/309144) and investigated the **Equation of State** (EoS) of strange quark matter  using the Density Dependent Quark Mass (DDQM) model, an extension of the MIT Bag Model, to better understand the internal structure of neutron stars.

## Density-Dependent Quark Mass Model

Quark matter in the cores of neutron stars is expected to exist in the form of **quark-gluon plasma** (QGP). It is referred as strange quark matter (SQM). The study of QGP requires non-perturbative QCD, and one approach involves using phenomenological models such as the Bag model.

An alternative to the MIT Bag model is the Density Dependent Quark Mass Model where the quark masses are parametrized as functions of the baryon density as mentioned in [Anand et al., 2000](https://iopscience.iop.org/article/10.1086/309144):

<div style="display: flex; justify-content: center; margin: 10px 0;">
  <img src="/blog/thesis/mass.png" style="max-width: 100%; height: auto;">
</div>

The system is in the presence of a magnetic field **B** which is directed along the z-axis. The energy of the charged particle of mass **m** and charge **q** in the presence of **B** is given by:

<div style="display: flex; justify-content: center; margin: 10px 0;">
  <img src="/blog/thesis/energy.png" style="max-width: 100%; height: auto;">
</div>

The expression for the thermodynamic potential follows [Anand et al., 2000](https://iopscience.iop.org/article/10.1086/309144):

<div style="display: flex; justify-content: center; margin: 10px 0;">
  <img src="/blog/thesis/potential1.png" style="max-width: 80%; height: auto;">
</div>

> _where the second term is due to the contribution from gluons._

<div style="display: flex; justify-content: center; margin: 10px 0;">
  <img src="/blog/thesis/potential2.png" style="max-width: 100%; height: auto;">
</div>

Standard thermodynamic relations yield the expressions for pressure, energy density, entropy, and specific heat:

<div style="display: flex; justify-content: center; margin: 10px 0;">
  <img src="/blog/thesis/relations.png" style="max-width: 50%; height: auto;">
</div>

Hence, these are numerically computed for a range of temperatures at chemical potential = **300 MeV**:

<div style="display: flex; justify-content: center; margin: 10px 0;">
  <img src="/blog/thesis/plots.png" style="max-width: 120%; height: auto;">
</div>

From the interaction term plot, we observe that as the temperature increases, the interaction term gradually decreases towards zero. It also indicates a critical temperature value around <span>T &approx; 200&nbsp;MeV</span> at which the transition of hadronic matter may occur.

The nature of the entropy density plot suggests a continuous, smooth second-order transition from the confined hadronic phase to a deconfined phase of quarks and gluons. Furthermore, the **speed of sound** was computed and compared with both lattice and curvature data, showing similar trend at higher temperatures. 

Hence, DDQM Model is a reasonable approximation for describing the EoS of QGP at high temperature and high density conditions that are present inside a neutron star.

<div style="display: flex; justify-content: center; margin: 10px 0;">
  <img src="/blog/thesis/cs2.png" style="max-width: 60%; height: auto;">
</div>

<div style="display: flex; flex-direction: column; gap: 15px; margin-top: 15px;">

  <a href="https://drive.google.com/file/d/1G-Ww_Pvn-I0Jd1doXdVe5DYmvnPAvA-U/view?usp=sharing" target="_blank" rel="noopener" style="text-decoration: none;">
    <button style="width: 100%; padding: 14px 24px; font-size: 16px; background-color: #007acc; color: white; border: none; border-radius: 6px; cursor: pointer;">
      Thesis Report
    </button>
  </a>

</div>

<br><br>

View my [Github Repository](https://github.com/anishak20/Master-Thesis/tree/main) for the full details and implementation of the work.
