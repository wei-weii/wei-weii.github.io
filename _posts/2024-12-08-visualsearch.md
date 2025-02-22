---
title: Notes on Visual Search
date: 2024-12-08 21:19:00 -0700
categories: [Blogging]
tags: [research, psychology]
author: wei
render_with_liquid: true
toc: false
pin: true
---

## What is visual search?
Looking for a specfic item in a visual scene (page 105, [*active vision The Psychology of Looking and Seeing*](https://doi.org/10.1093/acprof:oso/9780198524793.001.0001)). 

(...) an observer looks for one or more targets in a display containing some distractor items (page 11, [*Oxford Handbook of Attention*](https://doi.org/10.1093/oxfordhb/9780199675111.013.002)).

## Why is visual search (important)?
Humans are incapable to process all the visual information of a visual stimulus at the same time (page 27, [*The Handbook of Attention*](https://doi.org/10.7551/mitpress/10033.003.0004)). In most cases, we want to extract the gist or the most interesting parts in a snap, i.e., find the 'target' as fast as possible. 

Psychologically speaking, by studying visual search, psychologists are interested in:

    1. what characteristics of a stimulus facilitate fast search (AKA, parallel search),
    2. what is the role of attention in this process (preattentive vs. attentive),
    3. what is the neural basis of search visual search.

Personally speaking, from the perspective of my research interest - visualization design, how to design visualization, so it conveys the main points in an efficient and effective way, relies on a comprehensive understanding of humans' vision system. A better understanding of visul search will provide more solid guidelines for visualization design.     


## How is visual search (studied)?
### Employed tasks (see [paper](https://doi.org/10.1037/a0012780))
- Detection. Signal the presence or absence of a target
- Localization. Report the location of a target
- Identification. Report the type of a target, normally there are two types of targets


### A few related terms**

![Figure 1. Feature search (left) vs. Conjunction search (right). ](https://wei-weii.github.io/assets/img/postImgs/featuresearch.png) 
<div style="text-align:center;">
<p style="font-style:italic;">Figure 1. Feature search (left) vs. Conjunction search (right). Credit: <a  href= https://doi.org/10.7551/mitpress/10033.003.0004> The Handbook of Attention</a>, page 32.</p>
</div>

- <span style="color:#FF7043">Set size</span>. The number of items in the display.
- <span style="color:#FF7043">Preattentive stage (process)</span>.  Neisser introduced the idea of preattentive stage, in which processing "must be genuinely 'global' and 'wholistic'". (page 85, [Cognitive Psychology](https://doi.org/10.4324/9781315736174)) 
- <span style="color:#FF7043">Attentive stage (process)</span>. As opposed to preattentive stage, the process that requires the deployment of attention.
- <span style="color:#FF7043">Feature search</span>. Visual search in which target is defined by a *feature* (one of the features that Treisman et al. claim are processed in parallel).
- <span style="color:#FF7043">Conjunction search</span>. As opposed to feature search, conjuction search is visual search in which target is defined by the conjunction of two features (page 14, [Oxford Handbook of Attention](https://doi.org/10.1093/oxfordhb/9780199675111.013.002)). Figure 1 shows the example of feature search and conjunction search.
- <span style="color:#FF7043">Parallel search</span>. Search that proceeded multiple items together.
- <span style="color:#FF7043">Serial search</span>. Search that proceeded one item after another until the target is discovered. (page 13, [Oxford Handbook of Attention](https://doi.org/10.1093/oxfordhb/9780199675111.013.002)) 
- <span style="color:#FF7043">Covert attention</span>. "used to describe attending without looking, often colloquially termed looking out of the corner of the eye"
- <span style="color:#FF7043">Overt attention</span>. "the term we will use to describe attending by means of looking". The definition of covert attention and overt attention are from [*active vision The Psychology of Looking and Seeing*](https://doi.org/10.1093/acprof:oso/9780198524793.001.0001), page 3.
- <span style="color:#FF7043">Homogeneous / heterogeneous search</span>. Whether the distractors are identical to each other (Homogeneous) or not (heterogeneous).
- <span style="color:#FF7043">Bottom-up / Top-down guidence</span>.


### Two theories

**"While Feature Intergration Theory saw two types of search—parallel and serial—Guided search saw two ends of a continuum of guidance"** (page 20, [Oxford Handbook of Attention](https://doi.org/10.1093/oxfordhb/9780199675111.013.002)) 

- <span style="color:#9c755f">FIT (Feature Integration Theory)</span>. FIT is the most influential theory that tries to model visual search. Proposed by [Anne Treisman] (https://doi.org/10.1037/0033-295X.95.1.15), _FIT claims that a set of *features* are processed (more specifically, registered to a feature map) "early, automatically and in parallel across the visual field". This is then followed by a "binding" stage that "glues" features together into specific perceptual objects, which requires focused attention and is processed serially and is self-terminating_. Identified *features* include color, size, orientation, motion, curvature. (page 29, [*The Handbook of Attention*](https://doi.org/10.7551/mitpress/10033.003.0004)), which Treisman argued that could be processed 'preattentively', in parallel. A detailed and comprehensive summary of _features_ can be found in the Chapter 2 of the [Oxford Handbook of Attention](https://doi.org/10.1093/oxfordhb/9780199675111.001.0001).   Thus a visual search task will be accomplished in a fast way if the target-distractors difference is defined by a *feature* (feature search). Otherwise (conjunction search), the search will be serial and slow.  


- <span style="color:#9c755f">Guided Search</span>. Guided search is proposed by [Wolfe et al.](https://doi.org/10.1037/0096-1523.15.3.419) The original version of guided search borrows the two-steps logic of FIT theory. The key idea of guided search is that "preattentive feature information could be used to 'guide' the serial deployment of attention". _The main difference between guided search an FIT is "FIT proposed a dichotomy between parallel and serial search tasks, GS proposed a continuum based on the effectiveness of guidance_."(see [paper](https://doi.org/10.3758/s13423-020-01859-9)). Wolfe and his colleagues continue to refine the guided search theory, primarily by updating the sources of guidance. The newest one is [Guided Search 6.0](https://doi.org/10.3758/s13423-020-01859-9), published in 2021. Nonetheless, preattentive features remain as the number one form of guidence.












