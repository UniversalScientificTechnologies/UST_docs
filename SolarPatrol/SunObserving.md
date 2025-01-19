---
layout: page
title: "Sun observing"
parent: "Solar Patrol Telescope"
permalink: /SolarPatrol/SunObserving
has_children: false
nav_order: 3
---

# SOLAR Observing
This page focuses on the scientific aspects of solar observation. It describes how to configure hardware and software to perform specific types of observations, such as sketching the Sun and photographing full solar disks.

## Drawing Solar Sketches

### Preparing for Sketching

1. **Position the Dome:**
   - Rotate the dome so that the slit aligns with the Sun.
   - Use the wired remote controller or the web interface for precise alignment.

2. **Setup the Drawing Telescope:**
   - Remove the cap from the drawing telescope.
   - Place the observation sheet on the edge of the Sun's eastern side and secure it with magnets.

3. **Center the Sun:**
   - Use the remote controller to adjust the Sun's position on the observation sheet.
   - Switch to the second layer (`green mode`) on the controller for fine adjustments using the dedicated movement buttons.

4. **Improve Contrast:**
   - Partially close the dome to reduce excessive light and enhance contrast.

### Making the Sketch

1. **Draw Sunspots:**
   - Use a pencil to mark sunspots on the observation sheet.

2. **Draw Faculae:**
   - Highlight facular regions with an orange pastel pencil.

3. **Final Check:**
   - Ensure the sketch accurately represents the Sun's observed features.

---

## Capturing Full Solar Disks

### Preparing for Photography

1. **Open telescope Web Interface:**
   - Open the Solar Patrol Telescope control interface.

2. **Control Shutters and Mount:**
   - Open the telescope shutters using the `patrola_caps` tab.
   - Adjust the mount and enable automatic dome rotation.

### Setting Up the Cameras

1. **Connect Cameras:**
   - Verify camera connections in the SharpCap application.
   - Reconnect cables if the camera is not detected.

2. **Create Directories:**
   - On the observation computer, create folders named `hasnYYYYMMDDa` (chromosphere) or `wlsnYYYYMMDDa` (photosphere).
     - Replace `YYYYMMDD` with the current year, month, and day.

3. **Check Camera Settings:**
   - Ensure the following settings are applied:
     - Mode: `MONO16`
     - Binning: `1`
     - Output: `FITS files`
     - Gain: `0`
     - Frame Rate: `8 fps`

### Capturing Images

1. **Start the Capture Process:**
   - For chromosphere imaging, set capture mode to `Unlimited` and begin recording.
   - For photosphere imaging, set the frame count to `30` and capture hourly.

2. **Monitor Dome Movement:**
   - Check that the dome follows the Sun's path. Adjust manually if required.

3. **End the Capture:**
   - Stop the capture using the `Stop Capture` button.


## Closing Procedures

1. **Shut Down the Cameras:**
   - Close all active sessions in SharpCap.

