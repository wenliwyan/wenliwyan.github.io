---
layout: post
title: Study Notes - Causal Inference for Statistics, Social, and Biomedical Sciences
mathjax: true
---

Book: Causal Inference

for Statistics, Social, and Biomedical Sciences

An Introduction

by Guido W. Imbens, Donald B. Rubin (2015)

**Focus: binary treatment**

## Preface

Causal inference is fundamentally a missing data problem. In all missing data problem, a key role is played by the mechanism that determines which data values are observed and which are missing. In causal inference, this mechanism is referred to as the assignment mechanism, the mechanism that determines levels of the treatment taken by the units studied.

## Part I: Introduction

Notion: causality is tied to an **action**, applied to a **unit**.
  - action is also called manipulation, treatment, or intervention. 
  The book primarily considers settings with two actions (binary treatment). Often one of these actions corresponds to a more active treatment in contrast to a more passive action. The first one is referred to as *active treatment* or **treatment**, and the second one as *control treatment* or **control**.
  - unit can be a physical object, an individual person, or collection of objects or persons, *at a particular point in time*.

Each action-unit pair is associated with a **potential outcome**.

**Definition of causal effect**: *comparison of potential outcomes*, for the same unit, at the same moment in time post-treatment.
**"The fundamental problem of causal inference"** (Holland, 1986, p. 947) is therefore the problem that at most one of the potential outcomes can be realized and thus observed.

Contrarily, for **estimation** and **inference**, we make different comparisons, i.e. *comparison of observed outcomes*. Because there is only one realized potential outcome per unit, we will need to consider multiple units. 
For example, a before-and-after comparison of the same physical object (involves distinct units) and the comparison of two different physical objects at the same time (involves distinct units).

In order to exploit the presence of multiple units, we use the stability assumption, **SUTVA** - The stable unit treatment value assumption (Rubin, 1980a): The potential outcomes for any unit do not vary with the treatments assigned to other units, and, for each unit, there are no different forms or versions of each each treatment level, which lead to different potential outcomes.
  - no-interference: in cases where no-interference is controversial, the adjustment is defining the unit to be the community within which individuals interact, for example, schools in educational settings, or specifically limiting the number of units assigned to a particular treatment.
  - no hidden variations of treatments: in cases where there is variation in the treatment, the adjustment is redefining the represented treatment levels to comprise a larger set of treatments, for example, aspirin+, aspirin-, and no-aspirin (there are two kinds of aspirin tablets of different strength) instead of only aspirin and no-aspirin.

The **assumptions** and restrictions are **not directly informed by observations, but rely on previously acquired knowledge of the subject matter for their justification**. For example, on the basis of a prior knowledge of medicine and physiology, someone else taking an aspirin in a different location cannot have an effect on my headache (no interference). Causal inference is generally impossible without such assumptions, and thus it is critical to be explicit about their content and their justifications.

Assuming SUTVA, one can display each unit's potential outcomes under each treatment. Specifically in binary treatment case, we have one realized potential outcome and one missing potential outcome for each unit.

\\[ Y_i^{obs} = Y_i(W_i) = \left\\{ \begin{align}Y_i(0) &\text{ if } W_i=0 \\\ Y_i(1) &\text{ if } W_i=1 \end{align} \right.\ \\]

\\[ Y_i^{mis} = Y_i(1 - W_i) = \left\\{ \begin{align}Y_i(1) &\text{ if } W_i=0 \\\ Y_i(0) &\text{ if } W_i=1 \end{align} \right. \\]

The information on *observed outcomes* alone still does not allow us to infer the causal effect. Suppose in the two-person headache example, the person who chose not to take the aspirin did so because he had only a minor headache. Suppose an hour later both headaches have faded: the headache for the first person possibly faded because of the aspirin, and the headache of the second person faded simply because it was not a serious headache. When comparing these two observed outcomes, we might conclude that the aspirin had no effect, whereas in fact it may have been the cause of easing the more serious headache. The key piece of information that we lack is the **assignment mechanism**: how each individual came to receive the treatment level actually received.

To estimate the causal effect for any particular unit, we will generally need to predict, or impute, the missing potential outcome. Comparing the imputed missing outcome to the realized and observed outcome for this unit allows us to estimate the unit-level causal effect. In general, creating such predictions is difficult. They involve assumptions about the assignment mechanism and about comparisons between different units, each exposed to only one of the treatments. Often the presence of unit-specific background attributes, also referred to as pre-treatment variables, or **covariates**, denoted by X_i for unit i, can assist in making these predictions.

The key characteristic of these covariates is that they are *a priori* known to be unaffected by the treatment. This knowledge often comes from the fact that they are permanent characteristics of units, or that they took on their values prior to the treatment being assigned (as reflected in the name "pre-treatment" variables).

The information available in these covariates can be used in three ways:
  * covariates commonly serve to make estimates more precise by explaining some of the variation in outcomes
  * causal effect of the treatment on subgroups as defined by a covariate in the population of interest
  * the effect on the assignment mechanism

**Causal estimands** are defined in terms of the potential outcomes, possibly also involving the treatment assignments and pre-treatment variables. A leading example is the average difference of the pair of potential outcomes **over the entire population**:

\\[ \tau_{fs} = \frac{1}{N}\sum_{i=1}^N (Y_i(1) - Y_i(0)) \\]
where "fs" indicates finite sample.

Generalizations:
1. average over **subpopulations** rather than over the full population.. The subpopulation may be defined in terms of different sets of variables:
  * subpopulation is defined in terms of $X_i$, e.g. $X_i = f$
  * subpopulation is those who were exposed to it. There is less interest in the average effect for units not exposed to the treatment.
  * subpopulation is defined partly in terms of potential outcomes. For example, to study the average effect of a job-training program on hourly wages, over those individuals who would have been employed irrespective of the level of the treatment, i.e. $i: Y_i(0) > 0, Y_i(1) > 0$.
2. more general functions of potential outcomes instead of average. e.g. $median(Y_i(1)) - median(Y_i(0))$, $median(Y_i(1) - Y_i(0))$

[TBC]