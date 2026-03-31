## Smart Home Appliance Controller ##

A fully  functional embedded systems project that simulates a smart home controller using an Arduino UNO R3 (ATmega328P). The system automatically controls a DC fan based on real-time temperature and humidity readings, with manual override capability, a sleep mode with adaptive lighting, and a safety alarm system.

---

## 📚 Table of Contents

- [Features](#-features)
- [Hardware Components](#-hardware-components)
- [Pin Assignment](#-pin-assignment)
- [Course Concepts Demonstrated](#-course-concepts-demonstrated)
- [State Machine](#-state-machine)
- [Wiring Diagram](#-wiring-diagram)
- [Hardware Photos](#-hardware-photos)
- [Getting Started](#-getting-started)
- [Serial Monitor Output Example](#-serial-monitor-output-example)
- [Additional Information](#-additional-information)

---

## Features
- AUTO mode: Default mode, fan speed automatically adjusts based on temperature (LOW / MEDIUM / FULL / ALARM).
- MANUAL mode: User manually cycles fan speed via a button (OFF / LOW / MEDIUM / FULL).
- SLEEP mode: Fan off, blue LED dims/brightens based on ambient light (smart nightlight).
- ALARM condition: Fan off, buzzer sounds, red LED flashes when temperature exceeds 35°C.
  
- LCD diplay:  Real-time temperature, humidity, and system state.
- RGB LED indicators: Green (AUTO) | Blue (MANUAL) | Dim Blue (SLEEP) | Red (ALARM)
- Light detection: Photoresistor classifies environment as Dark / Dim / Light / Bright / Very Bright. It will show at Serial Moonitor/Console.
  
- Serial logging: Structured data output to PC at 9600 baud

---

## Hardware Components
- 



Florida International University

EEL 4730 - Programming Embedded Systems

Spring 2026

Instructor: Dr. Shafiul Islam

> Youtube link to see the project: https://www.youtube.com/
