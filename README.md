# SIT210 Task 3.3D – MQTT Wave & Pat Detector

This project demonstrates an IoT-based **Wave and Pat detection system** using Arduino Nano 33 IoT and MQTT protocol. The system reads sensor input, detects user gestures, and sends updates via MQTT to a cloud service.

This README provides a step-by-step guide to set up, run, and test the task.

---

## Table of Contents

1. [Prerequisites](#prerequisites)
2. [Hardware Setup](#hardware-setup)
3. [Software Setup](#software-setup)
4. [Folder & File Structure](#folder--file-structure)
5. [Configuration Steps](#configuration-steps)
6. [Running the Program](#running-the-program)
7. [Testing & Expected Behavior](#testing--expected-behavior)
8. [Troubleshooting](#troubleshooting)

---

## Prerequisites

Before starting, ensure you have the following:

* **Hardware:**

  * Arduino Nano 33 IoT
  * Ultrasonic sensor (for wave detection)
  * Force sensor or touch sensor (for pat detection)
  * LED or buzzer (optional, for feedback)
  * Jumper wires and breadboard

* **Software:**

  * Arduino IDE (latest version)
  * Arduino Nano 33 IoT board package installed
  * Libraries: `WiFiNINA`, `ArduinoMqttClient`

* **Account & Service:**

  * Access to an MQTT broker (Arduino Cloud or other MQTT service)
  * Wi-Fi network credentials (SSID & password)

---

## Hardware Setup

1. Connect the **ultrasonic sensor** to the Arduino:

   * VCC → 3.3V
   * GND → GND
   * TRIG → Digital Pin 2
   * ECHO → Digital Pin 3

2. Connect the **force/touch sensor**:

   * VCC → 3.3V
   * GND → GND
   * Signal → Analog Pin A0

3. Optional: Connect **LED** for visual feedback:

   * Positive → Digital Pin 4
   * Negative → GND

---

## Software Setup

1. Open **Arduino IDE**.
2. Install the required libraries via **Library Manager**:

   * `WiFiNINA`
   * `ArduinoMqttClient`
3. Connect your **Arduino Nano 33 IoT** via USB.
4. Select **Board → Arduino Nano 33 IoT** and the correct **Port**.

---

## Folder & File Structure

Organize your project like this:

```
SIT210_Task3_3D/
│
├── src/
│   └── main.ino             # Your main Arduino code
│
├── README.md                # This file
├── libraries/               # Optional: extra Arduino libraries
└── docs/                    # Optional: images or flow diagrams
```

---

## Configuration Steps

1. Open your `main.ino` file.
2. Update **Wi-Fi credentials**:

   ```cpp
   const char* ssid = "YOUR_WIFI_SSID";
   const char* password = "YOUR_WIFI_PASSWORD";
   ```
3. Update **MQTT broker info**:

   ```cpp
   const char* broker = "YOUR_MQTT_BROKER_ADDRESS";
   const int port = 1883; // or your broker port
   const char* topic = "wave_pat_topic";
   ```
4. Ensure your **sensor pins** match your hardware setup.
5. Save the file.

---

## Running the Program

1. Upload the code to the Arduino using **Upload** in the IDE.
2. Open **Serial Monitor** (baud rate 9600) to check status messages.
3. Connect the Arduino to the MQTT broker: it should display `Connected to Wi-Fi` and `Connected to MQTT`.

---

## Testing & Expected Behavior

1. **Wave Detection:**

   * Move your hand in front of the ultrasonic sensor.
   * The Serial Monitor should print `Wave Detected`.
   * MQTT message is sent to the broker.

2. **Pat Detection:**

   * Press the force/touch sensor.
   * The Serial Monitor should print `Pat Detected`.
   * MQTT message is sent to the broker.

3. Optional LED feedback should blink when a wave or pat is detected.

---

## Troubleshooting

* **Wi-Fi not connecting:** Check SSID/password, ensure 2.4GHz network.
* **MQTT errors:** Verify broker address, topic, and port.
* **Sensor not detecting:** Confirm wiring and correct pins in the code.
* **Arduino IDE upload issues:** Ensure correct board & port selected, reset board if needed.

