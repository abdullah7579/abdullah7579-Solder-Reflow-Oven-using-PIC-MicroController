# PIC18F458-Based Solder Reflow Oven Controller

This project presents the design and implementation of a cost-effective embedded control system for a basic solder reflow oven using a PIC18F458 microcontroller. The system monitors and regulates the thermal environment to match a standard four-stage temperature-time reflow profile (Preheat, Soak, Reflow, and Cooling).

## ⚙️ Core System Architecture
* **Temperature Sensing:** Uses a thermocouple paired with a MAX6675 sensor via a software-implemented SPI interface.
* **Setpoint Management:** A Timer0 interrupt triggers every 5 seconds to cycle through an array of 48 distinct temperature setpoints.
* **Actuator Control:** A single proportional-controlled PWM output alternately manages a DC heating element and a cooling fan.
* **Hardware Safety Logic:** Interlocks using discrete logic gates (AND, NOT) and IRF540N MOSFETs prevent simultaneous actuator operation.
* **Real-Time Monitoring:** Sends live temperature values over a UART serial interface to a Python script for real-time Matplotlib graphing.

## 🛠️ Hardware Requirements
* Microcontroller: PIC18F458 (with an 8 MHz Crystal oscillator)
* Thermal Interface: MAX6675 Digital Sensor + K-Type Thermocouple
* Power Stage: IRF540N Power MOSFETs & 1N4007 Flyback Diodes
* Actuators: DC Heater & DC Cooling Fan
* Safety Matrix: Standard TTL Logic Gates (AND / NOT)

## 🚀 How It Works
The main operational cycle is strictly interrupt-driven. When Timer0 flags an interrupt, the MCU reads the current oven temperature from the MAX6675, checks it against the 5-second setpoint index, and recalculates the required PWM duty cycle. The hardwired logic gates route the single PWM stream to either the heater or fan, enforcing mutual exclusivity. Simultaneously, the metrics are pushed to the UART data bus to update the localized performance curve on a connected workstation.
