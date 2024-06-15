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

**SUTVA** - The stable unit treatment value assumption (Rubin, 1980a): The potential outcomes for any unit do not vary with the treatments assigned to other units, and, for each unit, there are no different forms or versions of each each treatment level, which lead to different potential outcomes.
  - no-interference
  - no hidden variations of treatments

The assumptions and restrictions are not directly informed by observations, but rely on previously acquired knowledge of the subject matter for their justification. For example, on the basis of a prior knowledge of medicine and physiology, someone else taking an aspirin in a different location cannot have an effect on my headache (no interference). Causal inference is generally impossible without such assumptions, and thus it is critical to be explicit about their content and their justifications.

With SUTVA, for each unit, we have one realized potential outcome and one missing potential outcome (binary treatment case).

\\[ Y_i^{obs} = Y_i(W_i) = \left\\{ \begin{align}Y_i(0) &\text{ if } W_i=0 \\\ Y_i(1) &\text{ if } W_i=1 \end{align} \right.\ \\]

\\[ Y_i^{mis} = Y_i(1 - W_i) = \left\\{ \begin{align}Y_i(1) &\text{ if } W_i=0 \\\ Y_i(0) &\text{ if } W_i=1 \end{align} \right. \\]


The information on *observed outcomes* alone still does not allow us to infer the causal effect. Suppose in the two-person headache example, the person who chose not to take the aspirin did so because he had only a minor headache. Suppose an hour later both headaches have faded: the headache for the first person possibly faded because of the aspirin, and the headache of the second person faded simply because it was not a serious headache. When comparing these two observed outcomes, we might conclude that the aspirin had no effect, whereas in fact it may have been the cause of easing the more serious headache. The key piece of information that we lack is the **assignment mechanism**: how each individual came to receive the treatment level actually received.

[TBC]