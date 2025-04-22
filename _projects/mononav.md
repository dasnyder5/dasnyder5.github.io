---
layout: default
permalink: /mononav/
title: MonoNav
description: MAV Navigation via Monocular Depth Estimation and Reconstruction
img: assets/img/publication_preview/MonoNav_Anchor.png
importance: 1
category: work
---

<h1><center><span style="font-weight:bold;">MonoNav:</span><br>MAV Navigation via Monocular Depth Estimation and Reconstruction</center></h1>
<br>
<table style="width: 80%; max-width: 800px; margin: 0 auto;">
    <tr>
        <td style="text-align: center; width: 100px;">
            <span style="font-size: 22px; font-weight:bold;"><a href="https://natesimon.github.io/" target="_blank">Nathaniel Simon</a></span>
        </td>
        <td style="text-align: center; width: 100px;">
            <span style="font-size: 22px; font-weight:bold;"><a href="https://irom-lab.princeton.edu/majumdar/" target="_blank">Anirudha Majumdar</a></span>
        </td>
    </tr>
</table>
<td align=center style="width: 80%; max-width: 800px; margin: 0 auto; text-align: center;">
<div style="text-align: center; max-width: 200px; margin: 0 auto;">
    <p style="margin-top: 4px;"></p>
    <a href="https://irom-lab.princeton.edu/">
        <img src="../assets/img/irom_lab_logo.png" alt="IRoM" style="width: 100%;">
    </a>
</div>
<p style="margin-top: 2px;"></p>
<center><span style="font-size:20px"><a href="https://robo.princeton.edu/" target="_blank">Princeton University</a></span></center>
</td>
<br>
<table style="width: 70%; max-width: 800px; margin: 0 auto;">
    <tr>
    <td align=center width=20px><center><span style="font-size:28px">
        <a href="https://arxiv.org/pdf/2311.14100.pdf" target="_blank"><img src="../assets/img/PDF_file_icon.png" alt="PDF File Icon" style="max-width: 50px; height: auto;"></a></span></center>
    </td>
    <td align=center width=20px><center><span style="font-size:28px">
        <a href="https://youtu.be/msWLSfOmTpI" target="_blank"><img src="../assets/img/YouTube_full-color_icon_(2017).png" alt="Youtube Play Icon" style="max-width: 50px; height: auto;"></a></span></center>
    </td>
        <td align=center width=20px><center><span style="font-size:28px">
        <a href="https://github.com/natesimon/MonoNav/" target="_blank"><img src="../assets/img/GitHub_Invertocat_Logo.png" alt="Github Icon" style="max-width: 50px; height: auto;"></a></span></center>
    </td></tr>
    <tr>
    <td align=center width=20px><center><span style="font-size:28px"><a href="https://arxiv.org/pdf/2311.14100.pdf">[PDF]</a></span></center></td>
    <td align=center width=20px><center><span style="font-size:28px"><a href="https://youtu.be/msWLSfOmTpI">[Video]</a></span></center></td>
    <td align=center width=20px><center><span style="font-size:28px"><a href="https://github.com/natesimon/MonoNav/">[Code]</a></span></center></td>
    </tr>
</table>
<br>
<table style="width: 80%; max-width: 800px; margin: 0 auto;">
    <tr>
        <td style="text-align: center; width: 20%; vertical-align: top;">
            <a href="https://thenounproject.com/icon/award-1976316/" target="_blank"><img src="../assets/img/mononav/noun-award-1976316.png" alt="Image Description" style="max-width: 50px; height: auto;"></a>
        </td>
        <td style="width: 80%;">
            <p style="font-size: 20px;">
                <b>Best Paper:</b> <a href="https://wp.nyu.edu/workshopiros2023superautonomy/">Learning Robot Super Autonomy</a> Workshop at IROS 2023.
            </p>
        </td>
    </tr>
    <tr>
        <td style="text-align: center; width: 20%;">
            <a href="https://thenounproject.com/icon/binoculars-5031330/" target="_blank"><img src="../assets/img/mononav/noun-binoculars-5031330.png" alt="Image Description" style="max-width: 50px; height: auto;"></a>
        </td>
        <td style="width: 80%;">
            <p style="font-size: 20px;">
                <b>In Proceedings:</b> <a href="https://iser2023.org/">ISER 2023</a>.
            </p>
        </td>
    </tr>
</table>
<br>

<div class="row mt-3">
    <div class="col-sm col-12 mt-3 mt-md-0 d-flex justify-content-center">
        <div class="embed-responsive embed-responsive-16by9" style="width: 100%; max-width: 800px; margin: 0 auto;">
            <iframe class="embed-responsive-item rounded z-depth-1" src="https://www.youtube.com/embed/msWLSfOmTpI"></iframe>
        </div>
    </div>
