# MindGameSmartWatch

MindGameSmartWatch is a Java Android application for Wear OS smartwatches. Its primary purpose is to collect sensor data (including heart rate and motion sensors) from the wearable device and publish this data in real time to MQTT topics for remote monitoring and analysis.

## Features

- **Sensor Data Collection:** Captures data from the gyroscope, accelerometer, and heart rate sensors.
- **MQTT Publishing:** Streams sensor data to a remote MQTT broker (default: broker.hivemq.com) using unique watch IDs for topic separation.
- **Foreground Service:** Runs as a persistent service to ensure reliable, continuous data collection.
- **Permission Management:** Requests and manages required permissions for sensors, background operation, and storage.
- **Status Monitoring:** Displays MQTT connection status, watch ID, and internet connectivity directly on the watch interface.
- **Start/Stop Control:** Provides simple controls to start and stop data collection from the main activity.

## How It Works

1. On launch, the app requests all necessary permissions and displays the watch's unique ID.
2. Press **Start** to begin collecting and publishing sensor data. Data is sent to MQTT topics named after the watch ID.
3. Press **Stop** to end data collection and MQTT publishing.
4. The sensor service continues running in the background (with a notification), ensuring uninterrupted data acquisition.
5. The app monitors internet connectivity and MQTT connection status, updating the user via the UI.

## MQTT Data Format

Each sensor's data is published under a topic in the format: `<watchID>/<sensor_type>`

Data is formatted as CSV:  
`<value1>,<value2>,<value3>,<timestamp>,<formatted_date>`

Example for accelerometer:  
`-0.001,0.123,9.807,1234567890,2025-07-14 15:53:20.123`

## Permissions

The app requires the following permissions:
- `BODY_SENSORS`
- `WAKE_LOCK`
- `FOREGROUND_SERVICE`
- `WRITE_EXTERNAL_STORAGE`

These permissions are requested at runtime. If not granted, the app will prompt the user to enable them in settings.

## Building and Installation

1. Open the project in Android Studio.
2. Connect your Wear OS device or use the emulator.
3. Build and install the app using the standard Android Studio workflow.

## Usage

1. Grant all requested permissions on first launch.
2. Tap **Start** to begin streaming sensor data.
3. Monitor status updates on the main screen.
4. Tap **Stop** to end streaming.

## Customization

- **MQTT Broker:** Change the broker URL in `SensorService.java` (`"tcp://broker.hivemq.com:1883"`) if you need to use a different MQTT server.
- **Sensor List:** Modify the `initSensors()` method to add or remove sensors as needed.

## Dependencies

- [Paho MQTT Android Service](https://github.com/eclipse/paho.mqtt.android)
- AndroidX libraries
## Citation

Please cite the following publication-

**ACM Reference Format:**
Shehjar Sadhu, Nishtha Bhagat, Elijah Castillo, Lisa Weyandt, Kunal
Mankodiya, and Dhaval Solanki. 2025. Is wearable data reliable for monitoring behavior? Design of a wearable-based IoMT puzzle game for remote behavior monitoring. In The 15th International Conference on the Internet of Things (IOT 2025), November 18–21, 2025, Vienna, Austria. ACM, New York, NY, USA, 9 pages. https://doi.org/10.1145/3770501.3770523

## License

[MIT](LICENSE)

---

*This project is maintained by [wearablebiosensing](https://github.com/wearablebiosensing).*