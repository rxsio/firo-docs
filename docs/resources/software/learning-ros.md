---
title: Learning ROS

version: 1.0.0
date: 12.09.2024
authors:
  - Gabriel Brzeziński, gabriel@gabrielb.dev
---

## Prerequisites

Before diving into ROS, it's highly recommended that you have practical experience with the following:

- Git
- Python or C++ programming
- Working with Linux, especially Ubuntu

If you're lacking in any of these areas, consider brushing up through resources like [git - the simple guide](https://rogerdudler.github.io/git-guide/). If you're unfamiliar with more than one of these tools, it might be worth dedicating some time to thoroughly study each topic. For newcomers to programming, we suggest learning Python first—it’s more approachable than C++ and better suited for grasping basic programming concepts.

We recommend using **VSCode** as your IDE, as it’s the preferred option for working on the FIRO project.

For Linux beginners, we suggest installing Ubuntu 22.04 natively on your system. Be cautious when setting up dual-boot with Windows to avoid wiping out your other operating system. Alternatively, if you're on Windows 11, you can use **WSL (Windows Subsystem for Linux)**, though it might require extra troubleshooting for GUI applications like RVIZ or Gazebo. Regardless of your installation method, stick with Ubuntu 22.04, as neither older nor newer versions are compatible with ROS2 Humble, which we use for FIRO.

## Installing ROS and Setting Up the Environment

While we've prepared a dedicated ROS workspace for FIRO, I recommend not using it right away. Start by following the official ROS guides and [install ROS2 Humble natively](https://docs.ros.org/en/humble/Installation/Ubuntu-Install-Debs.html). Do a full desktop installation (`ros-humble-desktop`), then move on to [configuring your environment](https://docs.ros.org/en/humble/Tutorials/Beginner-CLI-Tools/Configuring-ROS2-Environment.html).

## Beginner Tutorials

The official [ROS 2 tutorials](https://docs.ros.org/en/humble/Tutorials.html) are excellent for getting started. Begin with [Beginner: CLI Tools](https://docs.ros.org/en/humble/Tutorials/Beginner-CLI-Tools.html), but skip the sections on **Understanding Services** and **Understanding Actions** for now, as they can be overwhelming for newcomers. You'll learn about them when they become necessary.

Next, move on to [Beginner: Client Libraries](https://docs.ros.org/en/humble/Tutorials/Beginner-Client-Libraries.html). Again, skip **Writing a Simple Service and Client**, **Creating and Using Plugins**, and only focus on the message-related parts in **Creating Custom Msg and Srv Files**, ignoring services.

Finally, go to the [Intermediate Tutorials](https://docs.ros.org/en/humble/Tutorials/Intermediate.html) and complete:

- **Managing Dependencies with rosdep**
- **Launch Files** (choose either XML or YAML syntax)

## Moving Forward

Once you've completed these tutorials, you’ll be ready to dive into FIRO development. For the next steps, head over to [[writing-ros-packages.md]], where you'll learn how to set up the recommended development environment for ROS2 FIRO packages and explore our coding standards and guidelines.
