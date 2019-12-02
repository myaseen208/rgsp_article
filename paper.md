---
# Example from https://joss.readthedocs.io/en/latest/submitting.html
title: 'rgsp: An R Package for Quality Control Charts under Repetitive Group Sampling Plan based on $C_{pk}$'
tags:
  - Quality Control
  - R
authors:
  - name: Muhammad Yaseen
    orcid:  0000-0002-5923-1714
    affiliation: 1
  - name: Sami Ullah
    affiliation: "1, 3" 
  - name: Muhammad Kashif
    affiliation: 1
  - name: Muhammad Aslam
    affiliation: 2 
  - name: Muhammad Imran Khan
    affiliation: 1 
affiliations:
 - name: Department of Mathematics & Statistics University of Agriculture Faisalabad, Pakistan
   index: 1
 - name: Department of Statistics, King Abdulaziz University Jeddah, Saudi Arabia
   index: 2
 - name: College of Agriculutre, University of Sargodha, Pakistan
   index: 3
citation_author: Yaseen, M. et. al.
date: 31 October 2019
year: 2019
formatted_doi: 
bibliography: paper.bib
output: rticles::joss_article
csl: apa.csl
journal: JOSS
---

# Summary

The application of statistical quality control tools in industry are gaining an increasing importance in the quality conscious modern society. Many new methods are developed in recent years but not commonly used in industry because of their non-availability in different commercial statistical softwares. An R package for repetitive group sampling plan proposed by @Aslam2012 was developed and named as  ``rgsp``. The proposed sampling plan is based on process capability index $C_{pk}$, when the quality characteristic follows a normal distribution with unknown mean and variance. This paper presents methodology to calculate the minimum average sample number and average sample size in repetitive sampling for both symmetric and asymmetric cases by using ``rgsp`` package. The functions ``rgsp_asym1``, ``rgsp_asym2`` and ``rgsp_asym`` are used to estimate $P_1$, $P_2$, $n$, $k_a$, $k_r$  and ASN for both symmetric and asymmetric cases. 

# Introduction

Decision making becomes challenging both for producers and consumers when they have to decide about purchase from bulk of materials. Since the decision is made on the basis of samples from the lot, so there is an involvement of both producer’s risk and consumer’s risk. The producer’s risk is a probability of rejecting a good lot where as the probability of accepting a bad lot is the concern of consumer’s risk. To reduce both risks simultaneously, the accepting sampling plan plays very important role by satisfying the probabilities of important plan parameters such as the acceptance number and sample size on operating characteristic (OC) curve [@Aslam2012].  Acceptance sampling plan is equally good for both attributes and variables quality characteristics. However, the variable sampling plan is more costly and require smaller sample size as compared to attribute acceptance sampling plans [@Pearn2007; @Wu2008; @Montgomery2019]. Along with acceptance sampling plans, different process capability indices such as $C_{p}$ ,$C_{pk}$, $C_{pm}$ and $C_{pmk}$ are also used for monitoring different manufacturing processes [@Kashif2016; @Kashif2017]. Among four indices, the $C_{pk}$, index considers both the magnitude of process variance and process departure from the midpoint of specifications limits and is defined as:  

$$
C_{pk} = \textrm{min} \bigg(\frac{USL-\mu}{3\sigma},\frac{\mu-LSL}{3\sigma}\bigg)
$$

where $\mu$ is the process mean, $\sigma$ is the process standard deviation, USL and LSL are the upper and the lower specification limits respectively.

# The Method

@Aslam2012 used the process capability index $C_{pk}$  to optimize the acceptance sampling parameters in order to minimize the cost for process evaluation. OC function for parameter optimization under repetitive sampling based on $C_{pk}$  is defined as:

$$
L(p) = \frac{A} 
	{1 + A - B}
$$	

where 

$$
A = \phi \left( (z_{pu} - 3k_{a}) \sqrt{ \frac{n}{1+ \frac{9k_{a}^{2}}{2}}} \right) - \phi \left( -(z_{pl} - 3k_{a}) \sqrt{ \frac{n}{1+ \frac{9k_{a}^{2}}{2}}} \right)
$$

$$
B = \phi \left( (z_{pu} - 3k_{r}) \sqrt{ \frac{n}{1+ \frac{9k_{r}^{2}}{2}}} \right) - \phi \left( -(z_{pl} - 3k_{r}) \sqrt{ \frac{n}{1+ \frac{9k_{r}^{2}}{2}}} \right)
$$


