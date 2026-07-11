---
title: Solutions of some issues of QUEST staircase in Psychopy for online studies
author: wei
date: 2026-06-18 12:13:00 +0200
categories: [Blogging, Research]
tags: [research]
render_with_liquid: true
toc: true
pin: true
---


## Notes about this post
This post is **only about online interleaved QUEST staircases** design that is based on psychojs. That is to say, this post doesn't apply to simple or QUEST Plus staircases, nor for local experiments that is based on psychopy (python). But, as we will see, some of the confusion originates from how QUEST is implementated in python.

The PsychoPy version I used: v2025.2.3

## Overview of QUEST implementation in psychojs
It is based on the jsQUEST project created by Daiichiro Kuroki, [official page](https://kurokida.github.io/jsQUEST/) and [github](https://github.com/kurokida/jsQUEST).

Psychopy provides instructions on how to set up staircase studies [here](https://psychopy.org/builder/flow.html) (henceforth referred as '*Instruction*'). However, I find some parts of the page are misleading or even incorrect, and some other important information is missing, especially for online studies. Here I want to clarify confusion and provide extra needed info so other people can save some time for their experiment design.

An interleaved staircase design is handled by the 'MultiStairHandler' class ([source code](https://psychopy.github.io/psychojs/data_MultiStairHandler.js.html)), while a single QUEST staircase design is handled by the 'QuestHandler' class ([source code](https://psychopy.github.io/psychojs/data_QuestHandler.js.html)). Since I will also mention the implementation of them in python. Henceforth I use 'js_MultiStairHandler', 'js_QuestHandler' to refer to javascript code implemented in psychojs, while 'py_MultiStairHandler' and 'py_QuestHandler' refer to their counterpart python code in psychopy([source code](https://psychopy.org/api/data.html#psychopy.data.QuestHandler)).

## Issues

Currently, there are following three problems in *the Instruction*:

1. How to correctly terminate a staricase by setting a max number of trials? 
    > Solution
    {: .prompt-tip }    
    **Don't use the *nReps* that Psychopy Builder provides, it won't work. There are two solutions:** i) pass *maxTrials* as an additional parameter to the 'nReps' field in the stair handler, as suggested by [this post](https://discourse.psychopy.org/t/quest-loop-not-terminating-online/43135). However, this method will set the same max number of trials to all your staircases if you have multiple staircases interleaved. ii) add one more column of *maxTrials* to your condition file, as shown below (the right most column ):
    ![The example condition file for interleaved QUEST staircases design](https://wei-weii.github.io/assets/img/postImgs/questCondition.png)

    This method enables you to set different max trial numbers to different staircases that are interleaved together, if needed. However, setting  individual *maxTrials* in this way will cause the loop (i.e., the loop that you interleave staircases) doesn't know when to stop. I add the following lines of code in the loop to help terminate the loop:

    ```
    let finishcount = 0

    for (let stair of currentLoop._staircases) {
        if (stair.finished){   
            finishcount++;
        }
    }
    // trials is the name of the loop
    trials.finished = finishcount===currentLoop._staircases.length;
    ```

    > Explannation
    {: .prompt-info }

    The description of *nReps* in the *Instruction* is misleading and does not work as it claims. In the source code of js_MultiStairHandler and js_QuestHandler, *nReps* is actually used as '*nTrials*.' And the actual *'nReps'* value used in the source code is always the default value: 1. So when you set value for 'nReps' through builder, you are actually providing value for *nTrials*.  My guess is that it aims to act as the parameter with the same name in py_QuestHandler. In py_QuestHandler, '*nTrials*' is described as:
   
    > The **maximum** number of trials to be conducted.

    However, in *Instruction*, it is described as:

    >The **minimum** number of trials to be conducted.
    
    which is contradictory. But this contradiction does not matter at all, because *nTrials* is actually not used in js_QuestHandler when the epxeriment intantiates a QUEST staircase, which means no matter what value you give for *nReps*, it has **NO EFFECT** on how many trials the staircase will run. As [people have found](https://discourse.psychopy.org/t/ending-a-staircase-after-a-maximum-number-of-trials/35276), the **actual maximum** of trials is controlled by variable *maxTrials*. Therefore, if you need to control the number of trials of your staircase, you need to use *maxTrials*, not *nReps* or *nTrials*. 


2. How to set the min and max value for your staircase level? 
    > Solution
    {: .prompt-tip }
    
    Short answer: there is no way to set a min or max value to the Quest algorithm. Nor the *minVal*, *maxVal*, or *range* mentioned in *Instruction* works. However, you can achieve it with with the this line of code: level = Math.max(Math.min(maxVal,level),minVal);

    > Explannation
    {: .prompt-info }

    As Daiichiro Kuroki and Denis Pelli explained in their code, Quest only provides a suggesting value based on priors and the new data it is given. It doesn't take other info, e.g., min or max constraints. You can, of course, set the prior sd to a very small value, e.g., 0.001, to constrain the suggesting value always close to the prior mean (i.e., starVal). But doing so basically invalidates the whole meaning of Quest staircase. 
    
    However, in practice, we do need constrain the value sometimes. For example, we want to make sure the value is larger than 0 when we use Quest to ascertain the minimum time of a task. In this case, what we can do is updating the variable '*level*' based on our constraints. For example, if we want to make sure '*level*' is between minVal and maxVal, we should have the following code:

    ```
    level = Math.max(Math.min(maxVal,level),minVal);
    ```

    The Quest will update next suggesting value based on the previous level (and priors). With the code above, we make sure the level is within the constrain and infor Quest what is the actual value we test. 


3. How to terminate a QUEST staircase based on a certain confidence internval?
    > Solution
    {: .prompt-tip }

    You can use *stopInterval* to terminate your staircase. Just add it to your condition file. As shown in the screenshot above.