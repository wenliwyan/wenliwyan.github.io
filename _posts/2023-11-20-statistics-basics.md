---
layout: post
title: Statistics Basics
mathjax: true
---

Statistics is fundamental to data science. The necessity to learn or to revisit statistics basics often arises in the middle of meticulous practice. The following notes are collected from references listed in the end, and hope to serve as a convenient reference to refresh the knowledge on statistics basics when needed.

**Table of Contents**
* TOC
{:toc}

## Descriptive Statistics

Descriptive statistics are used to communicate information and to support reasoning about data. When exploring data of large size, it becomes essential to use **summaries**.

1. graphical summary: visualization

    The nature of the data and the goal of the visualization determine which method to choose (e.g. pie chat, dot plot, bar graph, histogram, box plot, scatter plot).

2. numerical summary: **mean** $\bar{x}$ and **standard deviation** $s$
    
    $s=\sqrt{\frac{1}{n}\sum_{i=1}^n(x_i-\bar{x})^2}$ or $\sqrt{\frac{1}{n-1}\sum_{i=1}^n(x_i-\bar{x})^2}$

    Both are sensitive to a few large or small data. If that is a concern, use **median** and the **interquartile range** (i.e. 3rd quartile - 1st quartile, measure of spread).

## Inferential Statistics

* population: the entire group of subjects about which we want information
* parameter: the quantity of interest about the population. e.g. the population average $\mu$, the population standard deviation $\sigma$.
* sample: the part of the population from which we collect information
* **statistic (estimate)**: the quantity of interest as measured in the sample. e.g. the sample average $\bar{x}$, the sample standard deviation $s$.

### Sampling

[x] sample of convenience: leading to **bias** (systematic error, such as selection bias, non-response bias, voluntary response bias)

[√] simple random sample, or stratified random sample

Since the sample is drawn at random, the estimate will be different from the parameter due to chance error (sampling error):

$\text{estimate}=\text{parameter}+\text{bias}+\text{chance error}$

* chance error will get smaller as the sample size gets bigger, and we can compute how large the chance error will be.
* bias will repeat on a larger scale when increasing the sample size, and typically we don't know how large the bias is.

### Probability

standard definition: the proportion of times an event occurs in many repetitions. *e.g. in 2015 there were about 4 million babies born in the US, and 48.8% of the newborns were girls.*

\* subjective probability is not based on experiments, and different people may assign different subjective probabilities to the same event. *e.g. the probability that my best friend calls today is 30%.*

Four basic rules:

* Complement rule: $P(A \text{ does not occur})=1-P(A)$
* Rule for equally likely outcomes: each face of a die has probability 1/6.
* Addition rule: If A and B are mutually exclusive, then $P(A\text{ or }B)=P(A)+P(B)$
* Multiplication rule: If A and B are independent, then $P(A\text{ and }B)=P(A)P(B)$

General multiplication rule: $P(A\text{ and }B)=P(A)P(B\mid A)$

**Bayes' rule**: $P(B\mid A)=\frac{P(A\mid B)P(B)}{P(A)}=\frac{P(A\mid B)P(B)}{P(A\mid B)P(B)+P(A\mid \text{not }B)P(\text{not }B)}$

case 1. *1% of the population has a certain disease. If an infected person is tested, then there is a 95% chance that the test is positive. If the person is not infected, then there is a 2% chance that the test gives an erroneous positive result (‘false positive’). Given that a person tests positive, what are the chances that he has the disease?*

$P(D\mid +)=\frac{P(+\mid D)P(D)}{P(+\mid D)P(D)+P(+\mid \text{no }D)P(\text{no }D)}=\frac{0.95\times0.01}{0.95\times0.01+0.02\times0.99}=32.4\%$

case 2. Warner's randomized response model to solve the problem that students may be too embarrassed to answer truthfully. *We do a survey that first instructs students to toss a coin twice. If the student gets
‘tails’ on the first toss, then the student has to answer question 1, otherwise the student answers question 2. Q1: Have you ever cheated on an exam in college? Q2: Did you get ‘tails’ on the second toss?*

#### Normal distribution

pdf (probability density function): $f(x)=\frac{1}{\sigma\sqrt{2\pi}}e^{-\frac{1}{2}(\frac{x-\mu}{\sigma})^2}$

