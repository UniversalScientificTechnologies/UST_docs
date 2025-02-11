---
layout: page
title: "Technical description"
parent: "Solar Patrol Telescope"
permalink: /SolarPatrol/TechnicalDescription
has_children: false
nav_order: 1
---
# Technical Description of the System

## Overview

The Solar Patrol Telescope system is designed to support regular solar observations with minimal user intervention. It includes several telescopes, a mount system, control electronics, and a dome control mechanism.

### Main Components

1. **Telescopes:**
   
   - **Refractor 210/3430:** For detailed solar imaging.
   - **Refractor 205/2801:** High-precision observations.
   - **Refractor 150/750:** Full-disc imaging in white light and H-alpha.
   - **Refractor 63/840:** Dedicated for manual solar sketches.
   - Two focus assemblies with large iris shutters.
   - Two small telescope caps.

3. **Telescope Mount:**

   - Equipped with RA (Right Ascension) and DEC (Declination) axes, allowing micro-movements within a limited range.
   - A time axis for tracking solar movement.

4. **Control Electronics:**

   - Built on MLAB electronic modules.
   - Controlled by an Odroid C2 single-board computer.
   - Spare power supply with adjustable voltage and current limits.

5. **Dome Control:**

   - Automated dome rotation controlled via remote signals for the dome's power motor.
   - Manual override via remote controller.

### User interfaces

#### Control Panel

The control panel is located between the telescopes and serves as the main interface for power distribution and system monitoring:

![panel](https://github.com/user-attachments/assets/3a1e4a69-8532-4cd5-b8ad-974dfdb91233)

- **Indicators:**
  - `5V`: Indicates the power status for the control computer.
  - `CPU`: Displays activity of the control computer's processor.
  - `12V`: Confirms the presence of 12V power for the mount system.

- **Switches:**
  - `Motor Power`: Disconnects power to the motor drivers for the mount system.
  - `Electronics`: Isolates power for the control electronics and computer.

- **Additional Features:**
  - Includes an 8-port switch for connecting additional peripherals.

#### Wired Remote Controller

The wired remote controller provides users with direct access to essential control functions. Its features include:

![controler](https://github.com/user-attachments/assets/24ed05ff-fff7-4220-a765-315140323076)


- **Layer System:**
  - Each button can control two functions, toggled between layers.
  - The layer status is indicated by a light: inactive (off) or active (green).

- **Control Functions:**
  - **Group A:**
    - Toggle layer.
    - Rotate dome counterclockwise.
    - Rotate dome clockwise.
    - Enable or disable the time axis.
  - **Groups B, C, D:**
    - `CLONA+`, `CLONA-`: Adjust the iris.
    - `FOCUS+`, `FOCUS-`: Adjust focus.
  - **Group E:**
    - ~~Calibrate or center the mount.~~
    - ~~Mark the current position as the center.~~
  - **Group F:**
    - Set motor speed (1, 2, or 3).
  - **Group G:**
    - Adjust mount position in RA and DEC axes (`DEC+`, `DEC-`, `RA+`, `RA-`).

### Software

The software is based on the open-source frameworks ROS, AROM, and Tornado, primarily written in Python. It manages user interactions through a web interface and wired remote controller, facilitating control of telescope movement, dome operation, and other system elements.

### Connectivity

The system supports both local and remote operations:

- **Local Control:** Wired remote controller for basic operations such as dome movement, focusing, and shutter control.
- **Remote Interface:** Accessible through a web interface for complete system control and monitoring.

## Block Diagram

A visual representation of the system's architecture is provided in the block diagram below:

![patrola-schema](https://github.com/user-attachments/assets/8b50d0cc-56eb-47ff-a7e9-4ba903be955b)