Researchers have made attempts to improve the efficiency of the  $C_{pk}$  by reducing the sample size. @Balamurali2006 extended the work proposed by @Sherman1965 by improving the efficiency of the plan for the quality characteristic following the normal distribution. They also discussed the variables double-sampling plan and attribute repetitive group sampling plan.  @Aslam2012 discussed the process loss and presented a repetitive group sampling plan for variables based on $C_{pk}$  under symmetric and asymmetric conditions. They proposed the repetitive sampling plan limits as follows:

## Symmetric Case

$$
L(p_1) = \frac{2 \phi \left( (z_{\frac{p_1}{2}} - 3k_{a}) \sqrt{ \frac{n}{1+ \frac{9k_{a}^{2}}{2}}} \right)-1}{2 \phi \left( (z_{\frac{p_1}{2}} - 3k_{a}) \sqrt{ \frac{n}{1+ \frac{9k_{a}^{2}}{2}}} \right) - 2 \phi \left( (z_\frac{p_1}{2} - 3k_{r}) \sqrt{ \frac{n}{1+ \frac{9k_{r}^{2}}{2}}} \right) + 1} \geq 1-\alpha
$$

$$
L(p_2) = \frac{2 \phi \left( (z_\frac{p_2}{2} - 3k_{a}) \sqrt{ \frac{n}{1+ \frac{9k_{a}^{2}}{2}}} \right)-1}{2 \phi \left( (z_{\frac{p_2}{2}} - 3k_{a}) \sqrt{ \frac{n}{1+ \frac{9k_{a}^{2}}{2}}} \right) - 2 \phi \left( (z_\frac{p_2}{2} - 3k_{r}) \sqrt{ \frac{n}{1+ \frac{9k_{r}^{2}}{2}}} \right) + 1} \leq \beta
$$


## Assymetric Case

$$
L(p_1) = \frac{A_{1}} {1 +  A_{1} - B_{1}} \geq 1-\alpha
$$

$$
L(p_2) = \frac{A_{2}} {1 +  A_{2} - B_{2}} \leq \beta
$$

where

$$
A_{1} = \phi \left( (z_{3p_{1/4}} - 3k_{a}) \sqrt{ \frac{n}{1+ \frac{9k_{a}^{2}}{2}}} \right) - \phi \left( -(z_{p_{1/4}} - 3k_{a}) \sqrt{ \frac{n}{1+ \frac{9k_{a}^{2}}{2}}} \right)
$$


$$
B_{1} = \phi \left( (z_{3p_{1/4}} - 3k_{r}) \sqrt{ \frac{n}{1+ \frac{9k_{a}^{2}}{2}}} \right) - \phi \left( -(z_{p_{1/4}} - 3k_{r}) \sqrt{ \frac{n}{1+ \frac{9k_{a}^{2}}{2}}} \right)
$$



$$
A_{2} = \phi \left( (z_{3p_{2/4}} - 3k_{a}) \sqrt{ \frac{n}{1+ \frac{9k_{a}^{2}}{2}}} \right) - \phi \left( -(z_{p_{2/4}} - 3k_{a}) \sqrt{ \frac{n}{1+ \frac{9k_{a}^{2}}{2}}} \right)
$$


$$
B_{2} = \phi \left( (z_{3p_{2/4}} - 3k_{r}) \sqrt{ \frac{n}{1+ \frac{9k_{a}^{2}}{2}}} \right) - \phi \left( -(z_{p_{2/4}} - 3k_{r}) \sqrt{ \frac{n}{1+ \frac{9k_{a}^{2}}{2}}} \right)
$$


Minimizing conditions for $L(p_1)$ and $L(p_2)$ for both symmetric and asymmetric cases are given in @Aslam2012. Minimizing constraints  are used to compute Sample Number and Average Sample Number and sample size for Repetitive Group Sampling Plan based on $C_{pk}$.

# rgsp Functions

``rgsp`` is an R package containing functions to compute the above mentioned procedures for different sample size and different size of the shifts. The package contains following functions for the above mentioned methods



```r
rgsp_asym1(.p1, .p2, .alpha, .beta, .nums, .rep)
```


```r
rgsp_asym2(.p1, .p2, .alpha, .beta, .nums, .rep)
```


```r
rgsp_sym(.p1, .p2, .alpha, .beta, .nums, .rep)
```

Above given functions calculate $P_1$, $P_2$, $n$, $k_a$, $k_r$ and ASN for Repetitive Group Sampling Plan based on $C_{pk}$ under asymmetric case 1 and 2 and symmetric case given in @Aslam2012


# References
