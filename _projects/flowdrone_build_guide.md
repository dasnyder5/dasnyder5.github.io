---
layout: page
title: flowdrone build guide (in-progress)
description: autonomous quadrotor control via PX4
img: assets/img/x500/X500.jpg_original
importance: 1
category: hidden
---

This guide walks through the design of FlowDrone, an autonomous quadrotor platform used in my research. This guide enables something very specific: **autonomous, onboard, indoor/outdoor control of a PX4 platform**. In other words, all computation and sensing is contained _onboard_ (the system does not rely on motion capture or GPS for localization). Furthermore, the custom control scripts can be written in Python or C++, and commands to the PX4 are sent over the [PX4-ROS 2 Bridge](https://docs.px4.io/v1.12/en/ros/ros2_comm.html). Under this architecture, it is possible to read-in (and publish) any of the [uORB topics](https://docs.px4.io/main/en/middleware/uorb.html), as well as to publish position, velocity, acceleration, attitude, or body rate setpoints using [offboard control](https://docs.px4.io/main/en/ros/ros2_offboard_control.html). While the FlowDrone platform is specifically designed for gust rejection research (via novel flow sensing), the hardware itself can be used for many other applications. Furthermore, the software could be used for offboard control of any autonomous quadrotor using the Pixhawk 4.

There is a great deal of open-source content by PX4 (tutorials, pages, forum Q&A). This guide is meant to augment that content by providing a clear, descriptive build guide for one specific platform. Details specific to the FlowDrone's gust rejection capability will be outlined in later sections: [Mast & DAQ](https://natesimon.github.io/projects/flowdrone/#mast-and-daq) and [Results](https://natesimon.github.io/projects/flowdrone/#results).

<div class="container" style="font-size: 20px; width: 100%; max-width: 800px; margin: 0 auto;">
    <div class="row">
        <!-- First column (appears second on small devices) -->
        <div class="col-md-12 col-lg-4 mt-3 order-md-2 order-lg-1">
            <div class="content">
                <!-- Your content for the first column here -->
                {% include figure.html path="assets/img/x500/X500.jpg_original" title="example image" class="img-fluid rounded z-depth-1" %}
                <div class="caption">The FlowDrone platform in hover.</div>
            </div>
        </div>
        <!-- Second column (appears first on small devices) -->
        <div class="col-md-12 col-lg-8 mt-3 order-md-1 order-lg-2">
            <div class="content">
                <!-- Your content for the second column here -->
                {% include figure.html path="assets/img/x500/system_overview_freq.png" title="example image" class="img-fluid rounded z-depth-1" %}
                <div class="caption">The system overview, as instantiated in our paper. The system consisted of a Pixhawk 4 autopilot (for low-level control), Raspberry Pi companion computer (for learning-based autonomous control in Python), and a custom MAST flow sensor with corresponding data acquisition unit (DAQ).</div>
            </div>
        </div>
    </div>
</div>

If you find this guide to be helpful in your research, please cite our [paper](https://arxiv.org/pdf/2210.05857.pdf), which appeared at [ICRA 2023](https://www.icra2023.org/).
```
@inproceedings{simon2023flowdrone,
  title={FlowDrone: wind estimation and gust rejection on UAVs using fast-response hot-wire flow sensors},
  author={Simon, Nathaniel and Ren, Allen Z and Piqu{\'e}, Alexander and Snyder, David and Barretto, Daphne and Hultmark, Marcus and Majumdar, Anirudha},
  booktitle={2023 IEEE International Conference on Robotics and Automation (ICRA)},
  pages={5393--5399},
  year={2023},
  organization={IEEE}
}

```

## Table of Contents
1. [**Hardware**](#hardware)
2. [**ROS2 Bridge (C++ / Python)**](#ros2-python)
3. [**Offboard Control**](#offboard-control)
4. [**The MAST and DAQ**](#mast-and-daq)
5. [**Results**](#results)

### Hardware <a name="hardware"></a>

The FlowDrone is based on the [Holybro X500](https://docs.px4.io/main/en/frames_multicopter/holybro_x500_pixhawk4.html) kit, which includes the following components:
- [Pixhawk 4 autopilot](https://docs.px4.io/main/en/flight_controller/pixhawk4.html)
- Pixhawk 4 GPS
- Power Management - PM07
- Holybro Motors - 2216 KV880 x4
- Holybro BLHeli S ESC 20A x4
- Propellers - 1045 x4
- Battery Strap
- Power and Radio Cables
- Wheelbase - 500 mm
- 433 MHz Telemetry Radio/915 MHz Telemetry Radio

Not included is the receiver, transmitter, and battery. We used an [FrSky X8R](https://www.amazon.com/FrSky-Taranis-Compatible-Receiver-8-Channel/dp/B00RCAHHFM), [FrSky Taranis X9D Plus](https://www.amazon.com/FrSky-Taranis-Access-Telemetry-Silver/dp/B07VRP1V76/), and [Turnigy 5200mAh 4S Lipo Pack w/XT60](https://hobbyking.com/en_us/turnigy-high-capacity-5200mah-4s-12c-multi-rotor-lipo-pack-w-xt60.html).

To interface with the [Pixhawk 4](http://www.holybro.com/product/pixhawk-4/) autopilot, we purchased an 8GB [Raspberry Pi 4](https://www.raspberrypi.org/products/raspberry-pi-4-model-b/) companion computer. In addition to the PM07 Power Module, we installed a [Matek X Class 12S Power Distribution Board](https://www.amazon.com/Distribution-FCHUB-12S-Supports-Regulators-Current/dp/B07MHKTF7F/) to provide a 5V supply to the Raspberry Pi.

Finally, for GPS-denied state estimation (e.g. indoors), we installed a [LIDAR-Lite v3](https://www.garmin.com/en-US/p/557294) range sensor and [PX4Flow](https://www.amazon.com/HolyBro-PX4FLOW-Kit-v1-31/dp/B07FNDTC53/) optical flow sensor. The total cost of the aforementioned hardware was approximately $1,500. Building the X500 kit takes about a day. I highly recommend Alex Fache's [Pixhawk 4 + S500 Drone Build Tutorial](https://www.youtube.com/watch?v=wsrRNqihjE4&list=PLp8NnRiCCsXs-PI_jt96-bB4bOuiXRLKg).

<!-- Add padding to the detail (toggle list) --><style>
  details p {
    padding-left: 20px;
  }
  details ul,
  details ol {
    padding-left: 60px;
  }
</style>

<details><summary><strong>TIPS: PX4Flow Setup and Installation</strong></summary>
    <p>Follow the instructions from the <a href="https://docs.px4.io/master/en/sensor/px4flow.html" target="_blank">px4.io</a> website.
    To focus the lens:</p>
    <ol>
        <li>Plug in the PX4Flow by itself while QGroundControl is open. Navigate to the firmware tab and update the firmware by following the instructions.</li>
        <li>In Vehicle Setup, you should see 'PX4Flow' appear. Clicking on that, you can see the black and white camera output for focusing.</li>
        <li>To focus the lens, loosen the outer ring (around the lens) which will allow you to screw - unscrew the lens itself, changing the focal distance and focusing the text in the camera view.</li>
        <li>In Analyze Tools -> MavLink Inspector -> OPTICAL_FLOW, you can see the range reading from the PX4Flow in ground_distance.</li>
    </ol>
    <p>Pluggin the Pixhawk 4 back in, you will have to toggle the <code>SENS_EN_PX4FLOW</code> parameter value from 0->1. There are multiple ways to do this:</p>
    <ul>
        <li>Use QGroundControl -> Vehicle Setup -> Parameters -> <code>SENS_EN_PX4FLOW</code></li>
        <li>QGroundControl -> Analyze Tools -> MAVLink console: <code>param set SENS_EN_PX4FLOW 1</code></li>
    </ul> 
    <p>Once you have the PX4Flow sensor connected to the Pixhawk 4 via I2C1 -> I2CA, you can access the PX4Flow via QGroundControl -> Analyze Tools -> MAVLink console. The following commands are useful:</p>
    <ol>
        <li><code>> px4flow info</code> for general info </li>
        <li><code>> px4flow start -X</code> works to get the PX4Flow started (on I2C bus 4 (external). In the future, this may or may not start automatically upon booting up the Pixhawk 4.</li>
        <li>MAVLink Insector should show new topics: OPTICAL_FLOW_RAD and DISTANCE. Keep in mind that DISTANCE from the PX4Flow is quite imprecise, hence the need for the LIDAR-Lite-v3.</li>
    </ol>
    <p>Finally, in order to use the PX4Flow for state estimation, you must change the <code>EKF2_AID_MASK</code> parameter to use Optical Flow instead of GPS. This can be done in QGroundControl -> Vehicle Setup -> Parameters -> <code>EKF2_AID_MASK</code>.</p>
</details>

<details><summary><strong>TIPS: LIDAR-Lite-v3 Setup and Installation</strong></summary>
    <p>Follow the instructions from the <a href="https://docs.px4.io/main/en/sensor/lidar_lite.html" target="_blank">px4.io</a> website.
    Similarly to with the PX4Flow, the LIDAR-Lite-v3 status can be checked using MAVLink console with <code>ll40ls status</code>. With the LIDAR installed, you should see the quality of the optical flow estimates be consistently high (~255). You can check the quality either through MAVLink Inspector -> OPICAL_FLOW_RAD or <code>listener optical_flow</code> in MAVLink console.
    </p>
</details><br>

### ROS2 Bridge (C++ / Python) <a name="ros2-python"></a>

The PX4 computer and firmware is optimized for speed. This optimization renders the [firmware code](https://github.com/PX4/PX4-Autopilot/tree/main/src/modules) challenging to modify directly. It is instead recommended that you use a [companion computer](https://docs.px4.io/main/en/companion_computer/) for your custom control scripts, and then use a communication protocol to send (receive) data to (from) the PX4. Of the available options, we chose to use the [PX4-ROS 2 Bridge](https://docs.px4.io/v1.12/en/ros/ros2_comm.html), which was recommended at the time. At the time of writing, the similar but subtly different [PX4-XRCE-DDS Bridge](https://docs.px4.io/main/en/ros/ros2_comm.html) is recommended instead. For this tutorial, we will use the [PX4-ROS 2 Bridge](https://docs.px4.io/v1.12/en/ros/ros2_comm.html) (which depends on Fast-DDS as opposed to XRCE-DDS) - but keep in mind that this may no longer be officially supported.

#### Installing Prerequisites on the Raspberry Pi
Follow the primary guide ([PX4-ROS 2 Bridge](https://docs.px4.io/v1.12/en/ros/ros2_comm.html)) closely. My notes seek to augment the main tutorial. There are four main prerequisites.
<details><summary><strong>Install Ubuntu 20.04</strong></summary>
    <p>First, boot Ubuntu 20.04 onto the Raspberry Pi (<a href="https://www.youtube.com/watch?v=GVgMM_TFeOw" target="_blank">youtube</a>) using an SD card. I installed <a href="https://cdimage.ubuntu.com/releases/focal/release/" target="_blank">ubuntu-20.04.5-preinstalled-server-arm64+raspi.img.xz</a>. If you would like the desktop version, you can upgrade via <code>sudo apt-get install ubuntu-desktop</code>. The youtube tutorial recommends modifying the netplan to enable connection to wifi upon boot. I prefer to install the default .iso and connect the Raspberry Pi to a monitor, mouse, and keyboard, and to edit the <a href="https://dev.to/joeneville_/configure-ubuntu-wifi-with-netplan-4je0" target="_blank">netplan</a> from there.</p> <p>Here is an example of how you could configure the netplan via <code>sudo nano /etc/netplan/50-cloud-init.yaml </code>: (be very careful about indentation in .yaml files!)
        <pre>
            <code>
    network:
        ethernets:
            eth0:
                dhcp4: true
                optional: true
        wifis:
            wlan0:
                addresses:
                - 192.168.0.175/24
                gateway4: 192.168.0.1
                nameservers:
                    addresses: [192.168.0.1, 8.8.8.8]
                optional: true
                access-points:
                    "WIFI NAME":
                        password: "WIFI PASSWORD"
        version: 2
            </code>
        </pre>
    Once you have the netplan configured, you can apply the changes with <code>sudo netplan apply 50-cloud-init.yaml</code>. After a minute or so, you can check the status of the network with <code>ping google.com</code>. If you are able to ping, your pi is connected to wifi!</p>

</details>
<details><summary><strong>Install Fast-DDS</strong></summary>
    <p>Follow the main tutorial: <a href="https://docs.px4.io/v1.12/en/dev_setup/fast-dds-installation.html" target="_blank">Fast DDS Installation</a>. Here is the exact order in which I installed Fast-DDS and FastRTPSGen on a fresh Ubuntu 20.04 install:</p>
    <pre>
        <code>
sudo apt install openjdk-11-jre-headless
sudo apt install curl
sudo apt install zip
curl -s "https://get.sdkman.io" | bash
source "/home/ubuntu/.sdkman/bin/sdkman-init.sh"
sdk install gradle 6.3
sudo apt install cmake
sudo apt-get install build-essential

git clone https://github.com/eProsima/foonathan_memory_vendor.git
cd foonathan_memory_vendor
mkdir build && cd build
cmake ..
sudo cmake --build . --target install

sudo apt install libssl-dev
git clone --recursive https://github.com/eProsima/Fast-DDS.git -b v2.0.2 ~/FastDDS-2.0.2
cd ~/FastDDS-2.0.2
mkdir build && cd build
cmake -DTHIRDPARTY=ON -DSECURITY=ON ..
make -j$(nproc --all)
sudo make install

git clone --recursive https://github.com/eProsima/Fast-DDS-Gen.git -b v1.0.4 ~/Fast-RTPS-Gen \
    && cd ~/Fast-RTPS-Gen \
    && ./gradlew assemble \
    && sudo ./gradlew install
        </code>
    </pre>
    <p>You can check your installation with <code>which fastrtpsgen</code>.</p>
</details>
<details><summary><strong>Install ROS2 Foxy</strong></summary>
    <p>Follow the Ubuntu (Debian) <a href="https://docs.ros.org/en/foxy/Installation/Ubuntu-Install-Debians.html" target="_blank">installation instructions</a> for ROS2 Foxy. I opted for the ROS-Base Install (Bare Bones) as opposed to the Desktop install. After installing and sourcing your installation, you should be able to run <code>ros2</code> without error. Make sure you install the additional dependencies in the <a href="https://docs.px4.io/v1.12/en/ros/ros2_comm.html#install-ros-2" target="_blank">PX4 tutorial</a>.</p>
</details>
<details><summary><strong>Install and build the ROS 2 Workspace (<code>px4_ros_com</code> and <code>px4_msgs</code>)</strong></summary>
    <p>The <code>px4_ros_com</code> and <code>px4_msgs</code> messaging libraries provide the infrastructure to communicate with the Pixhawk 4 over ROS2. The official repositories do not (at the time of writing) support publisher/subscriber nodes written in Python, which we found very helpful in our development. If you wish to have this Python capability, I recommend installing our forks (and specifically, using the correct branch of our px4-ros-com fork). As a warning, our forks may not be maintained.
    
    <pre>
        <code>
    mkdir -p ~/px4_ros_com_ros2/src
    git clone https://github.com/irom-lab/px4_ros_com.git ~/px4_ros_com_ros2/src/px4_ros_com
    git clone https://github.com/irom-lab/px4_msgs.git ~/px4_ros_com_ros2/src/px4_msgs
    git fetch origin other-python
    git checkout other-python
    cd ~/px4_ros_com_ros2/src/px4_ros_com/scripts
    ./build_ros2_workspace.bash
        </code>
    </pre>
    The build process can take >30 min on the Raspberry Pi 4. Oftentimes, it has an stderr output. However, running <code>./build_ros2_workspace.bash</code> again often corrects this error (in around 1 min).
    </p>
</details><br>

#### Configuring the ROS2 Bridge Topics

One of the advantages of the ROS2 bridge is your ability to communicate across any of the UORB topics. From a Pixhawk 4 shell, you can list all of these topics with `uorb top -1`. They are also listed in the [uORB Message Reference](https://docs.px4.io/main/en/msg_docs/). To enable the bridge, there must be agreement between what the Pixhawk 4 publishes and what the Raspberry Pi 4 subscribes to (and vice versa).

#### Making your first connection over the ROS2 Bridge

Plug your Pixhawk 4 into the Raspberry Pi via USB/microUSB. The mavlink shell is a convenient way to access the Pixhawk 4 shell from the Raspberry Pi to start the micrortps_client.  

First, download the [`mavlink_shell.py`](https://raw.githubusercontent.com/PX4/PX4-Autopilot/main/Tools/mavlink_shell.py) script onto the Raspberry Pi 4. You will have to install pymavlink (`pip3 install --user pymavlink`) before successfully executing the shell.

You can then run the shell and start the client
```
python3 mavlink_shell.py
>nsh micrortps_client start -t UART
```
Back on the Raspberry Pi, start the micrortps_agent to complete the bridge. Remember to source the px4-ros-com workspace in every terminal before using the agent or ros2 commands.
```
source ~/px4_ros_com_ros2/install/setup.bash
micrortps_agent -start t UART
```
You should see a list of the subscribed and published topics that you can send/receive to/from the Pixhawk 4. In a new terminal, you can access some of these topics:
```
source ~/px4_ros_com_ros2/install/setup.bash
ros2 topic list
ros2 topic echo /fmu/vehicle_attitude/out
```

### Offboard Control <a name="offboard-control"></a>

### The MAST and DAQ <a name="mast-and-daq"></a>

### Results <a name="results"></a>