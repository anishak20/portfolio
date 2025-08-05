---
title: "Flavor Physics: Precision Measurements of CKM Matrix elements"
description: "To extract the CKM matrix element V₍ub₎, the shape parameter α, the form factor normalization f₊(0), and their associated uncertainties for precision flavor physics measurements."
dateString: June 2023- Nov 2023
draft: false
tags: ["vub", "flavor physics", "Chi square", "Python"]
weight: 104
cover:
    image: "/blog/reyes/cover2.png"
    # caption: "A sample landmark detection on a photo by Ayo Ogunseinde taken from Unsplash"
---

# Description

**Supervisor:** [**Dr. Sergi Gonzàlez-Solís**](https://inspirehep.net/authors/1247615) (Serra Húnter Fellow, Institut de Ciències del Cosmos, Universitat de Barcelona previously associated with Los Alamos National Lab, USA)

This project was carried out during and post [**REYES 2023**](https://physics.berkeley.edu/visiting-students/reyes-remote-experience-young-engineers-and-scientists). I extracted the CKM matrix element **V₍ub₎**, the shape parameter **α**, the form factor normalization **f₊(0)**, and their associated uncertainties using non-linear least squares optimization method. The methodology and approach were adapted from the [paper 1](https://arxiv.org/pdf/1805.11262) and [paper 2](https://arxiv.org/pdf/2110.06153).

# Introduction
The B meson is a bound state consisting of a bottom (b) quark and either an up or down quark. It is an unstable, heavy meson that decays via the weak interaction, making it a valuable probe for studying flavor physics and the elements of the CKM matrix. 

Our interest lies in charged current interactions (weak interactions), which have their flavor structure encoded in the [CKM matrix](https://en.wikipedia.org/wiki/Cabibbo%E2%80%93Kobayashi%E2%80%93Maskawa_matrix). The matrix describes the quark flavor-changing transitions in the standard model.

<div style="display: flex; justify-content: space-between; gap: 40px;">
  <img src="/blog/reyes/lagrangian.png" style="width: 80%;">
</div>

Vij matrix connects an up-type quark of the i-th generation to down-type quark of the j-th generation. 

<div style="display: flex; justify-content: space-between; gap: 40px;">
  <img src="/blog/reyes/vij.png" style="width: 100%;">
</div>

V_CKM matrix is unitary,
<div style="display: flex; justify-content: space-between; gap: 10px;">
  <img src="/blog/reyes/unitary.png" style="width: 100%;">
</div>

Unitarity violation can act as evidence for **Beyond Standard Model** (BSM) Physics. However, the Standard Model does not predict specific values for these elements—they must be determined experimentally. Of all the CKM parameters, |V_ub| is one of the least precisely known, and its accurate extraction helps in testing the consistency of the Standard Model.

## Why V_ub ?
The element V_ub connects an up-type quark to a bottom-type quark. It has the largest error amongst all the unitarity triangle parameters. 


<div style="display: flex; justify-content: space-between; gap: 40px;">
  <img src="/blog/reyes/vub2.png" style="width: 40%;">
</div>

## Where to look for it? 

<div style="display: flex; justify-content: space-between; gap: 40px;">
  <img src="/blog/reyes/image1.png" style="width: 100%;">
</div>

Here, we can see that the value of V_ub from BaBar and Belle experiments are not consistent with each other. This implies that the value is not conclusive. Hence, it seems that the best suited decay to study V_ub is instead semileptonic B meson decay B0→π-l+νl. 

# Methodology 

## Form factor models

1. **Model 1**: Single pole/ resonance <br>
The most simple parametrization is the single pole/resonance parametrization of the form factor which describes the production of B* meson. In the figure, we can observe the semi leptonic decay of B meson. Here, B* meson is an intermediate particle. When B meson decays into a pion, the intermediate B* meson decays into a W boson and a lepton pair.
<div style="display: flex; justify-content: space-between; gap: 20px;">
  <img src="/blog/reyes/model1.png" style="width: 70%;">
  <img src="/blog/reyes/vub3.png" style="width: 50%;">
</div>

Now for testing this model we extracted the value of **Vub= 4.62 x 10^(-3)** using BR equation by substituting the following inputs, 
<div style="display: flex; justify-content: space-between; gap: 20px;">
  <img src="/blog/reyes/model1_.png" style="width: 100%;">
</div>

However, if we go deeper we can analyze not only the BR but also consider the theoretical expression for decay distribution alongside the experimental data. The theoretical expression is given as,
<div style="display: flex; justify-content: space-between; gap: 20px;">
  <img src="/blog/reyes/image2.png" style="width: 100%;">
</div>
 where dB/dq2 represents decay distribution and q2 represents energy of lepton pair,

For analysis, we have used the decay distribution experimental data from Babar and Belle experiments. Then we have fitted the Model 1 with the extracted value of Vub to the experimental data.

<div style="display: flex; justify-content: space-between; gap: 20px;">
  <img src="/blog/reyes/plot1.png" style="width: 70%;">
</div>
We can observe that Model 1 does not fit the data points accurately. This implies that the single pole model is a poor description. This observation highlights the necessity of introducing a new model to better fit the data points to obtain a more optimal value of Vub.

2. **Model 2**: multi-pole model <br>
In order to improve the description we have proposed the multi-pole model.

<div style="display: flex; justify-content: space-between; gap: 20px;">
  <img src="/blog/reyes/model2.png" style="width: 70%;">
</div>
Here in the expression we have introduced 𝛼 which is an unknown parameter which gives the position of the second effective pole. 
<br><br>

Now, we have fitted the Model 2 to the data and extracted the value of 𝛼 and V_ub by using **χ² minimzation** method.
The χ² function to be minimized in our fit is defined as,
<div style="display: flex; justify-content: space-between; gap: 20px;">
  <img src="/blog/reyes/chi2.png" style="width: 100%;">
</div>

The extracted value of V_ub and 𝛼 are:

<div style="display: flex; justify-content: space-between; gap: 20px;">
  <img src="/blog/reyes/result.png" style="width: 50%;">
</div>

<div style="display: flex; justify-content: space-between; gap: 20px;">
  <img src="/blog/reyes/finalplot.png" style="width: 70%;">
</div>
The experimental data fits better with the dipole model. The χ² test was performed to quantify how well a model represents the experimental data. The null and alternative hypothesis were defined as,

* **H0**: The experimental data follows the expected behavior of the fitted model.
* **Ha**: The experimental data deviates from the expected behavior of the fitted model.

The obtained results are:
* **χ² value**: 10.57 , **Degrees of freedom**: 11	,  **P-value**: 0.48

Thus, the experimental data follows the expected behavior of the fitted model.

---
In the earlier analysis, the data points were assumed to be statistically independent. We now incorporate the correlations among the data points, which is essential for a more robust and realistic treatment of the uncertainties.

## Covariance Matrix

A Covariance Matrix is a type of matrix used to describe the covariance values between two items in a random vector. It is also known as the variance-covariance matrix because the variance of each element is represented along the matrix’s major diagonal and the covariance is represented among the non-diagonal elements.

It helps us to identify the direction of the relationship(positive or negative) between variables. Covariance matrix are also essential to understand the high- dimensional datasets.

The general form of the covariance matrix is given as:
<div style="display: flex; justify-content: space-between; gap: 20px;">
  <img src="/blog/reyes/cov3.png" style="width: 50%;">
</div>

Previously we were fitting the Model 2 to the data using the χ² function defined as:
<div style="display: flex; justify-content: space-between; gap: 20px;">
  <img src="/blog/reyes/cov1.png" style="width: 100%;">
</div>

Using the curve fitting method, we can extract the covariance matrix, where the square roots of the diagonal elements provide the uncertainties associated with |V_ub| and α.

> Optimal |V_ub| = 0.0036673564708459404 <br>
> Δ|V_ub| = 6.472941091232315e-05 <br>
> Optimal α = 0.5525955917130655 <br>
> Δα = 0.027348302682970248

> Covariance matrix: <br>
> [[ 4.18989664e-09 -1.42442466e-06] <br>
> [-1.42442466e-06  7.47929660e-04]] <br>


Now suppose that we have the **covariance matrix** for the experimental data points (dB/dq2), then our **χ² function** will be defined as,

<div style="display: flex; justify-content: space-between; gap: 20px;">
  <img src="/blog/reyes/cov4.png" style="width: 120%;">
</div>

<div style="display: flex; justify-content: space-between; gap: 20px;">
  <img src="/blog/reyes/covij.png" style="width: 100%;">
</div>

Now we can fit the Model 2 to the data using this χ² function to extract the values of V_ub and 𝛼.

> Optimal |V_ub|: 0.0036425765825239187 <br>
> Optimal α: 0.5517995594632777 <br>
> Minimum χ²: 0.10357435421646363 <br>

If we want to extract f_+(0) (normalization factor), and we have data from Lattice QCD simulations for form factor, then the χ² function will be defined as, 

<div style="display: flex; justify-content: space-between; gap: 20px;">
  <img src="/blog/reyes/cov2.png" style="width: 100%;">
</div>

<div style="display: flex; justify-content: space-between; gap: 20px;">
  <img src="/blog/reyes/covijlattice.png" style="width: 100%;">
</div>

The extracted values are:

> Minimum chi²   : 0.0009813578763637797 <br>
> Optimal f_plus0: 0.2916072589130864 <br>
> Optimal alpha  : 0.43369605256977545 <br>
> Delta f_plus0  : 0.015774043436603775 <br>
> Delta alpha    : 0.03757979960772628 <br>
> Covariance matrix of parameters: <br>
> [[ 0.00024882 -0.00056022] <br>
> [-0.00056022  0.00141224]] <br>

# Conclusion 

**Semileptonic B-meson decays** are an effective way to obtain accurate values for V_ub. The standard model only provides the structure of the transitions but does not predict specific values for parameters. The fitted model with the aforementioned values adequately represents the behavior of the experimental data gathered. 

However, the resulting values, though statistically meaningful, are not absolute and are subject to uncertainties arising from both experimental and theoretical inputs.

 <a href="https://drive.google.com/file/d/1b6wefz_heunm0p8oenY2CvoDSpTLSz_u/view?usp=sharing" target="_blank" rel="noopener" style="text-decoration: none;">
    <button style="width: 100%; padding: 14px 24px; font-size: 16px; background-color: #007acc; color: white; border: none; border-radius: 6px; cursor: pointer;">
      Project Report
    </button>
  </a>

</div>

<br><br>


View my <a href="https://github.com/anishak20/Hadronic-Physics" target="_blank" style="text-decoration: underline;">Github Repository</a> for the full details and implementation of the work.

