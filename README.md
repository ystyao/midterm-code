# The Breathing Reef

The Breathing Reef is an interactive installation that fuses bio-feedback technology with embodied interaction to create a therapeutic diving experience. 

## Description
Beyond teaching users the physical skill of maintaining neutral buoyancy through controlled breathing, the device serves as a tool for meditation and mental health. By guiding users into deep, rhythmic breathing patterns to navigate a generative 3D ocean environment, the system helps alleviate anxiety, assists individuals with ADHD in improving focus, and regulates emotional fluctuations. Ultimately, the project utilizes high-sensitivity bio-feedback to foster a profound sense of presence, inviting participants to reflect on the synchronicity between human biological rhythms and the complex, generative systems of natural coral ecosystems.

## Visuals
*(Note: It is highly recommended to add images of your physical setup and a GIF of the interaction here)*
![Hardware Setup Placeholder](./assets/hardware_setup.jpg)
![Interaction Demo Placeholder](./assets/demo_video.gif)

## Data Processing & Algorithm
To ensure zero-latency interaction without the heavy computational overhead of traditional ML models, the system processes raw sensor data using a lightweight **Heuristic Temporal Behavioral Model** for real-time motion classification.

The system continuously collects and utilizes the following data points:
* **Absolute Humidity & Temperature:** Captured as environmental baseline data.
* **Humidity Rate of Change ($\Delta H$):** Calculated through a sliding window average to filter out environmental noise and detect actual breath outputs.
* **Respiration Interval:** Time between breaths to monitor user breathing rhythms.

The algorithm features a **"Turbo Start"** burst detection that triggers movement immediately upon significant humidity spikes. Additionally, a **Hysteresis-based state machine** ensures smooth transitions into neutral buoyancy. The dynamic compensation system was "trained" through extensive manual calibration across diverse humidity baselines (from 17% to 49%), ensuring consistent performance regardless of atmospheric conditions.

## Hardware Setup
* Raspberry Pi
* DHT11 Temperature & Humidity Sensor
* I2C LCD1602 Screen
* LED Indicator (Visual Feedback)
* Active Buzzer (Auditory Alert)

## Installation
Use the package manager [pip](https://pip.pypa.io/en/stable/) to install the required dependencies for the sensors and output devices.

```bash
pip install adafruit-circuitpython-dht RPLCD RPi.GPIO