**the empirical rule** (68-95-99.7 rule): the probability of the data falling within 1, 2, and 3 standard deviations of the mean are 68%, 95%, and 99.7% respectively.

**z-score (standardized value)**: $z=\frac{x-\bar{x}}{s}$ - no unit, follow the standard normal curve $\varphi(z)=\frac{1}{\sqrt{2\pi}}e^{-\frac{1}{2}z^2}$

**normal approximation**: finding areas under the normal curve. Area to the left of a given value - cdf (cumulative distribution function): $\Phi(z)=\frac{1}{\sqrt{2\pi}}\int_{-\infty}^ze^{-t^2/2}dt=\frac{1}{2}[1+\text{erf}(\frac{z}{\sqrt{2}})]$, in which *error function* $\text{erf}(x)=\frac{2}{\sqrt{\pi}}\int_0^xe^{-t^2}dt$, use software or a table to find its value.

#### Binomial distribution

Binomial setting: 1) Independent repetitions of an experiment. 2) Each experiment has two possible outcomes. 3) The **probability of success $p$** is the same in each experiment.


* binomial coefficient: counts the number of ways one can arrange $k$ successes in $n$ experiments, $\frac{n!}{k!(n-k)!}$.

* binomial probability: $P(k\text{ successes in }n\text{ experiments})=\frac{n!}{k!(n-k)!}p^k(1-p)^{n-k}$

* binomial distribution: "number of successes" is a *random variable* that follow binomial distribution.

For one experiment, the mean is $p$ (success is 1, and failure is 0), and the standard deviation is calculated to be $\sqrt{p(1-p)^2+(1-p)p^2}=\sqrt{p(1-p)}$.

Simple random sample is not the binomial setting, because $p$ changes after a subject has been selected and removed. But if the population is much larger than the sample, then sampling with replacement is about the same as sampling without replacement.

### Sampling distribution

Sampling distribution is a theoretical distribution that describes all possible values of a sample statistic from random samples of the same size, taken from the same population.

Sampling variability is the variability of the sample statistic values characterized by the sampling distribution.

**standard error (SE)**: tells roughly how far off the statistic will be from its expected value. It plays for the statistic the same **role that the standard deviation $\sigma$ plays for one observation drawn at random**.

* sample mean $\bar{x}_n$: $\mathbf{E}(\bar{x}_n)=\mu$, $\mathbf{SE}(\bar{x}_n)=\frac{\sigma}{\sqrt{n}}$ (**square root law**)

* sample sum $S_n$: $\mathbf{E}(S_n)=n\mu$, $\mathbf{SE}(S_n)=\sqrt{n}\sigma$

**law of large numbers**: the sample mean will likely be close to its expected value $\mu$ if the sample size is large.

**central limit theorem**: when sampling with replacement and $n$ is large (if there is no strong skewness then $n \ge 15$ is sufficient), then the sampling distribution of the sample mean/sum approximately follows the normal curve (*no matter what the population histogram is*). To standardize, subtract off the expected value of the statistic, then divide by its SE.

### Regression

We use regression to make a better prediction than the average, with additional information.

The relationship between two quantitative variables: direction (sloping up or down), form (linear or others), strength (how closely do the scatter points follow the form).

If the form is **linear**, a good measure of strength is **correlation coefficient r**:

$r=\frac{1}{n}\sum_{i=1}^{n}\frac{x_i-\bar{x}}{s_x}\times\frac{y_i-\bar{y}}{s_y}$

**method of least squares**: for $n$ pairs of data $(x_1, y_1),\dots,(x_n, y_n)$ that has linear relationship, the **regression line** is the line $\hat{y}_i=a+bx_i$ that minimizes the sum of the squared distances (*residual*) between the observed $y_i$ and the predicted $\hat{y}_i$, i.e. $$\sum_{i=1}^n(y_i-\hat{y}_i)^2$$. Solution: $b=r\frac{s_y}{s_x}$, $a=\bar{y}-b\bar{x}$.

R-squared: $R^2=r^2$, gives the fraction of the variation in the y-values that is explained by the regression line.

### Confidence intervals

Confidence interval is the estimation of an interval describing a plausible range of values for the unknown truth.

The SE tells the likely size of the chance error. Confidence intervals give a more precise statement.

95% **confidence interval**: By the central limit theorem and the empirical rule, there is a 95% chance that the sample statistic is no more than 2 SEs (more accurately 1.96) away from the population parameter. That is the same as saying that the population parameter is no more than 2 SEs away from the sample statistic.

