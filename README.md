# Analog Signal Conditioning & Control - Scaled Punching Machine

This project covers the design, calculation, and implementation of the power supply that feeds a data acquisition and control system for a scaled industrial punching machine. The development focuses on the electrical and electronic hardware. It solves the problem of measuring a DC motor's current in a noisy environment using analog electronics and digital processing.

<p align="center">
  <img src="4_Media/punching_machine_prototype.jpg" alt="Scaled Punching Machine Prototype" width="40%">
</p>

## Project Context & My Role

This project was a multidisciplinary team challenge. The main objective was to design and build a fully functional, scaled prototype of an industrial punching machine. The project integrated several engineering fields:
* **Mechanical Design:** Creating the 3D model in SolidWorks and optimizing the structure.
* **Materials & Physics:** Studying cutting forces, shear strength, and calculating tool wear in MATLAB.
* **Signal Analysis:** Capturing and analyzing machine vibrations using Fourier Transforms (FFT) in MATLAB.
* **Electrical & Control:** Designing the power supply, analog conditioning circuits, and programming the microcontrollers.

### My Specific Contribution
To work efficiently as a group, we divided the tasks based on our technical strengths. **My role was to lead and develop the complete electrical, electronic, and control subsystems (which represented 90% of my personal workload in this project).**

While my teammates focused on the mechanical frames, material tests, and vibration analysis, I took full responsibility for the power delivery, analog circuit design, and Arduino programming. This portfolio documents my specific engineering work and decisions in these areas.

---

## 1. Project Overview

In industrial factories, monitoring motor current is very important to find machine faults and protect the system from overloads. The main goal of this project was to measure the real-time current of the punching machine's motor during its work cycle. In this case, the objective of measuring the current was to stop the machine if the power exceeds a safe limit. This current is read by an Arduino Uno R3, which controls a relay to switch the motor on or off. Additionally, the project required the possibility to change the motor's rotation direction. This specific part will be explained in broad strokes because it was a shared task with my team.

To do this, I designed and built an electronic system with three main parts:
* **Symmetric Power Supply:** A stable ±12V power supply. The +12V rail powers the DC motor and the positive analog rail, while the -12V rail is used for the negative analog rail of the operational amplifiers.
* **Signal Conditioning:** Reading the differential voltage from a shunt resistor and amplifying it so the microcontroller can read it and make control decisions based on this measurement.
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