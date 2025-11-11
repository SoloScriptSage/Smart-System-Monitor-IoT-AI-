# CortexNode — Smart System Monitor

**CortexNode** is a compact IoT device that monitors PC/server metrics including temperature, fan speed, power consumption, and voltage. It transmits real-time data to a dashboard and optionally integrates AI for predictive maintenance. This project demonstrates PCB design, embedded firmware, and full-stack development in a single package.

---

## Features

* **Real-time monitoring**: Temperature (TMP36), voltage/current (INA219), and system metrics.
* **Display**: Onboard 128×64 OLED shows live readings.
* **Wireless connectivity**: ESP32 Wi-Fi module sends data to cloud or dashboard.
* **AI predictive analysis** *(optional)*: TensorFlow Lite Micro model predicts trends and anomalies.
* **Battery-powered**: 18650 Li-ion with TP4056 charger and 3.3 V buck-boost regulator.
* **Compact PCB design**: Ready for prototyping or custom enclosures.

---

## Hardware Components

| Ref                   | Component                 | Notes                               |
| --------------------- | ------------------------- | ----------------------------------- |
| ESP32-WROOM-32        | Microcontroller           | Wi-Fi + I²C interface               |
| INA219AIDR            | Current/Voltage sensor    | Measures load and power consumption |
| TMP36xS               | Analog temperature sensor | Reads temperature                   |
| OLED 128×64 (SSD1306) | Display                   | I²C interface                       |
| 18650 Li-ion          | Battery                   | 2500–3500 mAh                       |
| TP4056                | Charger/protection        | 1S Li-ion                           |
| Buck-boost module     | 1S → 3.3 V                | Powers ESP32 and peripherals        |

---

## Software Stack

* **Firmware**: Arduino/C++ for ESP32
* **I²C Libraries**: Adafruit_INA219, Adafruit_SSD1306
* **Backend / Dashboard**: Python (FastAPI) or C# Blazor + SignalR
* **Frontend**: React or Blazor WebAssembly
* **Optional AI**: TensorFlow Lite Micro for predictive analytics

---

## Connections

* **ESP32 I²C**: SDA → GPIO21, SCL → GPIO22
* **INA219**: VS+ → 3.3 V, GND → GND, SDA/SCL → ESP32 I²C, VIN+/VIN– → load
* **TMP36**: VCC → 3.3 V, GND → GND, VOUT → GPIO34 (ADC input)
* **OLED**: VCC → 3.3 V, GND → GND, SDA/SCL → ESP32 I²C

---

## Power Supply

* **Battery**: 1 × 18650 Li-ion
* **Charger**: TP4056 module with protection
* **Voltage Regulation**: Buck-boost module outputs stable 3.3 V to ESP32, sensors, and display
* **Decoupling**: 0.1 µF ceramic + 10 µF bulk capacitor near ESP32

---

## Getting Started

1. **Assemble hardware**: Connect ESP32, sensors, OLED, and power circuit as per schematic.
2. **Flash firmware**: Use Arduino IDE or PlatformIO.
3. **Install libraries**: `Adafruit_INA219`, `Adafruit_SSD1306`
4. **Configure Wi-Fi & dashboard**: Update SSID, password, and backend endpoint.
5. **Run dashboard**: Launch React/Blazor frontend to visualize metrics.
6. **Optional**: Deploy TinyML model for predictive monitoring.

---

## Future Improvements

* Add multiple sensor nodes for distributed monitoring
* Integrate cloud services (Azure/AWS) for historical analysis
* Implement low-power deep sleep for longer battery life
* Extend AI models for fan failure and voltage anomaly prediction

---

## License

MIT License — free to use, modify, and distribute.