$\bar{x}\pm z\text{SE}(\bar{x})$

  * 90% confidence level -> [estimate - 1.65 SE, estimate + 1.65 SE]
  * 95% confidence level -> [estimate - 1.96 SE, estimate + 1.96 SE]
  * 99% confidence level -> [estimate - 2.58 SE, estimate + 2.58 SE]

*Why "confidence" instead of "probability"?*
The population parameter is a fixed number, which either falls into the interval or not. There are no chances involved. Rather, the chances are in the sampling procedure, a different sample will give a slightly different interval. Inf one does many experiments, then 95% of these intervals trap the population percentage, and 5% will miss it.

**bootstrap principle**: we can estimate $\sigma$ by its sample version $s$ and still get an approximately correct confidence interval.

### Test of significance

Hypothesis testing proceeds by collecting data and evaluating whether the data are compatible with $H_0$ or not (in which case one rejects $H_0$).

* **null hypothesis $H_0$**: nothing extraordinary is going on
* **alternative hypothesis $H_A$**: there is a different chance process that generates the data.

**test statistic**: measures how far away the data are from what we would expect if $H_0$ were true.

* **z-statistic**: $z=\frac{\text{observed} - \text{expected}}{SE}$, in which SE is calculated from the population $\sigma$, and is often estimated by sample $s$. Extensions:

  * two-sample test: Compare two independent samples, $H_0: p_2-p_1=0, H_1: p_2-p_1\ne0$. Use z-test for the difference $\hat{p}_2-\hat{p}_1$: $z=\frac{(\hat{p}_2-\hat{p}_1)-0}{SE(\hat{p}_2-\hat{p}_1)}$, in which $SE(\hat{p}_2-\hat{p}_1)=\sqrt{(SE(\hat{p}_1))^2+(SE(\hat{p}_2))^2}$ due to the fact that $\hat{p}_1$ and $\hat{p}_2$ are independent.

  * paired test: Compare two samples that are not independent, e.g. given ages of husbands and wives, test whether husbands tend to be older than their wives.

  * sign test: e.g. test whether a coin is fair, test whether husbands tend to be older than their wives given if the husband was older or not in each couple.

* **chi-square statistic** (testing several categories): $\chi^2=\sum_{\text{all categories}}\frac{(\text{observed} - \text{expected})^2}{\text{expected}}$

* **ANOVA** (Analysis of Variance) - compare the variation between the groups to the variation within the groups: $$F=\frac{MST}{MSE}=\frac{SST/(k-1)}{SSE/(N-k)}=\frac{\sum_j(\bar{y}_j-\bar{\bar{y}})^2}{\sum_j\sum_i(y_{ij}-\bar{y}_j)^2}$$ (MST and MSE are treatment mean square and error mean square respectively, and SST and SSE are treatment sum of squares and error sum of squares respectively).

**p-value**: the probability of getting a value of test statistics *as extreme or more extreme* than the observed value, assuming $H_0$ is true. *The smaller the p-value, the stronger the evidence against $H_0$*. Often the criterion for rejecting $H_0$ is a p-value smaller than 5%, then the result is called **statistically significant**.

* the p-value of the z-statistic is the one tail or two tails of the normal distribution, depending on whether it is **one-sided** or **two-sided** test.

* for small sample size ($n \le 20$), the p-value needs to be computed from the t-distribution, because now the normal curve is not a good enough approximation to the distribution of the z-statistic, rather, an appropriate approximation is **Student's t-distribution with $n-1$ degrees of freedom**. The fatter tails account for the additional uncertainty introduced by estimating $\sigma$ by $s$.

* the p-value of the chi-square statistic is the right tail of the $\chi^2$ distribution with ? degrees of freedom

  * test of goodness-of-fit (test whether the categorical distribution  is the the same as given): degrees of freedom is $n-1$, in which n in the number of categories.

  * test of homogeneity (test whether the categorical distribution is the same for several populations): degrees of freedom is $(\text{number of categories} - 1) \times (\text{number of populations} - 1)$

  * test of independence (test whether two categorical variables are independent): the same as above

* the p-value of F in ANOVA is the right tail of the F-distribution with $k-1$ and $N-k$ degrees of freedom.

## Reference

Introduction to Statistics, Stanford University, Coursera

