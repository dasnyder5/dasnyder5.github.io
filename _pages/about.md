---
layout: about
title: About
permalink: /
subtitle: Generalization and Safety in Robotics at <a href='https://www.upenn.edu/'>University of Pennsylvania</a>.

profile:
  align: right
  image: profile.jpg
  image_circular: true # crops the image to make it circular
  address: >
    <p>Department of <a href='https://www.upenn.edu/'>Electrical and Systems Engineering</a>.</p>
    <p>Philadelphia, PA 19104</p>
# <p>555 your office number</p>
# <p>123 your address street</p>
# <p>Your City, State 12345</p>
news: true  # includes a list of news items
selected_papers: true # includes a list of papers marked as "selected={true}"
talks: true # includes a list of talks
social: true  # includes social icons at the bottom of the page
---

<!-- Highlight bubble -->
<!-- <div class="highlight-bubble">
    <strong>I am on the job market this year, seeking full-time engineering roles in aerospace and robotics.</strong>
    If you or your team are hiring, don't hesitate to reach out!
</div> -->
I am a postdoctoral research scholar in the [Department of Electrical and Systems Engineering](https://www.ese.upenn.edu/) and the [GRASP Lab](https://www.grasp.upenn.edu/) at the University of Pennsylvania, working with [George Pappas](https://www.georgejpappas.org/group/#george-pappas) and [Nikolai Matni](https://nikolaimatni.github.io/) at the intersection of control, robust decision-making, machine learning, and robotics. Previously, I completed my PhD in the [Intelligent Robot Motion Laboratory](https://irom-lab.princeton.edu/) at Princeton University, advised by [Ani Majumdar](https://irom-lab.princeton.edu/majumdar/). 

My research develops theory for robotic systems which holds nonasymptotically (i.e., in finite samples) under realistic models of uncertainty in the operating environment. These guarantees are designed to codify, complement, and inform empirical developments within the field. In general, my work can be partitioned according to the modeling assumptions over the uncertainty, spanning the worst-case (adversarial, or 'nonstochastic') settings to i.i.d. stochastic realizations of uncertainty. The former occur _within-trajectory_, where the signals may have strong temporal correlation, whereas the latter tend to arise in batch contexts and _across-trajectory_ validation. One of the most compelling areas of research at present is understanding the scope of the 'in-between:' when the data is correlated but admits structure so as to not require fully adversarial treatment. 

During my PhD I developed methods tailored to each of these domains. In the adversarial context, I developed an algorithm for learned controller validation in the setting of linear systems ([MOTR](https://proceedings.mlr.press/v144/ghai21a.html)) using techniques from regret minimization in online learning; this was later lifted to the higher-level problem of obstacle avoidance ([OLC](https://proceedings.mlr.press/v229/snyder23a.html)). The latter was one of the first examples of practical implementation of online regret-minimizing controllers on hardware. In the stochastic context, we developed methods for online failure prediction and mitigation via extending PAC-Bayes generalization bounds [FP](https://www.roboticsproceedings.org/rss18/p042.html). More recently, we have applied techniques from sequential analysis and safe, anytime-valid inference (SAVI) for multivalent problems of _evaluation_ within the robotics context. This has led to fruitful developments within the context of policy comparison and active data collection, as illustrated by [STEP](https://tri-ml.github.io/step/), [NSCORE](), and [AnyRank](). 

Prior to my PhD, I received my bachelor's degrees in Aerospace Engineering and Economics from the [University of Maryland, College Park](https://umd.edu/) (go Terps!). Outside of work I enjoy cycling, chess, classical music, and playing tennis.

<!-- I am a PhD Candidate in the [Intelligent Robot Motion Lab](https://irom-lab.princeton.edu/) and [FAST Group](https://fluids.princeton.edu/), co-advised by [Ani Majumdar](https://irom-lab.princeton.edu/majumdar/) and [Marcus Hultmark](https://mae.princeton.edu/people/faculty/hultmark). My research aims to improve aerial vehicle performance in the real world through tightly-integrated perception, planning, and control. Specifically, using high-dimensional sensors (such as vision and flow sensing) and machine learning to unlock new capabilities. During my PhD, I invented an omnidirectional flow sensor for UAVs [(patent)](#patents) and developed a wind-aware flight controller for gust rejection [(FlowDrone)](/flowdrone/). In addition, I advanced state-of-the-art in monocular micro aerial vehicle navigation through simultaneous depth estimation and 3D reconstruction [(MonoNav)](/mononav/). My work aims to drive transformative autonomy in robotics applications such as urban air mobility, package delivery, infrastructure inspection, and ISR.

Here is a 3-min overview of my recent work, from [Princeton Research Day](https://researchday.princeton.edu/):

<div class="row mt-3">
    <div class="col-sm col-12 mt-3 mt-md-0 d-flex justify-content-center">
        <div class="embed-responsive embed-responsive-16by9" style="width: 90%;">
            <iframe class="embed-responsive-item rounded z-depth-1" src="https://www.youtube.com/embed/uw0p1I9V2CM"></iframe>
        </div>
    </div>
</div>


<div class="row mt-3">
    <div class="col-sm col-12">
    </div>
</div> -->

<!-- Prior to the PhD, I received bachelor's and master's degrees in Mechanical Engineering from [Stanford University](https://me.stanford.edu/). Outside of work, I love to fly aircraft, and I am a member of both the [Princeton Flying Club](http://www.princetonflyingclub.com/) and [Soaring Tigers](https://soaringtigers.org/). I recently earned my instrument rating, and have written about my experience [here](./projects/instrument). -->


Feel free to contact me at: ``dsnyder5`` \[at\] ``engineering`` \[dot\] ``upenn`` \[dot\] ``edu``.
