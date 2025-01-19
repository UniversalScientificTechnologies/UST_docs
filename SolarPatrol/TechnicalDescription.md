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

2. **Telescope mount:**

   - Equipped with RA (Right Ascension) and DEC (Declination) axes, allowing  micro-movements within a limited range.
   - A time axis for tracking solar movement.

3. **Control Electronics:**

   - Built on MLAB electronic modules.
   - Controlled by an Odroid C2 single-board computer.
   - Spare power supply with adjustable voltage and current limits.

4. **Dome Control:**

   - Automated dome rotation.
   - Manual override via remote controller.

### Software

The software is based on the open-source frameworks ROS, AROM, and Tornado, primarily written in Python. It manages user interactions through a web interface and wired remote controller, creates simple control of telescope movement, dome operation, and other system elements.

- **Key Features:**
  - Manages user interaction through interfaces like the web page and wired remote controller.
  - Handles the control of movable elements, including telescope axes and the dome.
  - Facilitates remote monitoring and commands through a web interface.

### Connectivity

The system supports both local and remote operations:

- **Local Control:** Wired remote controller for basic operations such as dome movement, focusing, and shutter control.
- **Remote Interface:** Accessible through a web interface for complete system control and monitoring.

##

