# 💧📡 IoT Based Smart Water Leakage Detection System

> Real-time dual flow monitoring and automatic water leakage control using ESP32 and Blynk.

---

## 📌 Overview

This project is an IoT-based Smart Water Leakage Detection System developed using **ESP32**, two **water flow sensors**, **Blynk IoT platform**, and a **relay-controlled pump mechanism**.

The system compares the water flow at the inlet and outlet of a pipeline. If a difference in flow rate is detected beyond a threshold, it identifies it as leakage and automatically shuts off the water supply while sending a notification to the user.

---

## 🚀 Key Features

* 💧 Dual flow sensor comparison
* 📊 Real-time flow monitoring
* 📱 Blynk mobile app integration
* 🚨 Automatic leakage detection
* 🔌 Relay-based automatic pump shutoff
* 🔔 LED leakage indication
* 📟 LCD live display
* 📡 WiFi-based IoT monitoring

---

## 🛠️ Hardware Components

* ESP32 Development Board
* 2 × Water Flow Sensors (YF-S201 or similar)
* 16x2 I2C LCD Display
* Relay Module
* LED Indicator
* Water Pump / Solenoid Valve
* Power Supply

---

## ⚙️ Working Principle

1. Two flow sensors are installed at the inlet and outlet of the pipeline.
2. Each sensor generates pulses proportional to water flow.
3. ESP32 counts pulses using interrupts.
4. Flow rate is calculated every second.
5. Data is:

   * Displayed on LCD
   * Sent to Blynk App
6. If outlet flow is significantly lower than inlet flow:

   * Leakage is detected
   * Relay turns ON (stopping pump)
   * LED turns ON
   * Blynk notification is sent

---

## 🔄 Leakage Detection Logic

Leakage condition:

```
if (flowRate2 < flowRate1 && flowRate2 < 8)
```

This ensures:

* Output flow is less than input flow
* Flow drop is significant enough to indicate leakage

---

## 📱 Blynk Configuration

* V0 → Flow Sensor 1 Data
* V1 → Flow Sensor 2 Data
* Event Name → "flow_notify"
* Add 2 Gauge Widgets
* Enable Push Notifications

---

## 📊 System Architecture

```
Flow Sensor 1 → ESP32 → LCD
                    ↓
Flow Sensor 2 → ESP32 → Blynk App
                    ↓
               Relay Control
                    ↓
                Water Pump
```

---

## 📂 Project Structure

```
Smart-Leakage-Detection/
│
├── code/
│   └── leakage_system.ino
├── images/
├── circuit/
└── README.md
```

---

## 📌 Applications

* Apartment water systems
* Industrial pipelines
* Underground water supply monitoring
* Smart buildings
* Irrigation systems

---

## 🔮 Future Enhancements

* GSM-based SMS alerts
* Cloud data logging
* Pressure sensor integration
* AI-based leakage prediction
* Multi-zone monitoring
