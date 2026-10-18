# ESP32 Home Automation System with Blynk IoT

## 📌 Project Overview

This project is an IoT-based Home Automation System built using the **ESP32 microcontroller**, **Blynk IoT platform**, and a **DHT11 temperature and humidity sensor**. It allows users to control four electrical appliances remotely through the Blynk mobile application while monitoring real-time temperature and humidity data.

The system also supports physical push buttons, enabling appliances to be controlled manually as well as through the mobile app.

## ✨ Features

- **Remote Appliance Control:** Switch four appliances ON or OFF using the Blynk mobile application.
- **Manual Control:** Operate relays using four physical push buttons.
- **Temperature Monitoring:** Measure temperature in Celsius using the DHT11 sensor.
- **Humidity Monitoring:** Measure ambient humidity as a percentage.
- **Real-Time IoT Updates:** Send sensor readings to the Blynk dashboard every two seconds.
- **State Synchronization:** Synchronize virtual button states when the device connects to Blynk.
- **Wi-Fi Connectivity:** Connect the ESP32 to a Wi-Fi network for remote monitoring and control.
- **Serial Monitoring:** Display sensor readings and relay status in the Serial Monitor.

## 🛠️ Hardware Requirements

- ESP32 development board
- 4-channel relay module
- DHT11 temperature and humidity sensor
- 4 push buttons
- Wi-Fi connection
- Jumper wires and breadboard
- Suitable power supply
- Electrical appliances or low-voltage test loads

## 💻 Software Requirements

- Arduino IDE
- ESP32 board package for Arduino IDE
- Blynk IoT account and mobile application
- Blynk library for Arduino
- DHT sensor library
- Adafruit Unified Sensor library, if required by the installed DHT library

## 🔌 Pin Configuration

### DHT11 Sensor

| Component | ESP32 GPIO |
|---|---|
| DHT11 Data | GPIO 15 |
| DHT Type | DHT11 |

### Push Buttons

| Button | ESP32 GPIO | Blynk Virtual Pin |
|---|---|---|
| Button 1 | GPIO 26 | V1 |
| Button 2 | GPIO 25 | V2 |
| Button 3 | GPIO 33 | V3 |
| Button 4 | GPIO 32 | V4 |

### Relay Module

| Relay | ESP32 GPIO |
|---|---|
| Relay 1 | GPIO 13 |
| Relay 2 | GPIO 12 |
| Relay 3 | GPIO 14 |
| Relay 4 | GPIO 27 |

### Blynk Sensor Data

| Sensor Data | Blynk Virtual Pin |
|---|---|
| Humidity | V5 |
| Temperature | V6 |

## ⚙️ Setup and Installation

### 1. Install Arduino IDE

Download and install the Arduino IDE from the official website:

https://www.arduino.cc/en/software

Install the ESP32 board package and select the appropriate ESP32 board and serial port.

### 2. Install Required Libraries

Open Arduino IDE → **Sketch → Include Library → Manage Libraries** and install:

- Blynk
- DHT sensor library by Adafruit
- Adafruit Unified Sensor, if needed

The `WiFi.h`, `WiFiClient.h`, and ESP32 networking functionality are provided by the ESP32 board package.

### 3. Configure Blynk IoT

Create a device template in Blynk IoT and configure the following virtual datastreams:

- V1–V4: Integer values for appliance control buttons
- V5: Humidity value
- V6: Temperature value

Configure the four control widgets as switches and the sensor widgets as gauges, labels, or charts.

Add the Blynk template ID, template name, and device authentication token to the Arduino sketch.

### 4. Configure Wi-Fi

Update the Wi-Fi credentials in your sketch:

```cpp
char ssid[] = "YOUR_WIFI_NAME";
char pass[] = "YOUR_WIFI_PASSWORD";
```

Use a compatible Wi-Fi network supported by your ESP32.

### 5. Upload the Code

1. Connect the ESP32 to your computer.
2. Open the project sketch in Arduino IDE.
3. Select the correct board and COM port.
4. Upload the code.
5. Open Serial Monitor at **115200 baud**.
6. Check that the device connects to Wi-Fi and Blynk.

### 6. Test the System

- Use the Blynk app to switch each relay.
- Press the physical buttons to toggle the corresponding relays.
- Monitor temperature and humidity on the dashboard.
- Check the Serial Monitor for sensor readings and connection errors.

## 🔄 How It Works

1. The ESP32 initializes the relay outputs, push-button inputs, and DHT11 sensor.
2. It connects to the configured Wi-Fi network and Blynk IoT.
3. Blynk virtual pins V1–V4 receive remote appliance-control commands.
4. Physical buttons allow local toggling of the four relays.
5. The DHT11 sensor provides temperature and humidity readings.
6. The readings are sent to Blynk virtual pins V5 and V6 every two seconds.
7. When the device reconnects to Blynk, the code requests synchronization of the four virtual button states.

## 🔐 Security Considerations

- Never publish your real Blynk authentication token or Wi-Fi password in a public repository.
- Store credentials in a separate, untracked configuration file or use a secure configuration method.
- If credentials have already been exposed publicly, change the Wi-Fi password if appropriate and regenerate the Blynk device token.
- Use a properly rated relay module and suitable electrical protection.
- Mains-voltage wiring should be handled by a qualified person. Disconnect power before making wiring changes.

## ⚠️ Important Implementation Notes

- The code initializes relay outputs to `HIGH`, which is commonly the OFF state for active-low relay modules. Confirm the logic for your particular module.
- The DHT11 sensor generally does not require readings as frequently as every two seconds; a longer interval may improve reliability.
- The physical button logic uses `delay(200)` for basic debouncing. A non-blocking debounce approach can improve responsiveness.
- The current button-handling function checks buttons sequentially, so simultaneous button presses may not all be processed.
- Relay state synchronization should be tested carefully, especially if your relay module uses active-low logic.

## 🚀 Future Improvements

- Add energy consumption monitoring.
- Introduce scheduling and automation rules.
- Add voice assistant integration.
- Improve button debouncing and relay state synchronization.
- Add sensor fault alerts and Wi-Fi reconnection handling.
- Support additional sensors and appliances.

## 📄 License

This project is available for educational and personal learning purposes. Add a specific open-source license file if you intend to distribute it under a formal license.

## 👨‍💻 Author

**Zeeshan Anjum**

IoT and Embedded Systems Project


