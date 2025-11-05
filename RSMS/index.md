---
title: "Radio Storm Monitoring Stations (RSMS)"
layout: page
permalink: /RSMS/
has_children: true
nav_order: 10
---


# Radio Storm Monitoring Stations (RSMS)

The RSMS series consists of research-grade lightning monitoring stations operating in two complementary frequency domains:

| Model               | RF Band            | Indicative Range        | Key features                                       |
| ------------------- | ------------------- | ----------------------- | ------------------------------------------------- |
| [RSMS01](/RSMS01/) | **UHF (~400 MHz)**   |  40-70km         | Active QFH antenna array, GNSS time-stamping, to study detailed structure of lightning breakdown |
| [RSMS02](/RSMS02/) | **VLF (20–500 kHz)** |  100-200km       | Multi-loop antenna array with on-board processing, Trigger, long-range detection and mapping |

> **Low-frequency note:**  
> At VLF and lower bands, the electric and magnetic field components are no longer tightly coupled.  
> For the **electric field**, should be measured using the [THUNDERMILL](/THUNDERMILL/) sensor.  
> For the **magnetic field**, use a magnetometer.
> This separation is a consequence of near-field behaviour, where the wavelength is large compared to the source distance, and E- and H-fields carry different information. In the near-field region (typ. < λ/2π), the E-field is dominated by charge dynamics, while the H-field is dominated by current dynamics. Since they decay differently with distance and are not bound by E/H = Z₀, they provide complementary information and require independent sensors.


## Concept Overview

The RSMS system is designed for multi-band radio detection of lightning. While RSMS02 provides reliable VLF triggering and coarse localization, RSMS01 captures the fine-scale UHF signatures of the lightning events. Both units operate time-synchronously and can be combined for interferometric and correlation analyses with optical, E-field, or radiation sensors.

## Applications

* Coordinated observation of lightning discharges
* Study of spatial and temporal characteristics of leaders
* Multi-band correlation with optical, EFM, or radiation detectors
* Calibration of atmospheric electromagnetic models

## Related Publications

* [In situ ground-based mobile measurement of lightning events above central Europe](https://amt.copernicus.org/articles/16/547/2023/)
* [Detection of Electromagnetic Phenomena in the Atmosphere – Integrating Advanced Instrumentation and UAVs for Enhanced Atmospheric Research](https://dspace.cvut.cz/handle/10467/120570)

