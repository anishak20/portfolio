---
title: "Local galaxies as time machines: Navigating biases in studying Cosmic Evolution"
description: "Using galaxies as probes to investigate the observational biases that affect the estimation of physical parameters (e.g., stellar masses) in galaxies."

dateString: July 2023
math: true
draft: false
tags: ["galaxies", "galaxy evolution", "Python", "Astropy", "Data Analysis"]
weight: 102
cover:
    image: "/blog/iastro/cover.png"
    # caption: "A sample landmark detection on a photo by Ayo Ogunseinde taken from Unsplash"
---

# Introduction

**Supervisor:** **Ana S. Paulino Afonso** (Researcher, Instituto de Astrofísica e Ciências do Espaço, Portugal) 

 This project was undertaken as part of a summer research internship at <a href="https://www.iastro.pt/" target="_blank" style="text-decoration: none;"> the Instituto de Astrofísica e Ciências do Espaço (**IAstro**)
</a>, Portugal. During this internship, I have simulated and applied the transformation effects: **Cosmological dimming**, **scaling** and modelling of **luminosity evolution** to the host galaxy **SN2005hc** at three different values of redshift using the artificial redshifting algorithm (**FERENGI**). 
<br>
<br>
The main project aim was to investigate the observational biases that influence the estimation of physical parameters such as Star Formation Rate, Stellar Mass in galaxies.

# Why do we need to examine the biases?

The motivation behind this project stems from the fact that galaxies tend to appear increasingly **irregular** at higher redshifts. However, to make meaningful comparisons between galaxy populations across different cosmic epochs, it's essential to account for various **observational** limitations. These include selection and instrumental biases as well as cosmological effects. For example, the surface brightness dimming effect impacts the flux of the galaxy by two orders of magnitude from z=0 to z=2. This strongly effects the galaxy morphological studies.

<figure>
  <img src="/blog/iastro/image_.png" alt="Hubble Ultra Deep Field" style="width:100%;">
  <figcaption style="font-size: 0.9em; text-align: center;">
    Nearly 10,000 galaxies captured in the Hubble Ultra Deep Field, revealing 13 billion years of cosmic history.  
    <br>
    <a href="https://science.nasa.gov/universe/galaxies/evolution/" target="_blank" rel="noopener">Credits: NASA, ESA, STScI & HUDF Team</a>
  </figcaption>
</figure>

# Data Source

The data used is acquired from the **amusing survey** which focuses on the galaxies hosting type 1a supernovae. Instrument used is MUSE on the VLT. The target for our study is SN2005hc host galaxy. The data here is in the form of **FITS** file which consists of 3d data cube containing both spatial and spectral information.

<div style="display: flex; justify-content: space-between; gap: 40px;">
  <img src="/blog/iastro/image1.png" style="width: 50%;">
  <img src="/blog/iastro/image2.png" style="width: 60%;">
</div>

# Methodology

The artificial redshifting algorithm implemented follows the **FERENGI** approach to simulate how nearby galaxies would appear at higher redshifts as described in the paper by
<a href="https://arxiv.org/abs/2202.04078" target="_blank" style="text-decoration: none;">A. Paulino-Afonso et al., 2022</a>:

### Step 1: Redshift Selection

Selected target redshifts: **z = 0.3**, **0.8**, and **1.3**

### Step 2: Transformations Applied

Three major transformations were performed:

1. **Cosmological Dimming** <br>
   Applied a flux dimming factor proportional to:
   <div style="display: flex; justify-content: flex-start; gap: 10px; margin-top: 8px; margin-bottom: 16px;">
     <img src="/blog/iastro/flux.png" style="width: 60%;">
   </div>

2. **Spatial Scaling** <br>
   Used the **FREBIN 2D** algorithm to resample each 2D wavelength slice, scaling to match the pixel scale at higher redshift. This preserves both:

   * **Physical size** (via angular diameter distance)  
   * **Total flux** (via luminosity distance)

3. **Luminosity Evolution** <br>
   Applied an evolution factor to account for the average evolution in brightness across different redshifts. This effect also accounts for the reduced observed flux due to increasing distance and redshift as outlined by <a href="https://arxiv.org/pdf/1611.05039" target="_blank" style="text-decoration: none;">A. Paulino-Afonso et al., 2016</a>.

   <div style="display: flex; justify-content: center; margin-top: 12px;">
     <img src="/blog/iastro/lum2.png" style="width: 50%; max-width: 500px;">
   </div>


# Results

<br>
<br>
<!-- Flex container for the two columns -->
<div style="display: flex; flex-wrap: wrap; gap: 90px; justify-content: center;">

  <!-- Left column -->
  <div style="flex: 1; min-width: 300px; text-align: center;">
    <img src="/blog/iastro/image1.png" 
         style="width: 70%; max-width: 400px; display: block; margin: 0 auto 60px;">
    
<img src="/blog/iastro/image5.png" 
         style="width: 120%; max-width: 500px;">
  </div>

  <!-- Right column -->
  <div style="flex: 2; min-width: 200px; text-align: center;">
    <img src="/blog/iastro/cover.png" 
         style="width: 155%; max-width: 900px;">
  </div>

</div>
<br>



<p style="font-size: 1em; margin-top: 4px; width: 130%; text-align: justify;">
The above images illustrate how galaxy appearance changes with increasing redshift. As redshift increases, in the <strong>cosmological dimming effect</strong> we observe a reduction in flux, especially in the outer regions of galaxies. While the <strong>scaling effect</strong> shows no apparent flux loss, the intrinsic <strong>luminosity evolution</strong> shows the change in intrinsic brightness of galaxies. Combining these effects, the images show galaxies appearing smaller and dimmer at higher redshifts, with noticeable flux loss from their outskirts.
</p>

<br>
<!-- Flex container for the two columns -->
<div style="display: flex; flex-wrap: wrap; gap: 60px; justify-content: center;">

  <!-- Left column -->
  <div style="flex: 1; min-width: 300px; text-align: center;">
    <img src="/blog/iastro/image2.png" 
         style="width: 70%; max-width: 400px; display: block; margin: 0 auto 40px;">
    
<img src="/blog/iastro/image6.png" 
         style="width: 110%; max-width: 500px;">
  </div>

  <!-- Right column -->
  <div style="flex: 2; min-width: 200px; text-align: center;">
    <img src="/blog/iastro/image3.png" 
         style="width: 210%; max-width: 900px;">
  </div>

</div>

<br>


<p style="font-size: 1em; margin-top: 4px; width: 130%; text-align: justify;">
  Comparing with the spectral graph at z = 0, we observe that from z = 0.3 to z = 1.3, the <strong>dimming effect</strong> reduces the observed flux by approximately two orders of magnitude. However, under the <strong>scaling effect</strong>, the flux appears to be preserved across different redshifts at longer wavelengths. This suggests that as we move to higher redshift values, the flux of galaxies can be recovered to its intrinsic value. In the case of <strong>luminosity evolution</strong>, flux increases with redshift due to changes in the intrinsic brightness of galaxies. When <strong>combined</strong>, these effects result in a slight increase in observed flux, explained by the overlap between luminosity evolution and cosmological dimming.
</p>




<br>


View my [Jupyter Notebook](https://github.com/asofiafonso/local-galaxies2023/blob/main/IASTRO-%20Combined%20Effects.ipynb) for the full implementation of the work.
