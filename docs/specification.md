--- 
title: General Specification
---

## Component Overview
1.  *(A, B)* **Battery Packs** - 2 x 127Wh
2.  *(A, B, C, D)* **Wheel BLDC Motors**
3. **Power Management Module**
4. **Placeholder for Future Use** - Currently designed to hold a Raspberry Pi 3
5. *(A, B)* **BLDC Motor Drivers** - ODrive v3.6
6. **USB Hub** - 2 x 4 ports
7. **Onboard Computer** - Jetson Nano
8. **Charging Module**

???+ outdated
    Outdated information:
    - Raspberry PI 3 is not planned anymore
    - Onboard computer replacement to ASUS NUC

    Missing:
    - description for battery Packs
    - description for BLDC motors
    - description for power management module
    - description for charging module

### Component Layout

<div class="image-box pins annotate" markdown>
![[firo-layout-top-outline-markings.png]]
<span class="pin pin-big pin-contrast" data-x="0.35" data-y="0.35" markdown> (1) </span>
</div>

1. Onboard Computer

???+ outdated   
    Requires update

**Top View Photo for Reference**

![[firo-top-view.jpg]]

???+ outdated
    Requires update

## **Mechanical Design**
- **Dimensions**: 
  - **Width**: 42.5 cm
  - **Length**: 56.5 cm   
  
  **Additional context**: 
  - The distance between the front and back wheels is equal to the distance between the left and right wheels (wheel track = wheel base = 40cm).   
  - The platform fits within a circle with a diameter of 71cm, allowing it to easily turn, even when passing through a standard door frame (80cm width).  

- **Mobility**: The rover is a 4-wheel differential robot, which means it can turn in place but cannot drive sideways.
- **Wheels**: Each wheel has a radius of 8.25 cm and is powered by an industrial BLDC motor. These motors provide a nominal torque of 2.5 Nm and can peak at 7.5 Nm, operating at 71 rpm nominally. The motors are operated at a higher voltage than nominal (24V), therefore the actual operating speed is higher. 
- **Speed**: The robot is capable of reaching speeds slightly above 1m/s, however, for safety, it is limited to 1 m/s both in rover software and in wheel motor drivers' configuration.  
  
## **Power System**
- **Battery Specifications**: 
    - **Nominal voltage**: 36.4V (10s configuration)
    - **Nominal capacity**: 254 Wh
- **Charging**: At the front of the robot, deployable probes are used for connecting to a custom-made flat charging station. Alternatively, a charger can be manually connected to the XT60 plug located in the power management module.
- **Power Management Module**: Located at the back of the robot, this module is responsible for distributing battery power. Besides directly powering output ports, it includes handling an emergency button, overvoltage and overcurrent protection, and voltage converters (5, 12, and 24V).
  
???+ outdated
    Outdated:
    - power management module description

## **Control and Communication Systems**
- **Onboard Computer**: Jetson Nano
- **Software Framework**: ROS Noetic
- **Periphery Interfaces**:  
    Peripherals can use USB 2, USB 3, or CAN for communication with the onboard computer. Below is outlined what interfaces are currently used by the rover's equipment:
    - **Webcams**: USB 2
    - **Depth camera**: USB 3
    - **360-degree camera**: USB 3
    - **Motor drivers**: USB 2, but in the future will use CAN
    - **Charging module**: Not supported yet, will use CAN
    - **RadCon**: Not supported yet, will use USB 2
- **Motor Drivers**: ODrive v3.6
- **Remote Connectivity**: Wi-Fi 2.4GHz and 5GHz  
  **Additional context**: Standard USB stick antenna is used. High-powered antennas are restricted within FLASH. However, the network coverage is supported by the facility's infrastructure. In areas with weak coverage, a dedicated team works to enhance connectivity.

???+ outdated
    Outdated:
    - onboard computer
    - software framework
