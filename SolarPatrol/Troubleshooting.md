---
layout: page
title: "Troubleshooting"
parent: "Solar Patrol Telescope"
permalink: /SolarPatrol/Troubleshooting
has_children: false
nav_order: 10
---


# Troubleshooting

## Calibration Issues

If the mount calibration reaches the edge of its working range, it could be caused by various issues such as interrupted calibration or failure to detect the range limit. To resolve this problem, follow these steps:

1. On the remote controller, press the `Center` button. This action tells the control system that the mount is at the center of its range.
2. Using the RA and DEC movement buttons, manually adjust the mount to the actual center. Repeat this process as needed, as a single press of the `Center` button may not be sufficient.
3. Once the mount is centered, it is highly recommended to restart the calibration process and visually verify its accuracy.

## Time Axis Not Rotating

If the time axis does not rotate:

1. Try enabling the time axis using the remote controller. If this does not work, use the web interface to enable it.
2. Check that the start button in the web interface is highlighted green, indicating it is active.
3. Navigate to the `Mount >> Motor Time` section in the interface and ensure the `SPEED` value is non-zero and the `POSITION` parameter is changing.
4. Manually verify that the motor axis driving the time axis can rotate freely. If the resistance is minimal, proceed with the troubleshooting steps under "Other Problems." If there is significant resistance, the issue may be mechanical.

## Incorrect Time Axis Speed

The speed of the time axis can be adjusted through the web interface:

1. In the `Mount` section, locate the settings button at the bottom.
2. Click on it to open a window with two numerical fields. Enter the absolute speed value and click `Save` to apply the changes.
3. To check the current speed, enable the time axis and find the `SPEED` parameter in the `Motor Time` driver settings menu.

## Other Problems

1. Use the software power switch to shut down the control computer. Wait for the LED indicators to turn off.
2. Disconnect power to the electronics and motors by completing the shutdown process.
3. Wait approximately 20 seconds, then restart the system as described in the main manual.
4. If the issue persists, contact the developers at [info@ust.cz](mailto\:info@ust.cz) or [romandvorak@mlab.cz](mailto\:romandvorak@mlab.cz). Include a detailed description of the problem for faster solving your issue.
5.
