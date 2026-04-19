---
layout: page
title: "THUNDERMILL01: Lightweight EFM"
parent: "Electric field sensors (EFM)"
permalink: /THUNDERMILL/THUNDERMILL01/
has_children: false
nav_order: 10
---

# THUNDERMILL01: Lightweight Portable Electric Field Mill Sensor

The THUNDERMILL01 is an advanced, high-precision electric field mill sensor developed for measuring static and semi-static electric fields. It offers consistent performance in stationary and portable setups in a broad range of meteorological conditions. Its robust design and precise measurement capabilities make it ideal for research institutions, meteorological monitoring, and industrial safety applications.

![THUNDERMILL01 portable mount](https://raw.githubusercontent.com/UniversalScientificTechnologies/THUNDERMILL01/refs/heads/THUNDERMILL01B/doc/img/THUNDERMILL01_stationary.jpg)

## What Does THUNDERMILL01 Measure?

The THUNDERMILL01 sensor measures the strength and approximate direction of atmospheric electric fields. Atmospheric electric fields result from the distribution of electric charges within clouds, between clouds and the Earth's surface, and within hydrometeors. By monitoring these fields, THUNDERMILL01 provides data for the enhancement of understanding storm dynamics, lightning activity, and evaluating the risk of electrical discharges. It is particularly valuable for researchers investigating atmospheric phenomena and seeking insight into the electrical interactions occurring during weather events.

## Applications

For detailed practical examples and operational scenarios, refer to [Use Cases Documentation](./usecases.md).

* **Meteorology:** UAV-based monitoring and atmospheric analysis.
* **Thunderstorm and Weather Research:** Detailed observation of storm-induced electric field variations.
* **Industrial Safety:** Protecting equipment and personnel from electrical discharges.
* **Lightning Warning Systems:** Real-time monitoring for storm-related safety measures.
* **Emergency Management:** Decision support data during severe weather events.
* **Portable Field Studies:** Flexible deployment for temporary measurement campaigns (balloons, drone, cars).

## How Does THUNDERMILL01 Work?

![THUNDERMILL01 woriking principle](Thundermill_sine.webp)

THUNDERMILL01 operates using a rotating shutter mechanism that periodically exposes and shields its sensing electrodes to the atmospheric electric field. This alternating exposure generates an induced charge on the electrodes, measured as a voltage signal (E [V] in the graph). The internal electronics then process these signals to quantify the electric field strength and its variations. The THUNDERMILL01 is unique in capturing a full waveform, which provides extensive data, allowing for advanced analyses such as identifying rapid fluctuations associated with lightning and detailed studies of electrical phenomena within thunderstorms. 

## Key Features

* **Fast Response Rate:** Captures rapid atmospheric phenomena, including lightning.
* **Waveform Capture:** Provides complete waveforms for in-depth event analysis.
* **Real-Time data:** Enable instant processing of atmospheric conditions.
* **GPS Tagging:** Optional time and location tagging of all recorded samples.
* **Open-Source:** Open-source hardware and firmware
* **Portability:** Lightweight design applicable to airborne in-situ measurement.
* **Compliance:** Adheres to [IEEE standard 2819-2022](https://ieeexplore.ieee.org/document/9790051) for electromagnetic environment measurement.

## Technical Specifications

Some technical parameters, like resolution and measurement range, could be customized for the specific application required by the customer. 

| Parameter             |Specification        |
| ------------------------------ | --------------------------------------------------- |
| **Measurement Range**          | ±100 kV/m                         |
| **Resolution**                 | 50 V/m                                               |
| **Accuracy**                   | ±5%                                               |
| **Raw Data**                   | Complete waveform capture                                  |
| **Processed Output**           | Electric field intensity                                          
| **E-Field sampling Rate**     | 25 Hz Typical (Depends on shutter RPM)     |
| **Time resolution**            | 521 us (Corresponds to ADC sample rate)|
| **Time Tagging**               | External Multi-constellation GNSS receiver           |
| **Motor Type**                 | External rotation force (eg. engine, turbine, or popeller rotor)  |
| **Dimensions**                 | Cylindrical; 80x20 mm                       |
| **Mass**                 | 34 grams (without cabling)          |
| **Power Consumption**          | 20 mA@5V + External rotation force (5 W maximum) |
| **Data Interface**       |  UART             |
| **Temperature Range**      | -40°C to 40°C                         |
| **Humidity Range**         | 0–90% RH                                                 |
| **Weatherproof Rating**        | IP03                                              |

## System Architecture

The THUNDERMILL01 system consists of two core components: the sensor unit (EFM) and the terminal unit.

  * The **sensor unit** is responsible for direct electric field measurement using a rotating electrode system. It is designed for outdoor deployment, with internal electronics for signal processing, and environmental protection to withstand harsh conditions.
  * The **terminal unit** serves as the primary interface for configuration, data storage, and communication. It supports real-time visualization, remote access, and integration with external systems. The terminal connects to the sensor via optical or metal-wired links and houses local storage as well as embedded software tools.

This modular architecture allows for flexible deployment in both portable and fixed installations, with high reliability across various atmospheric monitoring scenarios.

## Comparative Analysis

![THUNDERMILL01 test setup](THUNDERMILL01_test_setup.png)

A comparative analysis against conventional sensors (e.g., Boltek EFM-100) has demonstrated significant performance advantages in measurement range, response flexibility, and portability, making THUNDERMILL01 particularly suited for advanced meteorological studies and real-time monitoring scenarios.

![THUNDERMILL01 EFM-100 comparison](EFM-100_THUNDERMILL01_comparison.png)


## Experimental Results

Measurements conducted with THUNDERMILL01 during thunderstorm events have provided insights, notably:

* Enhanced detection and differentiation of atmospheric electric field variations.
* Advanced capability to deduce directional information of electric field sources.

For a discussion of angular‑sensitive electric field mill measurements in thunderstorms, see the paper [Measurements with Angular Sensitive Electric Field Mill in Thunderstorms](https://iopscience.iop.org/article/10.1088/1742-6596/2985/1/012014/pdf).
