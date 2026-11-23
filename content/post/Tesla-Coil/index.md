---
title: "My Tesla Coils"
date: 2022-05-05
description: "Storm, earth and lightning — heed my call!"
slug: my-tesla-coils
categories:
  - Power-Electronics
tags:
  - High-voltage
  - Tesla-Coil
  - Inverter
series:
  - Notes
image: coil.jpg
---

Me and lightning.

This project spanned my middle school and undergraduate years. With each new location, I always wanted to improve the design and build it again.

## Beginning

At first, I just wanted to make a switching power supply. When I came across the NE555 chip, I discovered the mystery of the AC world.

This is a CD4046-based PLL driver.

![](4013.jpg)

So I changed my target and decided to build an inverter. At the same time, I searched for an interesting device that could release over 1,000,000 volts. It was invented by Nikola Tesla.

Of course, the load of my inverter is a Tesla coil. To verify the function of the coil, my first target was to build an SGTC (Spark Gap Tesla Coil).

![](sgtc.jpg)

There is an HV generator and an inverter. At that time I was a junior high school student, so my solution was a classical ZVS inverter plus a CRT line output transformer.

![](zvs1.jpg)

Here is the arc at the output, approximately 15 kV DC.

![](arc.png)

### Gen 1

To replace the spark gap, we need to control the coil artificially with chips and transistors.

All circuits cited from Steve's UD1.3.

Based on 74HC74/74HC08/74HC04.

The isolators are HFBT1414/HFBT2412 ST optical fiber.

The interrupt signal is transmitted through fiber.

![](driver1.jpg)

For the inverter, I chose a full-bridge topology. The IGBT driver used a magnetic isolator (GDT, gate driver transformer, made of Ethernet wire).

![](inverter.jpg)

To control the working duration, I designed an interrupt signal generator based on NE555 and LM393.

![](interrupter.jpg)

Here is the testing site. The MCU is responsible for generating a fake primary working excitation to trigger the D flip-flop.

![](testing.jpg)

And the oscilloscope result.

![](testing2.jpg)

![](testing6.jpg)

This is the current sensor and feedback sensor.

![](sensor.jpg)

Then I mounted the relevant equipment onto the coil.

![](primarycoil.jpg)

![](interrupter.jpg)

Finally, I finished the whole device and decided to test it at home. I made two coils in total based on different calculated parameters. My mom and dad helped me with the winding.

![](test.jpg)

![](coil0.jpg)

![](coil1.jpg)

Actually, the result was not good. I had to change my solution and debug the whole system.

### Gen 2

Following this approach, I reached for the CPLD. Here is the next-generation driver.

The solution is based on a CPLD Altera MAX II, which integrated the whole gate circuit into one chip.

The new GDT driver uses P-N MOSFETs FDD8424H instead of the IRFP540/9540 totem-pole MOS amplifier.

![](driver2.jpg)

This time I recalculated the resonance parameters, taking into account the conclusions of enthusiasts in other parts of the world.

![](testing3.jpg)

This time the result was very significant. According to the calculation, the resonant current has reached 100 A, while the IGBT is rated at 50 A.

In order to keep using the previous secondary coil and get better results, I set out to improve a new generation of inverters, this time with 5 IGBTs in parallel per arm.

![](inverter2.jpg)

I tested the coil at my home and at my high school.

![](testing4.jpg)

![](testing5.jpg)

## Twisting

As time went by I entered university. Because of some trivial matters, I could not concentrate on higher-power testing, so I switched to optimization design.

Here is the new-generation driver based on a CPLD Xilinx CoolRunner II.

On this board, I tried to design some protection circuits and a faster PWM signal in the CPLD — such as a phase-shift circuit to protect the IGBT.

I also added an isolated IGBT driver through fiber instead of a gate driver transformer (GDT).

![](driver3.jpg)

The new platform in my lab.

![](coil4.jpg)

This time I tried to use IGBT modules to build the full-bridge inverter.

![](inverter3.jpg)

But it did not last long. The program was quickly suspended by the school and terminated after my lobbying was ineffective.

## Rebirth

Restart, new life...

I still remember when I was in my third year of junior high school, my dad gave me 3,000 RMB to realize my dream. That year I built an oversized IGBT inverter. But the lack of theoretical knowledge meant I never successfully and safely drove this big guy.

![](inverter5.jpg)

These are the resonant capacitors prepared at that time.

![](cap1.jpg)

And this is the secondary coil prepared at that time.

![](coil.jpg)

Before my graduation defense, I was reminded again of my childhood aspirations, so I redesigned the driver circuit. The new driver is based on an Infineon Cypress PSoC, which integrates an FPGA, PGA and ARM.

After that, I developed a GUI based on Node.js. It is a digital operation panel with various sensor data.

![](teslanode.jpg)

I hope that someday I can actually finish and close this ten-year project!
