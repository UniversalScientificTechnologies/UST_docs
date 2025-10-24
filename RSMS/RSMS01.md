---
title: "RSMS01 – UHF Radio Storm Monitoring Station"
layout: page
parent: "Radio Storm Monitoring Stations (RSMS)"
permalink: /RSMS01/
nav_order: 1
---

# RSMS01 – UHF Radio Storm Monitoring Station

RSMS01 is a UHF lightning observation station designed for ground or vehicle-mounted deployments. It complements the [RSMS02](/RSMS02/) VLF receiver, which provides triggering and coarse detection. Together, both instruments capture long, contiguous, and time-synchronized RF segments of lightning activity for detailed post-processing. The system was conceived for research applications requiring high temporal accuracy and wide dynamic range, allowing detailed analysis of lightning structure and propagation.

## Functional Overview

The receiver operates in the UHF band around 400 MHz, providing a contiguous 10 MHz capture window. This band is particularly rich in signatures of the initial lightning breakdown and leader formation, offering complementary information to lower-frequency systems. Each RSMS01 station combines a four-element antenna array, active front-end modules, and a base unit with high-speed digitizers. Signals from the antennas are fed as differential I/Q pairs over shielded CAT6 cabling, ensuring low noise and excellent channel synchronization even during mobile operation.

During operation, the VLF station (RSMS02) detects strong electromagnetic impulses associated with lightning and sends a trigger to RSMS01. The UHF station then preserves a selected time segment of the continuous radio stream — typically about 1.45 seconds — including data both before and after the trigger. Embedded GNSS-derived time marks make it possible to align individual samples with absolute UTC, which enables cross-correlation with optical, electric-field, or radiation sensors.

## Technical Parameters

| Parameter             | Typical value / range      | Notes                                 |
| --------------------- | -------------------------- | ------------------------------------- |
| **Frequency band**    | 370–406 MHz                | Tunable within local RFI constraints  |
| **Sampling rate**     | 10 MSPS                    | 12‑bit resolution per I/Q channel     |
| **Capture bandwidth** | 10 MHz I/Q complex         | Contiguous spectrum segment           |
| **Recording length**  | up to 1.45 s per event      | Configurable pre/post number of blocks        |
| **Timing source**     | GNSS PPS                   | nanosecond‑class absolute accuracy   |
| **Trigger input**     | TTL from RSMS02            | Adjustable level and pulse width      |
| **Antenna type**      | 4× QFH (Quadrifilar Helix) | Circularly polarized, omnidirectional |
| **Data transport**    | CAT6 differential pairs    | 100 Ω, low‑noise I/Q link             |
| **Power supply**      | 9–15 V DC                  |  Car plug compatible           |

## RF Front-End and Antenna Array

Each antenna element is equipped with an active front-end that includes a chain of band‑pass filters and low‑noise amplifiers for improved dynamic range. The down‑conversion stage uses a high‑linearity mixer with low‑jitter local oscillator distribution, followed by an anti‑alias low‑pass filter (≈ 5 MHz) and differential line driver. All components are enclosed in aluminum housings to provide effective electromagnetic shielding.

The four QFH antennas are arranged on a rigid, non‑conductive deck, such as a vehicle roof platform or mast mount. Their circular polarization and wide‑angle response make the system suitable for capturing impulsive radio emissions regardless of lightning orientation.

## System Operation

Before measurement, the antennas and active front‑ends are assembled and connected to the base unit. After powering up, the operator configures the VLF trigger levels in RSMS02 and starts monitoring. Once the trigger system is validated, the UHF recorder begins capturing radio bursts. Real‑time visualization can be performed using [fosphor](https://osmocom.org/projects/sdr/wiki/fosphor), which provides a live spectrum or waterfall view for verifying signal quality and interference conditions.

## Data Format

Each recorded event consists of:

* Four per‑element I/Q streams (12‑bit, 10 MS/s, 10 MHz complex bandwidth)
* PPS time marks and sample indices for UTC reconstruction
* Trigger metadata (VLF detection parameters)

The data can be processed offline for interferometric or correlation analysis, allowing reconstruction of lightning event geometry and timing with high precision.

## Related Publications

* [In situ ground-based mobile measurement of lightning events above central Europe](https://amt.copernicus.org/articles/16/547/2023/)
* [Detection of Electromagnetic Phenomena in the Atmosphere – Integrating Advanced Instrumentation and UAVs for Enhanced Atmospheric Research](https://dspace.cvut.cz/handle/10467/120570)

