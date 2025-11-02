---
title: "RSMS02 – VLF Radio Storm Monitoring Station"
layout: page
parent: "Radio Storm Monitoring Stations (RSMS)"
permalink: /RSMS02/
nav_order: 4
---

# RSMS02 – VLF Radio Storm Monitoring Station

RSMS02 is a Very Low Frequency (VLF) lightning mapping station designed for detection, recording, and triggering of lightning-related electromagnetic signals. It serves as the low-frequency counterpart to [RSMS01](/RSMS01/), generating triggers for simultaneous UHF recording and enabling synchronized multi-band observation of atmospheric electrical activity.

![Lightning signal receiver RSMS01](https://raw.githubusercontent.com/UniversalScientificTechnologies/RSMS01/refs/heads/RSMS01B/DOC/SRC/img/RSMS01B_receiver.jpg "UHF lightnig signal receiver RSMS01")

## Functional Overview

The station uses a three-axis loop antenna array to capture the magnetic component of VLF emissions from lightning discharges. The loops can be deployed either on a stationary platform or mounted on a vehicle roof for mobile campaigns. Each loop feeds a high-speed digitizer implemented on the [ADCoctoSPI01](https://www.mlab.cz/module/ADCoctoSPI01/) MLAB module, which provides low-noise analog front-end amplification, variable gain control, and high-resolution conversion. The station’s embedded processing unit manages data capture, triggering, and network communication.

![Stationary antenna array](https://raw.githubusercontent.com/UniversalScientificTechnologies/RSMS02/refs/heads/RSMS02A/DOC/SRC/img/mobile_array.jpg "Stationary antenna array on an observatory roof")

<!-- TODO, replace photo
![Mobile antenna array](https://raw.githubusercontent.com/UniversalScientificTechnologies/RSMS02/refs/heads/RSMS02A/DOC/SRC/img/Stationary_array.jpg "Mobile antenna array on a car roof")
-->

The RSMS02 station continuously monitors the VLF spectrum and identifies events using an energy-based algorithm implemented in FPGA logic. When a threshold is exceeded for a defined duration, a TTL trigger pulse is issued to the connected instruments, such as RSMS01 or high-speed optical systems. The triggering mechanism ensures that even short-duration lightning impulses are captured while minimizing false positives from narrowband interference.

## Technical Parameters

| Parameter                           | Typical value / range              | Notes                                 |
| ----------------------------------- | ---------------------------------- | ------------------------------------- |
| **Sampling rate (per channel)**     | 10 MSPS                            | 12-bit resolution                     |
| **Number of channels**              | 3 (orthogonal loops)               | Measures X, Y, Z magnetic components  |
| **Timing source**     | PPS                   | From external GNSS receiver   |
| **Timestamp precision**             | 100 ns                             | GNSS-disciplined clock                |
| **Pre-trigger capture**             | Supported                          | Configurable window length            |
| **Trigger output**                  | TTL compatible                     | Adjustable level and width            |
| **On-board computer**                | Zynq XC7Z01 SoC + Epiphany E16G301 | ARM + parallel coprocessor            |
| **Operating system**                | Linux (Ubuntu)                     | Web and CLI control interface         |
| **RAM / Storage**                   | 1 GB / microSD (typ. 16 GB)        | Data and configuration files          |
| **Network interface**               | 1 Gbit Ethernet                    | Data offload and remote control       |
| **Power input**                     | 9–14.8 V DC                        | Vehicle-compatible                    |
| **Preview latency**                 | ~2 s                               | Depends on configuration              |
| **THD (Total Harmonic Distortion)** | ≈ −65 dBFS                         | Typical at 1 MHz input                |
| **Signal-to-Noise and Distortion Ratio  (SINAD)**                           | ≈ 63 dB                         | Optimal signal conditions       |
| **Input impedance**                 | ≈ 5 kΩ                             | Differential, ~2 pF input capacitance |
| **Input referred noise**            | ≈ 5.5 nV/√Hz                       | At VGA gain = 31 dB                   |
| **VGA gain range**                  | −5 dB to +31 dB                    | Step size 0.125/1 dB                  |


![Station block schamatics](https://raw.githubusercontent.com/UniversalScientificTechnologies/RSMS02/refs/heads/RSMS02A/DOC/SRC/img/RSMS02_receiver.png "Overview of interconnection of station components")


## Front-End and Digitizer

The digitizer module [ADCoctoSPI01](https://www.mlab.cz/module/ADCoctoSPI01/) integrates an eight-channel TI AFE5801 chip, providing variable gain amplifiers and 12-bit ADCs with LVDS output. In RSMS02, three of these channels are used for the orthogonal loop antennas. The analog front-end features fine (0.125 dB) and coarse (1 dB) gain steps, ensuring accurate signal scaling over a wide dynamic range. Signal linearity and low noise make the system suitable for quantitative analysis of electromagnetic field intensity and waveform structure.

To minimize interference, the antenna shields follow a star-ground topology, and the loop outputs are galvanically isolated from the chassis. Each channel maintains consistent phase characteristics for accurate vector reconstruction of lightning directionality.

## System Operation

During operation, the station continuously monitors the incoming magnetic field signals. When the energy content within the configured time window exceeds the threshold, the event is stored locally, and a trigger is propagated to auxiliary devices. Operators can monitor signal levels, trigger thresholds, and data capture via a web-based interface or command-line tools. Data files include binary waveform streams with sidecar metadata that describe timestamping, gain settings, and antenna configuration.

For field deployment, the loop array can be mounted orthogonally on a lightweight frame attached to the roof of a measurement vehicle or on a fixed building. The electronics enclosure is weather-protected, and the system can be powered directly from the vehicle’s DC bus.

## Data Format

Each recording contains:

* Three-channel VLF waveform data (12-bit, 10 MS/s)
* PPS timestamps and internal counters
* Configuration metadata (gain, trigger settings, decimation)

These files can be analyzed using post-processing tools for event classification, correlation with UHF data from RSMS01, or temporal matching with optical and radiation sensors.

## Data Processing and Distributed Lightning Mapping

With a minimum of three RSMS02 stations, it is already possible to reconstruct the location of a lightning discharge using time‑of‑arrival processing of VLF waveforms. An example of such a reconstruction is shown below:

![Example VLF lightning map](https://raw.githubusercontent.com/UniversalScientificTechnologies/RSMS02/refs/heads/RSMS02A/DOC/SRC/img/RSMS02_VLF_lightning_map.png)

This first‑generation map demonstrates the feasibility of locating lightning sources using synchronized VLF recordings. However, the system is designed to enable far more advanced processing. Unlike traditional lightning‑location networks that rely on centralized servers, RSMS02 stations are built as **software‑defined radio receivers with sufficient on‑board compute power** to participate directly in the processing pipeline.

Because both signal bandwidth and required computation scale rapidly with the number of stations, the architecture is intentionally distributed. Individual waveform fragments can be exchanged between stations in the network, allowing cooperative processing and load balancing. Stations that are not in direct range of the event may still contribute their unused compute capacity to perform localization tasks for events recorded elsewhere.

This approach has two main advantages:

1. It keeps the full waveform data accessible to researchers, enabling open and verifiable scientific use rather than a black‑box location service.
2. It removes the scalability limits that affect centralized networks such as Blitzortung.org or similar, where both data bandwidth and compute requirements grow faster than the infrastructure can support.

The long‑term goal is a completely open, peer‑to‑peer lightning mapping network, where any properly synchronized UST's RSMS station can contribute raw waveforms, participate in distributed processing, or run localization and mapping algorithms.

## Related Publications

* [In situ ground-based mobile measurement of lightning events above central Europe](https://amt.copernicus.org/articles/16/547/2023/)

