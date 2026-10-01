# 10 MHz STM32 Digital Oscilloscope

A custom-designed digital oscilloscope based on the **STM32H723ZGT6**
microcontroller and **AD9226 12-bit ADC**.

The project is designed as a compact standalone oscilloscope with a
high-speed analog front-end, selectable relay-based input attenuation,
parallel ADC acquisition and an SPI TFT display.

> ⚠️ **Project status:** Work in progress  
> Hardware is currently in the PCB design / manufacturing stage.
> Firmware development and hardware validation are ongoing.

---

## Overview

The main goal of this project is to design a digital oscilloscope
completely from scratch — including the analog front-end, ADC interface,
power supply, relay control, PCB and firmware.

The oscilloscope architecture is based around:

- STM32H723ZGT6 MCU
- AD9226 12-bit ADC
- AD8132 differential ADC driver
- OPA356 high-speed operational amplifier
- Relay-based input attenuation
- STM32 PSSI parallel data interface
- 2.4" 240×320 SPI TFT display
- USB Type-C interface
- Separate analog and digital power domains

The target measurement bandwidth is **up to 10 MHz**.

---

## Main Specifications

| Parameter | Value |
|---|---|
| MCU | STM32H723ZGT6 |
| ADC | AD9226 |
| ADC resolution | 12-bit |
| Target bandwidth | Up to 10 MHz |
| ADC interface | 12-bit parallel |
| MCU acquisition interface | PSSI |
| ADC driver | AD8132 |
| High-speed amplifier | OPA356 |
| Input attenuation | ×1 / ×10 / ×20 |
| Input attenuation switching | Relays |
| Display | 2.4" 240×320 TFT |
| Display interface | SPI |
| Input connector | BNC |
| USB connector | USB Type-C |
| Relay supply | Isolated 5 V |
| Isolated DC/DC | B0505S-2W |
| User controls | 4 buttons |

> The target bandwidth is a design objective. Final performance
> characteristics such as bandwidth, SNR, ENOB and sampling performance
> will be determined experimentally after hardware validation.

## System Architecture

Input → Protection → Attenuator → Analog Front-End → Differential Driver → AD9226 (12-bit ADC) → PSSI → DMA → STM32H723ZGT6 → TFT Display