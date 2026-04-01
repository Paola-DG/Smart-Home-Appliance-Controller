# Smart Home Appliance Controller
![Arduino](https://img.shields.io/badge/Arduino-UNO%20R3-00979D?style=flat&logo=arduino)
![Language](https://img.shields.io/badge/Language-C%2B%2B-blue?style=flat&logo=cplusplus)
![Course](https://img.shields.io/badge/FIU-EEL4730-blue?style=flat)

Modern homes rely on embedded systems to automate appliances and improve energy efficiency. This project presents a fully functional smart home appliance controller built on an Arduino UNO R3 (ATmega328P — Harvard architecture, 8-bit RISC microcontroller), designed to automatically manage a DC fan based on real-time environmental conditions.

The system reads temperature and humidity from a DHT11 digital sensor and ambient light levels from a photoresistor (ADC), then responds by controlling a DC fan motor through PWM, visual RGB LED state indicators, an LCD1602 display, and a safety buzzer alarm — all communicating status to a PC via UART serial output.

The hardware-software integration is achieved through direct peripheral register control: GPIO pins manage buttons and LEDs, the PWM module controls fan speed proportionally to temperature, the ADC converts analog light levels to digital values, and a state machine governs system behavior across four operating modes — AUTO, MANUAL, SLEEP, and ALARM. A safety countermeasure automatically shuts down the fan and triggers an alarm when temperature exceeds 35°C, mirroring real-world embedded safety systems used in home appliances and HVAC controllers.

---

## 📚 Table of Contents

- [Features](#features)
- [Hardware Components](#hardware-components)
- [Pin Connections](#pin-connections)
- [Course Concepts Demonstrated](#course-concepts-demonstrated)
- [State Machine](#state-machine)
- [Wiring Diagram](#wiring-diagram)
- [Hardware Photos](#hardware-photos)
- [Getting Started](#getting-started)
- [Serial Monitor Output Example](#serial-monitor-output-example)
- [Additional Information](#additional-information)

---

## Features
- AUTO mode: Default mode, fan speed automatically adjusts based on temperature (LOW / MEDIUM / FULL / ALARM).
- MANUAL mode: User manually cycles fan speed via a button (OFF / LOW / MEDIUM / FULL).
- SLEEP mode: Fan off, blue LED dims/brightens based on ambient light (smart nightlight).
- ALARM condition: Fan off, buzzer sounds, red LED flashes when temperature exceeds 35°C.
  
- LCD display:  Real-time temperature, humidity, and system state.
- RGB LED indicators: Green (AUTO) | Blue (MANUAL) | Dim Blue (SLEEP) | Red (ALARM)
- Light detection: Photoresistor classifies environment as Dark / Dim / Light / Bright / Very Bright. It will show at Serial Monitor/Console.
  
- Serial logging: Structured data output to PC at 9600 baud

---

## Hardware Components
| Component               | Purpose                          |
|-------------------------|----------------------------------|
| Elegoo UNO R3           | Main microcontroller             |
| 830-point breadboard    | Prototyping platform             |
| DHT11                   | Reads temp and humidity          |
| Photoresistor (LDR)     | Ambient light detection          |
| DC Fan Motor            | PWM-controlled fan               |
| Active buzzer           | Alarm output                     |
| x3 RGB LED              | Visual state indicator           |
| LCD1602 display         | Live sensor readings             |
| PN2222 transistor       | Fan motor driver                 |
| 1N4007 flyback diode    | Motor protection                 |
| 2x Push buttons         | Mode and speed control           |
| 10kΩ resistor           | Ambient light detection          |
| 1kΩ resistors           | Transistor base resistor         |
| 3x 220Ω resistors       | LED current limiting             |

---

## PIN Connections
| Arduino PIN             | Component                          |
|-------------------------|------------------------------------|
| PIN 2                   |  Mode Button (INPUT_PULLUP)        |
| PIN 3                   |  Speed Button (INPUT_PULLUP)       |
| PIN 6                   |  Active buzzer                     |
| PIN 7                   |  RGB LED Red                       |
| PIN 8                   |  RGB LED Green                     |
| PIN 10                  |  RGB LED Blue                      |
| PIN 11                  |  Fan Motor PWM                     |
| PIN 13                  |  DHT11 data                        |
| PIN A0                  |  Photoresistor ADC input           |
| PIN A1                  |  LCD D7                            |
| PIN A2                  |  LCD RS                            |
| PIN A3                  |  LCD EN                            |
| PIN A4                  |  LCD D4                            |
| PIN A5                  |  LCD D5                            |
| PIN 12                  |  LCD D6                            |

---

## Course Concepts Demonstrated
- ADC: Photoresistor on A0, analogRead() returns 0–1023.
- PWM: Fan speed and LED brightness via analogWrite().
- GPIO: Buttons (input), LEDs, Buzzer (output).
- Timers: delay(2000), periodic DHT11 sampling.
- UART: Serial.begin(9600), structured data to PC terminal.
- State Machine: AUTO | MANUAL | SLEEP | ALARM with modeState.
- Digital sensor: DHT11 single-wire protocol.
- Analog sensor: LDR voltage divider to ADC conversion.
- Hardware interfacing: PN2222 transistor driving DC motor from GPIO.
- Countermeasure: Fan OFF and  alarm at 35°C safety threshold.
- Harvard architecture: ATmega328P separates Flash (program) and SRAM (data), same principle as PIC18F4520.

---

## State Machine
    Power ON → AUTO
    Button 1 press → AUTO → MANUAL → SLEEP → AUTO (cycles)

    AUTO:   Fan responds to temperature automatically
    MANUAL: Button 2 cycles fan OFF → LOW → MEDIUM → FULL
    SLEEP:  Fan off, blue LED brightness adapts to ambient light
    ALARM:  Triggered when temp >= 35°C — fan off, buzzer ON, red LED

---

## Wiring Diagram


---

## Hardware Photos

---

## Getting Started
### Prerequisites
  -  Arduino IDE
  -  DHT11 library: install via Sketch → Include Library → Manage Libraries → search DHT11 (by Dhruba Saha)
  -  LiquidCrystal library: built into Arduino IDE

### Upload
  1) Clone this repository;

    git clone https://github.com/Paola-DG/smart-home-appliance-controller.git
  2) Open SmartHomeAppliance.ino file in Arduino IDE.
  3) Select board: Arduino UNO.
  4) Select correct COM port.
  5) Click Upload.
  6) Open Serial Monitor at 9600 baud.

---

## Serial Monitor Output Example
    Smart Home Appliance Control System
    EEL4730 - FIU
    Temperature: 23C | Humidity: 55%
    Light Detection. Enviroment Lighting is Light
    Fan Motor: LOW speed
    MODE: MANUAL
    Manual Fan: MEDIUM
    MODE: SLEEP
    MODE: AUTO
    Fan Motor: FULL speed
    Fan Motor: OFF --- ALARM!! ---
    BUZZER: ON

---

## Additional Information

Florida International University

EEL 4730 - Programming Embedded Systems

Spring 2026

Instructor: Dr. Shafiul Islam

> Youtube link to see the project: https://www.youtube.com/
