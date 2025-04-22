---
layout: default
permalink: /ladrone/
title: LaDrone
description: Micro Aerial Vehicles as Lagrangian Particles in the Atmospheric Boundary Layer
img: assets/img/LaDrone_Outside.jpeg
importance: 1
category: work
---

<h1><center><span style="font-weight:bold;">Go with the Flow:</span><br>Micro Aerial Vehicles<br>as Lagrangian Particles in<br>the Atmospheric Boundary Layer</center></h1>
<br>
<table style="width: 80%; max-width: 800px; margin: 0 auto;">
    <tr>
        <td style="text-align: center; width: 100px;">
            <span style="font-size: 22px; font-weight:bold;"><a href="https://natesimon.github.io/" target="_blank">Nathaniel Simon</a></span>
        </td>
        <td style="text-align: center; width: 100px;">
            <span style="font-size: 22px; font-weight:bold;"><a href="https://www.linkedin.com/in/skywalkerli/" target="_blank">Skywalker Li</a></span>
        </td>
    </tr>
</table>
<table style="width: 60%; max-width: 800px; margin: 0 auto;">
    <tr>
            <td style="text-align: center; width: 100px;">
            <span style="font-size: 22px; font-weight:bold;"><a href="https://mae.princeton.edu/people/graduate-students/conlin-0" target="_blank">Nick Conlin</a></span>
        </td>
    </tr>
</table>
<table style="width: 60%; max-width: 800px; margin: 0 auto;">
    <tr>
        <td style="text-align: center; width: 100px;">
            <span style="font-size: 22px; font-weight:bold;"><a href="https://sites.google.com/view/njwei" target="_blank">Nathan Wei</a></span>
        </td>
        <td style="text-align: center; width: 100px;">
            <span style="font-size: 22px; font-weight:bold;"><a href="https://www.girguissedky.com/" target="_blank">Girguis Sedky</a></span>
        </td>
    </tr>
    <tr>
        <td style="text-align: center; width: 100px;">
            <span style="font-size: 22px; font-weight:bold;"><a href="https://irom-lab.princeton.edu/majumdar/" target="_blank">Anirudha Majumdar</a></span>
        </td>
        <td style="text-align: center; width: 100px;">
            <span style="font-size: 22px; font-weight:bold;"><a href="https://mae.princeton.edu/people/faculty/hultmark" target="_blank">Marcus Hultmark</a></span>
        </td>
    </tr>
    <tr>
    <td align=center width=40px><center><span style="font-size:28px">
        <a href="https://irom-lab.princeton.edu/">
            <img src="../assets/img/irom_lab_logo.png" alt="IRoM" style="width: 80%;">
        </a></span></center>
    </td>
    <td align=center width=40px><center><span style="font-size:28px">
        <a href="https://fluids.princeton.edu/" target="_blank"><img src="../assets/img/fast_lab_logo.jpg" alt="FAST Lab Logo" style="width: 30%;"></a></span></center>
    </td>
    </tr>
</table>
<center><span style="font-size:30px"><a href="https://mae.princeton.edu/" target="_blank">Princeton University</a></span></center>
<br>
<table style="width: 80%; max-width: 800px; margin: 0 auto;">
    <tr>
        <td style="text-align: center; width: 50%;">
            <a href="https://thenounproject.com/icon/binoculars-5031330/" target="_blank"><img src="../assets/img/mononav/noun-binoculars-5031330.png" alt="Image Description" style="max-width: 50px; height: auto;"></a>
        </td>
        <td style="width: 50%;">
            <p style="font-size: 20px;">
                <b>As seen at:</b> <a href="https://meetings.aps.org/Meeting/DFD23/Session/J21.9">APS DFD 2023</a>.<br>
                <a href="../assets/pdf/LaDrone_APS_2023.pdf">(Presentation slides.)</a>
            </p>
        </td>
    </tr>
    <tr>
        <td style="text-align: center; width: 50%;">
            <a href="https://thenounproject.com/icon/newspaper-68257/" target="_blank"><img src="../assets/img/mononav/noun-newspaper.png" alt="Image Description" style="max-width: 50px; height: auto;"></a>
        </td>
        <td style="width: 50%;">
            <p style="font-size: 20px;">
                <b>APS News feature: </b><a href="https://aps.org/publications/apsnews/202402/drones.cfm">Drones Blowing, and Flying, In The Wind</a>.
            </p>
        </td>
    </tr>
</table>
<br>
<div style="text-align: center; font-size: 20px; width: 60%; max-width: 800px; margin: 0 auto;">
    <b>Warning:</b> This is ongoing work. Stay tuned for more details and comprehensive evaluation!
