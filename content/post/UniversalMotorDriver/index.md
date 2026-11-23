---
title: "Universal Driver"
date: 2022-03-13
description: "Beginning."
slug: universal-driver
categories:
  - Motor-Driver
tags:
  - motor
series:
  - Notes
image: stm.jpg
---

# In Development...

Building a modular general-purpose motor driver with support for various algorithms, complete protection, multiple sensors, signal outputs and oscilloscope access.

---

- Isolated op-amps
- Isolated power supplies
- AS2S1210
- AD7401 (bus voltage, three-phase current)
- Zynq
- Input voltage 10–60 V
- Input current 80 A
- 3.3 V 20 A rail (tested with PW22 and ZXD10)
- 5 V 8 A rail
- TLV62130 / TPS51200 quad power and DDR
- RTL8211 network PHY ×2
- FT2232 JTAG
- MAX232 RS232 architecture
- Isolated CAN?
- HDMI PHY?
- Connectors
- Differential encoder receive
- Encoder input optical isolation
- Reserved resolver position
- Encoder signal input MUX
- CPLD 12-channel PWM protection
- AD7124-8 temperature, phase voltage, bus voltage
- AD7124
- STM32 functions
- Four-way voltage protection; all four outputs leave a test point
- Bus voltage protection (bus voltage resistor network leaves a test point, then connects two voltage followers: one into the CPU, one into the south bridge, leaving a test point) (low-voltage bus board uses PMOS; high power uses an AC contactor)
- Temperature protection (read via 7124)
- Hard overcurrent protection with a comparator and op-amp; STM32 outputs PWM through a second-order filter

(Later these functional requirements were realized with an FPGA; the protection logic no longer involves software.)