</div>
<br>
<div style="font-size: 18px; width: 100%; max-width: 800px; margin: 0 auto; text-align:justify">
<b>Abstract:</b> A major challenge in deploying the smallest of Micro Aerial Vehicle (MAV) platforms (< 100 g) is their inability to carry sensors that provide high-resolution metric depth information (e.g., LiDAR or stereo cameras). Current systems rely on end-to-end learning or heuristic approaches that directly map images to control inputs, and struggle to fly fast in unknown environments. In this work, we ask the following question: using only a monocular camera, optical odometry, and offboard computation, can we create metrically accurate maps to leverage the powerful path planning and navigation approaches employed by larger state-of-the-art robotic systems to achieve robust autonomy in unknown environments? We present MonoNav: a fast 3D reconstruction and navigation stack for MAVs that leverages recent advances in depth prediction neural networks to enable metrically accurate 3D scene reconstruction from a stream of monocular images and poses. MonoNav uses off-the-shelf pre-trained monocular depth estimation and fusion techniques to construct a map, then searches over motion primitives to plan a collision-free trajectory to the goal. In extensive hardware experiments, we demonstrate how MonoNav enables the Crazyflie (a 37 g MAV) to navigate fast (0.5 m/s) in cluttered indoor environments. We evaluate MonoNav against a state-of-the-art end-to-end approach, and find that the collision rate in navigation is significantly reduced (by a factor of 4). This increased safety comes at the cost of conservatism in terms of a 22% reduction in goal completion.
</div>
<br>
<center><h2><a href="https://github.com/natesimon/MonoNav/">Try MonoNav!</a></h2></center>
<div style="font-size: 18px; width: 100%; max-width: 800px; margin: 0 auto; text-align:justify">
    The <a href="https://github.com/natesimon/MonoNav/">MonoNav GitHub Repo</a> includes all of the code for this project, including a demo dataset (monocular images and poses) to run depth estimation, reconstruction, and planning pipelines out of the box (no robot needed).
</div>
<div style="text-align: center; max-width: 800px; margin: 0 auto;">
    <p style="margin-top: 4px;"></p>
    <a href="https://raw.githubusercontent.com/natesimon/MonoNav/main/utils/reconstruction.gif">
        <img src="https://raw.githubusercontent.com/natesimon/MonoNav/main/utils/reconstruction.gif" alt="MonoNav Demo" style="width: 80%;">
    </a>
</div>
<br>
<center><h2>MonoNav System Overview</h2></center>
<br>
<div style="font-size: 18px; width: 100%; max-width: 800px; margin: 0 auto; text-align:justify">
    MonoNav uses pre-trained depth-estimation networks (<a href="https://github.com/isl-org/ZoeDepth">ZoeDepth</a>) to convert RGB images into depth estimates, then fuses them into a 3D reconstruction using <a href = "http://www.open3d.org/">Open3D</a>. MonoNav then selects from motion primitives to navigate collision-free to a goal position. If the motion primitive selection problem is infeasible (e.g., no motion primitive remains sufficiently far from obstacles), then MonoNav executes a safety maneuver (e.g., stop and land).
</div>
<div style="text-align: center; max-width: 800px; margin: 0 auto;">
    <p style="margin-top: 4px;"></p>
    <a href="../../assets/img/mononav/MonoNav_System.png">
        <img src="../../assets/img/mononav/MonoNav_System.png" alt="MonoNav System" style="width: 100%;">
    </a>
</div>
<br>
<center><h2>Examples: Reconstruction and Planning</h2></center>
<div style="font-size: 18px; width: 100%; max-width: 800px; margin: 0 auto; text-align:justify">
    MonoNav is capable of navigating in diverse, constrained indoor environments. Specifically, hallways with corners, curved walls, and furniture. The crash in Hall 4 (bottom right) was due to MonoNav turning into a previously occluded obstacle. This limitation occurs because MonoNav is currently configured to explore aggressively, treating unseen space as free.
</div>
<div style="text-align: center; max-width: 800px; margin: 0 auto;">
    <p style="margin-top: 4px;"></p>
    <a href="../../assets/img/mononav/MonoNavReconstructions.png">
        <img src="../../assets/img/mononav/MonoNavReconstructions.png" alt="MonoNav Reconstructions" style="width: 100%;">
    </a>
</div>
<br>
<center><h2>Results: Comparison to State of the Art</h2></center>
<div style="font-size: 18px; width: 100%; max-width: 800px; margin: 0 auto; text-align:justify">
    We evaluate MonoNav against <a href="https://general-navigation-models.github.io/nomad/">NoMaD: Goal Masking Diffusion Policies for Navigation and Exploration</a>, a state of the art approach in monocular navigation. NoMaD uses a transformer encoder and diffusion policy, trained over 100 hours of robot navigation data, to directly output action candidates with optional goal-image conditioning to further refine the action candidates.  
</div>
<br>
<div style="font-size: 18px; width: 100%; max-width: 800px; margin: 0 auto; text-align:justify">
    We find that NoMaD performs well when a clear maneuver is required (e.g., turn left to avoid a wall), but struggles in settings where more nuanced action candidates are required. For example, in a straight hallway segment, NoMaD produces straight action candidates, which are insufficiently expressive and evasive to avoid collision as the quadrotor drifts into the wall.
</div>
<div style="text-align: center; max-width: 800px; margin: 0 auto;">
    <p style="margin-top: 4px;"></p>
    <a href="../../assets/img/mononav/MonoNav_Results.png">
        <img src="../../assets/img/mononav/MonoNav_Results.png" alt="MonoNav System" style="width: 100%;">
    </a>
</div>
<div style="font-size: 18px; width: 100%; max-width: 800px; margin: 0 auto; text-align:justify">
   In 15 trials in 5 unique environments, we plot the goal positions, trajectories, and crash locations. MonoNav's key advantage is its ability to explicitly reason about scale, which allows self-arresting when an imminent collision is detected. This capability results in a 4x reduction in collisions. This increase in safety comes at the cost of conservatism, as MonoNav has an associated 22% reduction in goal completion.
</div>
<br>
<div style="font-size: 18px; width: 100%; max-width: 800px; margin: 0 auto; text-align:justify">
    <p><strong>Bibtex</strong></p>
    <pre>
@inproceedings{simon2023mononav,
    title     = {MonoNav: MAV Navigation via Monocular Depth Estimation and Reconstruction},
    author    = {Nathaniel Simon and Anirudha Majumdar},
    booktitle = {Symposium on Experimental Robotics (ISER)},
    year      = {2023},
    url       = {https://arxiv.org/abs/2311.14100}
}</pre>
</div>