</div>
<br>
<div class="row mt-3">
    <div class="col-sm col-12 mt-3 mt-md-0 d-flex justify-content-center">
        {% include video.html path="assets/video/Flow.mp4" class="img-fluid rounded z-depth-1" controls=true autoplay=true loop=true%}
    </div>
</div>
<div class="caption" style="font-size: 18px;">
    Slow motion video of LaDrone hovering in a flow (left to right), with tracer particles illuminated by a time-resolved laser. Image credit: Girguis Sedky.
<br>

<div style="font-size: 20px; width: 100%; max-width: 800px; margin: 0 auto; text-align:justify">
<p style="margin-top: 4px;"></p>
<b style="font-size: 22px;">Abstract:</b> Scientists are interested in the movement of particles in our atmosphere, for applications such as measuring and modeling pollutant dispersion. Conventional particle velocimetry techniques are restricted to measurement volumes on the centimeter scale; recent tracking algorithm and tracer particle advances increase domain sizes into the meter range, but to reach hundreds or thousands of meters alternative methods are required. The authors propose LaDrone, a particle velocimetry technique based on a 40 gram Micro Aerial Vehicle (MAV). Tasked only to compensate for gravity, LaDrones move freely due to the wind force in three dimensions. They can be tracked at centimeter-level precision using RTK GPS, collecting atmospheric boundary layer data as they are swept by the wind. Such data could be used to analyze the atmosphere at the kilometer scale. 
</div>
<br>

<div style="font-size: 20px; width: 100%; max-width: 800px; margin: 0 auto; text-align:justify">
<p style="margin-top: 4px;"></p>
<b style="font-size: 22px;">Core Aspects of LaDrone:</b>
<ol>
  <b><li>Micro Aerial Vehicle (~40 grams)</li></b>
  We want LaDrone to be as light as possible. By keeping the inertia low, LaDrone responds faster to subtle velocity changes in the surrounding fluid. This enables the measurement of smaller length and time scales that a larger vehicle would filter out. To do this, we use the 27 gram open-source <a href="https://www.bitcraze.io/products/crazyflie-2-1/">Crazyflie 2.1</a> as a base.
  <b><li>Gravity Compensation Control (Neutral Buoyancy)</li></b>
  LaDrone uses a simple heuristic to behave like a fluid particle: <i>compensate only for gravity, letting the fluid forces push you in every direction</i>. To do this, we instruct LaDrone to keep its roll and pitch angles zero, and output its weight in thrust. This keeps the thrust vector equal and opposite the weight vector!
  <b><li>Centimeter-level GNSS Tracking</li></b>
  Conventional GNSS tracking is not very accurate due to <a href="https://en.wikipedia.org/wiki/Error_analysis_for_the_Global_Positioning_System">numerous sources of error</a>. However, correction signals can reduce this error from 2-10 m to sub-centimeter precision! Since our position is not needed real-time, we use a post-processing kinematic (PPK) approach (<a href="https://rtklibexplorer.wordpress.com/2019/08/24/dual-frequency-ppk-solutions-with-rtklib-and-the-u-blox-f9p/">example</a>).
</ol>
</div>
<br>

<div style="text-align: center; max-width: 800px; margin: 0 auto;">
    <p style="margin-top: 4px;"></p>
    <a href="../../assets/img/LaDrone_Outside.jpeg">
        <img src="../../assets/img/LaDrone_Outside.jpeg" alt="LaDrone System" style="width: 80%;">
    </a>
</div>
<div class="caption" style="text-align: center; font-size: 18px; width: 80%;  margin: 0 auto;">
    LaDrone consists of entirely off-the-shelf components: a <a href="https://www.bitcraze.io/products/crazyflie-2-1/">Crazyflie 2.1</a> micro aerial vehicle, a <a href="https://www.sparkfun.com/products/15136">ZED-F9P</a> RTK GPS board + antenna, and a <a href="https://www.sparkfun.com/products/13712">data logger</a>.
</div>

<div style="font-size: 20px; width: 100%; max-width: 800px; margin: 0 auto; text-align:left">
<p style="margin-top: 4px;"></p>
<b style="font-size: 22px;">Ongoing work:</b>
<ol>
  <li>Reduce weight through custom components,</li>
  
  <li>Improve GNSS tracking performance with L2 antenna,</li>

  <li>Evaluate in windy, outdoor environments.</li>
</ol>
</div>

<div style="font-size: 18px; width: 100%; max-width: 800px; margin: 0 auto; text-align:justify">
<p style="margin-top: 4px;"></p>
<b style="font-size: 20px;">The story behind the name:</b> In fluid dynamics, the study of a single fluid parcel or particle along its trajectory is known as the <i>Lagrangian</i> specification. Since we aspire to use a drone to track the movement of an individual fluid parcel, we call our "Lagrangian" vehicle: LaDrone!
</div>
<br>