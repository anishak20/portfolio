---
title: "Spectral lag in gamma-ray bursts"
description: "Estimating the spectral lag in gamma ray bursts to understand its emission mechanism"
dateString: April 2025 - Ongoing
draft: false
tags: ["Gamma-rays", "GRBs", "Statistical Analysis", "Python"]
showToc: false
weight: 203
cover:
    image: "projects/grbs/cover.png"
--- 
<!-- ### 🔗 [Colab Notebook](https://colab.research.google.com/drive/1Q553uslYW3Ho6P1G46SOEDxOS_VmHXfJ) -->

## Description

**Guide :** **Khushboo Sharma** (Ph.D. student at ARIES, Nainital, India)

This project was carried out as part of the ARIES Training School in Observational Astronomy and Atmospheric Sciences ([**ATSOAA**](https://www.aries.res.in/ATSOAA-2025)) held in Nainital, India. In this project, I constructed light curves of **GRB 240825A** from the FERMI GBM detector data and performed a cross-correlation analysis between two energy bands to estimate time delays between low and high-energy photon arrivals.

## What are Gamma-ray Bursts?

Gamma-ray bursts (GRBs) are among the most energetic transients in the universe. They can last from just a few milliseconds to several minutes and are observed at cosmological distances, with redshifts ranging from as low as 0.008 up to as high as 9.4. Their isotropic luminosities are exceptionally high — spanning from 10^47 to 10^54 erg/s. For comparison, the luminosity of the Sun is about 10^33 erg/s.

<div style="display: flex; justify-content: flex-start; gap: 10px;">
  <figure style="margin: 0;">
    <img src="/projects/grbs/grb.png" style="width: 100%;">
    <figcaption style="font-size: 0.9em; color: #555;">Credit: A Roquette/ESO/CC BY-SA</figcaption>
  </figure>
</div>

GRBs emit across a broad range of the electromagnetic spectrum, from radio waves to TeV gamma rays. There are two main types of GRBs: **long** and **short**.

* **Long-duration GRBs** are generally believed to originate from *collapsars* — the core collapse of a massive star at the end of its life.
* **Short-duration GRBs**, on the other hand, are thought to result from the merger of compact objects, such as two neutron stars or a neutron star and a black hole.

<div style="display: flex; justify-content: flex-start; gap: 10px;">
  <figure style="margin: 0;">
    <img src="/projects/grbs/grb1.png" style="width: 60%;">
  </figure>
</div>



## Prompt Emission and Afterglow: Two Powerful Phases of GRBs

GRBs are short-lived but extremely energetic events, typically lasting from a few seconds to a few days. They are generally divided into two distinct phases: the **prompt emission** and the **afterglow**.

### **Prompt Emission Phase**

The prompt emission is the initial phase of a GRB and lasts only a few seconds.

* It originates from **internal shocks** or **magnetic reconnection** occurring within the fast-moving jet launched by the central source.
* This phase takes place **within the ejected material**, before it has interacted with the surrounding environment.
* The emission is **dominated by gamma rays**, making it extremely bright and detectable even from cosmological distances.

### **Afterglow Phase**

The afterglow follows the prompt emission and can last for **hours to several days**.

* It is caused by **external shocks** that form when the jet interacts with the surrounding **interstellar medium (ISM)**.
* This phase occurs in the **shocked external environment**, where the jet loses energy to the medium.
* The emission spans a wide range of wavelengths, including **X-rays, optical, infrared, and radio**, and gradually fades over time.

<div style="display: flex; justify-content: flex-start; gap: 10px;">
  <figure style="margin: 0;">
    <img src="/projects/grbs/phase.png" style="width: 70%;">
  </figure>
</div>

## The Fermi Instrument

The **Fermi Gamma-ray Space Telescope** carries two main instruments:

* **Gamma-ray Burst Monitor (GBM)**: Covers 8 keV to 40 MeV energy range. It has **14 detectors**—12 NaI detectors (8 keV to 1 MeV) and 2 BGO detectors (200 keV to 40 MeV).
* **Large Area Telescope (LAT)**: Detects higher-energy photons in the range of 20 MeV to 300 GeV.

<div style="display: flex; justify-content: flex-start; gap: 10px;">
  <figure style="margin: 0;">
    <img src="/projects/grbs/fermi.png" style="width: 50%;">
  </figure>
</div>

These instruments records the arrival time and energy of individual photons emitted by distant GRBs. Although all photons travel at the speed of light, they are emitted at slightly different times due to the internal dynamics of the burst. This timing difference is what we refer to as spectral lag.

## What is Spectral Lag ?

**Spectral lag** refers to the time delay between the arrival of high-energy photons and low-energy photons during a Gamma-Ray Burst (GRB). It is one of the key temporal features observed in GRB light curves and is typically measured in **milliseconds**.

Spectral lag plays a significant role in:

* **Understanding emission mechanisms** involved in GRBs.
* **Estimating GRB redshifts indirectly**, especially when direct measurements are unavailable.

<div style="display: flex; justify-content: flex-start; gap: 10px;">
  <figure style="margin: 0;">
    <img src="/projects/grbs/lag1.png" style="width: 50%;">
  </figure>
</div>

### Interpretation of Spectral Lag
Spectral lag is observed in two primary forms, each providing insights into the emission mechanisms and internal dynamics of GRBs.

#### **Positive Spectral Lag**

* In a **positive lag**, high-energy photons are detected *earlier* than low-energy photons.
* This can be explained by **synchrotron cooling**, where high-energy photons are emitted first. As the electrons lose energy over time, they emit lower-energy photons, resulting in a delayed arrival of the latter.

#### **Negative Spectral Lag**

* In a **negative lag**, low-energy photons are detected *before* high-energy photons.
* This can be attributed to **inverse Compton up-scattering**, where soft (low-energy) photons are boosted to higher energies by interactions with hot electron clouds in the jet. These upscattered high-energy photons are emitted later, causing the observed delay.

<div style="display: flex; justify-content: flex-start; gap: 10px;">
  <figure style="margin: 0;">
    <img src="/projects/grbs/compton.png" style="width: 40%;">
  </figure>
</div>


## Methodology

### Data Source

**Instrument**: *Fermi Gamma-ray Space Telescope*

* **GBM (Gamma-ray Burst Monitor)**: 8 keV – 40 MeV

  * 12 NaI detectors (8 keV – 1 MeV)
  * 2 BGO detectors (200 keV – 40 MeV)
* **Data Format**: FITS (.fit, .pha, .rsp2)
* **Source**: Fermi GBM Burst Catalog (FERMIGBRST)
* **Download Method**: `wget` from GBM archive
* **Energy Channels**: 128, with mapping defined in `.rsp2` response file

> **Detector Selection**: NaI N7 was chosen as it recorded the brightest signal and had the smallest angle relative to the GRB source, resulting in maximum photon counts and better signal-to-noise.

### Light Curve Generation

* Generated light curves in 3 energy bands:

  * Low: 8–50 keV
  * Medium: 50–300 keV
  * High: 300–1000 keV

### Cross-Correlation Method

Cross-correlation estimates the time shift needed to best align the two light curves. It computes similarity as a function of time lag between the two curves, and the peak of the Cross-Correlation Function (CCF) gives the optimal lag value. It was implemented using `scipy.signal.correlate()` from SciPy library in Python.

<div style="display: flex; justify-content: flex-start; gap: 10px;">
  <figure style="margin: 0;">
    <img src="/projects/grbs/cc.gif" style="width: 80%;">
  </figure>
</div>


## Data Files

<table style="width: 100%; border-collapse: collapse; text-align: left;">
  <thead>
    <tr style="background-color: #f2f2f21f;">
      <th style="padding: 8px; border: 1px solid #ddd;">Data File</th>
      <th style="padding: 8px; border: 1px solid #ddd;">Description</th>
      <th style="padding: 8px; border: 1px solid #ddd;">Usage</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="padding: 8px; border: 1px solid #ddd;"><strong>.fit</strong><br><code>glg_tte_n7_bn240825662_v00.fit</code></td>
      <td style="padding: 8px; border: 1px solid #ddd;">Time-Tagged Event data from NaI detector N7</td>
      <td style="padding: 8px; border: 1px solid #ddd;">Extract photon arrival times and PHA channels</td>
    </tr>
    <tr>
      <td style="padding: 8px; border: 1px solid #ddd;"><strong>.pha</strong><br><code>glg_cspec_n7_bn240825662_v00.pha</code></td>
      <td style="padding: 8px; border: 1px solid #ddd;">Binned count spectrum with energy boundaries</td>
      <td style="padding: 8px; border: 1px solid #ddd;">Identify energy channels corresponding to 8–50 keV</td>
    </tr>
    <tr>
      <td style="padding: 8px; border: 1px solid #ddd;"><strong>.rsp2</strong><br><code>glg_cspec_n7_bn240825662_v04.rsp2</code></td>
      <td style="padding: 8px; border: 1px solid #ddd;">Instrument response matrix</td>
      <td style="padding: 8px; border: 1px solid #ddd;">Map channels to energy and filter 8–50 keV photons</td>
    </tr>
  </tbody>
</table>



## Results

### Light Curves

**GRB240825A** (T90 = 3.968 ± 0.091 s)
Energy bands:

* Low: 8–50 keV
* Medium: 50–300 keV
* High: 300–1000 keV

<div style="display: flex; justify-content: flex-start; gap: 10px;">
  <figure style="margin: 0;">
    <img src="/projects/grbs/lightcurve.png" style="width: 80%;">
  </figure>
</div>



### Estimated Spectral Lag (from CCF)

<div style="display: flex; justify-content: space-between; gap: 40px;">
  <img src="/projects/grbs/result1.png" style="width: 50%;">
  <img src="/projects/grbs/result2.png" style="width: 50%;">
</div>

<div style="display: flex; justify-content: space-between; gap: 40px;">
  <img src="/projects/grbs/result3.png" style="width: 50%;">
</div>

<br>

<table style="width: 100%; border-collapse: collapse; text-align: left;">
  <thead>
    <tr style="background-color:  #f2f2f21f;">
      <th style="padding: 8px; border: 1px solid #ddd;">Energy Bands (keV)</th>
      <th style="padding: 8px; border: 1px solid #ddd;">Spectral Lag</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="padding: 8px; border: 1px solid #ddd;">8–50 vs 50–300</td>
      <td style="padding: 8px; border: 1px solid #ddd;">–64 ms</td>
    </tr>
    <tr>
      <td style="padding: 8px; border: 1px solid #ddd;">50–300 vs 300–1000</td>
      <td style="padding: 8px; border: 1px solid #ddd;">–64 ms</td>
    </tr>
    <tr>
      <td style="padding: 8px; border: 1px solid #ddd;">8–50 vs 300–1000</td>
      <td style="padding: 8px; border: 1px solid #ddd;">–128 ms</td>
    </tr>
  </tbody>
</table>
<br>

### Error Estimation (Gaussian Fit)

<div style="display: flex; justify-content: space-between; gap: 40px;">
  <img src="/projects/grbs/result4.png" style="width: 60%;">
  <img src="/projects/grbs/result5.png" style="width: 60%;">
</div>

<br>

<table style="width: 100%; border-collapse: collapse; text-align: left;">
  <thead>
    <tr style="background-color: #f2f2f21f;">
      <th style="padding: 8px; border: 1px solid #ddd;">Energy Bands (keV)</th>
      <th style="padding: 8px; border: 1px solid #ddd;">Spectral Lag (Peak CCF)</th>
      <th style="padding: 8px; border: 1px solid #ddd;">Spectral Lag (Gaussian Fit)</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="padding: 8px; border: 1px solid #ddd;">8–50 vs 50–300</td>
      <td style="padding: 8px; border: 1px solid #ddd;">–64 ms</td>
      <td style="padding: 8px; border: 1px solid #ddd;">–299 ± 8 ms</td>
    </tr>
    <tr>
      <td style="padding: 8px; border: 1px solid #ddd;">8–50 vs 300–1000</td>
      <td style="padding: 8px; border: 1px solid #ddd;">–128 ms</td>
      <td style="padding: 8px; border: 1px solid #ddd;">–334 ± 9 ms</td>
    </tr>
  </tbody>
</table>


## Discussion
A **negative spectral lag** was observed for **GRB 240825A**. Negative spectral lag in GRBs, though rare, can arise from inverse Compton up-scattering of soft photons by a surrounding hot electron medium. A notable difference exists between the spectral lag values obtained from the peak of the CCF and from Gaussian fitting. This discrepancy suggests that the CCF may follow an **Asymmetric Gaussian** profile rather than a **Gaussian** one. 

To address this, I’m currently fitting an asymmetric gaussian to the CCF, which may provide a more accurate estimate of the spectral lag. In addition, I am also investigating the lag–luminosity relation. Further improvements and analysis are ongoing to refine the results.