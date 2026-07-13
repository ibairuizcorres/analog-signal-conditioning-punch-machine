# Analog Signal Conditioning & Control - Scaled Punching Machine

This project covers the design, calculation, and implementation of the power supply, data acquisition, and control system for a scaled industrial punching machine. The development focuses on the electrical and electronic hardware. It solves the problem of measuring a DC motor's current in a noisy environment using analog electronics and digital processing.

## 1. Project Overview

In industrial factories, monitoring motor current is very important to find machine faults and protect the system from overloads. The main goal of this project was to measure the real-time current of the punching machine's motor during its work cycle.

To do this, we designed and built an electronic system with three main parts:
* **Symmetric Power Supply:** A stable ±12V power supply to power the analog components.
* **Signal Conditioning:** Reading the differential voltage from a shunt resistor and amplifying it so a microcontroller can read it.
* **Control Logic:** Processing the signal with an Arduino to monitor the machine and filtering the electrical noise using software.

---

## 2. Technical Specifications

We selected the following hardware components and parameters to make the system accurate:

| System Component | Technical Specification | Primary Role / Range |
| :--- | :--- | :--- |
| **Main Actuator** | Brush DC Motor (12V, 20W) | Drives the mechanical system of the machine. |
| **Shunt Resistor** | 0.1 Ohm Precision Resistor (2A / 200mV HOBUT) | Generates a small voltage proportional to the motor current. |
| **Analog Power Supply** | ±12V Symmetric PSU (regulated from 230V AC) | Provides clean power to the analog amplifiers. |
| **Differential Stage** | AMP03 Difference Amplifier (Gain = 1) | Reads the voltage across the shunt and removes common-mode noise. |
| **Gain Stage** | uA741CP Operational Amplifier (Gain = 25) | Amplifies the analog signal to a 0-5V range. |
| **Control Unit** | Arduino Uno R3 | Reads the analog signal and filters the noise using code. |