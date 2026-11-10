---
layout: page
title: "THUNDERMILL02 Raw data format"
parent: "THUNDERMILL02: Rugged EFM"
grand_parent: "Electric field sensors (EFM)"
permalink: /THUNDERMILL/THUNDERMILL02/raw-data-format/
has_children: false
nav_order: 2
has_toc: true
---

# THUNDERMILL02 Raw Data Format
{: .no_toc }

<details open markdown="block">
  <summary>Table of contents</summary>
  {: .text-delta }
1. TOC
{:toc}
</details>

This page describes the data stream sent by the sensor. You need it when using the sensor without the terminal, e.g. connected directly to a computer or a data logger. For the data stored by the terminal, see [Data Storage and Access]({% link THUNDERMILL/THUNDERMILL02_manual.md %}#data-storage-and-access).

The sensor sends its data as a one-way ASCII stream over the RS485 interface (115200 baud, 8 data bits, no parity, 1 stop bit). Each message is one line terminated by a newline. Lines starting with `#` are informational messages (e.g. at startup) and carry no data.

## Identification Header

After power-up, the sensor sends an identification header once, before the data stream:

```
$MILL,THUNDERMILL02,1.0.0-0-CIBuild,0,e8231d3c2643d1be2363cf65275ef62ede0742f1,<serial number>
$ADC,USTEFMADC01B,<serial number>,ffff
```

| Field | Example | Description |
|---|---|---|
| `$MILL` | | Message identifier |
| Model | `THUNDERMILL02` | Sensor model |
| Firmware version | `1.0.0-0-CIBuild` | `<major>.<minor>.<release>-<build>-<build type>` |
| — | `0` | <!-- TODO: meaning of this field --> |
| Git hash | `e8231d3c…` | Firmware source revision |
| Serial number | 32 hex digits | Unique serial number of the sensor |

The `$ADC` line identifies the analog front-end board (model, serial number).

## Waveform Message

The main message carries the signal measured during one revolution of the rotor:

```
32768,32801,32915,…,32790
```

- Comma-separated raw ADC values (16-bit unsigned, 0–65535, printed as 5 digits with leading zeros). The value 32768 corresponds to zero signal.
- The line is terminated by the rotor revolution pulse, so **one line = one rotor revolution**. The number of samples per line depends on the rotor speed (typically ~100).
- The electric field intensity is calculated by the terminal from the waveform (difference of the samples at the exposed and shielded rotor positions, multiplied by a calibration constant).

## Environment Message

Every 10 seconds, the sensor reports the temperature and relative humidity measured inside the sensor housing. The message is sent between two waveform lines:

```
$ENV,,1234.56,21.4,55.2
```

| Field | Example | Description |
|---|---|---|
| `$ENV` | | Message identifier |
| — | (empty) | Reserved field |
| Time | `1234.56` | Time since sensor power-up in seconds (10 ms resolution) |
| Temperature | `21.4` | Temperature in °C |
| Humidity | `55.2` | Relative humidity in % |
