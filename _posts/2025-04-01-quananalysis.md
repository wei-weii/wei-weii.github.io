---
title: Quantitative Data Analysis
author: wei
date: 2025-04-01 15:48:00 -0700
categories: [Blogging]
tags: [research]
render_with_liquid: true
math: true
toc: true
pin: false
---

## Traditional Statistics (More details can be found in [Koji Yatani's webpage](https://yatani.jp/teaching/doku.php?id=hcistats:start))
### ANOVA
ANOVA (ANalysis Of VAriances) is **a family of  statistical methods used to compare the means of two or more groups by analyzing variance**. In a nutshell, it compares the variance within each group to the variance between the group means. If between-group variance is *substantially* larger than within-group variance, then the null hypothesis can be rejected, and we claim that the group means are likely different. ANOVA is suitable when the following assumptions are met:
- Normality: The distribution of the populations you take samples from are normal;
- Homogeneity of Variances: The variance in each group should be similar enough;
- Data: The dependent variable must be continuous. 



### Some Key Concepts
- **Null Hypothesis**: There are no differences between the group means (i.e., all group means are equal)

- **Highest Density Interval (HDI)**: HDI indicates which points of a distribution are most credible, and which cover most of the distribution. HDI summarizes the distribution by specifying an interval that spans most of the distribution, say 95% of it, such that every point inside the interval has higher credibility than any point outside the interval.


### Some Common Statistic Distributions
- **Bernoulli distribution**: Bernoulli distribution describes the probability of a single yes-no question.
- **Binomial distribution**:Binomial distribution describes the number of successes in a sequence of *n* independent experiments, each asking a yes-no question with probability *p*.
- **Logistic distribution**:The cumulative distribution function of logistic distribution is the logistic function.

## Bayesian Statistics
### Theory

Recall that conditional probability is:

$$ 
\begin{equation}
    p(a \mid b) = p(a,b)/p(b) 
    \label{eq:condiP}
\end{equation}
$$

Similarly $$\begin{equation}
    p(b \mid a) = p(a,b)/p(a) 
\end{equation} $$, we can then infer Bayesian Theorem easily :

$$ 
\begin{equation}
    p(a \mid b) = p(b \mid a)p(a)/p(b)
    \label{eq:bayesiT}
\end{equation}
$$

Let's say we want to estimate a parameter's value (more formally, the probability distribution of the parameter), say $\theta$, based on the data (D) we collected. We can then write the equation above as:

$$ 
\begin{equation}
    p(\theta \mid D) = p(D \mid \theta)p(\theta)/p(D)
    \label{eq:bayesiTheta}
\end{equation}
$$

Phrased in plain language, the equation above tells us how much we believe parameter values ( $\theta$ ) given the data (D) can be calculated with the three parts: 
- i. the likelihood that the data values are sampled given the parameter values--- $$ p(D \mid \theta) $$ ; 
- ii. the probability of parameter values--- $$ p(\theta) $$ , 
- iii. the probability of data values--- $$ p(D) $$ .

Furthermore, the denominator p(D) can be calculated with: 

$$ 
\begin{equation}
    p( D) = \sum_{ \theta^*} p(D \mid \theta^*)p(\theta^*)
\end{equation}
$$

In the jargons of Bayesian data analysis, i. is called *likelihood*, ii. *prior*, iii. *evidence*, and  $$ p(\theta \mid D) $$ is called *posterior*.

At the core of all the mess above is a simple idea: we have some info of the value(s) of  $\theta$ (either from previous research, existing knowledge, or simply guesses). To gain more confidence in the value(s), we collect additional data (D). And based on D, we can improve our guesses about $\theta$, which is $$ p(\theta \mid D) $$ 


### Practice (with jags, MCMC, and R. The content is based on [*Doing Bayesian Data Analysis*](https://www.oreilly.com/library/view/doing-bayesian-data/9780124058880/) by John Kruscheke) 
And [Bayesian analysis reporting guidelines]( https://jkkweb.sitehost.iu.edu/BARG.html) details how to report Bayesian stats for research papers.

Some notes from the book:
- MCMC: An approach that samples a large number of representative values from a distribution
- How to read MCMC diagnostics
1. Details of trace plot, shrink factor, density plots, can be found in p. 180-183, Chapter 7.5

