---
title: Bayesian Data Analysis
author: wei
date: 2025-04-01 15:48:00 -0700
categories: [Blogging]
tags: [research]
render_with_liquid: true
toc: false
pin: false
---


# Statistics Concepts
## ANOVA
ANOVA is **a family of  statistical methods used to compare the means of two or more groups by analyzing variance**. In a nutshell, it compares the variance within each group to the variance between the group means. If between-group variance is *substantially* larger than within-group variance, then the null hypothesis can be rejected, and we claim that the group means are likely different. 

- The null hypothesis: there are no differences between the group means (i.e., all group means are equal)
## Bayesian Data Analysis

# Bayesian
## Theory

Known that conditional probability is:
> p(a|b) = p(a,b)/p(b) --- (1)

We can infer Bayesian Theorem easily from (1):
> p(a|b) = p(b|a)p(a)/p(b) --- (2)

Within Bayesian data analysis, we want to estimate parameter values, say $\theta$, based on the data - D - we collected. We can then write (2) as:
> p($\theta$|D) = p(D|$\theta$)p($\theta$)/p(D) --- (3)

Phrased in plain language, (3) tells us how much we believe parameter values ($\theta$) given the data values (D) can be calculated when we know: 
- i. the likelihood that the data values are sampled given the parameter values(p(D|$\theta$)); 
- ii. the probability of parameter values (p($\theta$)), 
- iii. the probability of data values (p(D)).

In the jargons of Bayesian data analysis, i. is called *likelihood*, ii. *prior*, iii. *evidence*. And  p($\theta$|D) is called *posterior*.

At the core of all the mess above is a simple idea: We have some info of the value(s) of $\theta$ (whether from previous research, existing knowledge, or simply guesses). To gain more confidence in this value, we collect additional data (D). And based on D, we can improve our guesses about $\theta$.

## Practice (with jags, MCMC, and r. The content is based on [*Doing Bayesian Dat Analysis*](https://www.oreilly.com/library/view/doing-bayesian-data/9780124058880/) by John Kruscheke) 


[Bayesian analysis reporting guidelines]( https://jkkweb.sitehost.iu.edu/BARG.html)
## How to read MCMC diagnostics
1. Details of trace plot, shrink factor, density plots, can be found in p. 180-183, Chapter 7.5

