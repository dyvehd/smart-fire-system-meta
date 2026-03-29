# Smart Fire Monitoring and Alarm System (Meta Repository)

This repository serves as a central meta-repository linking the core components of the Smart Fire Monitoring and Alarm System project. It aggregates submodules for the system API/Dashboard and the AI/Hardware integration modules.

## Project Overview

This multidisciplinary project integrates IoT hardware, a web dashboard, and an AI-powered computer vision system to provide real-time monitoring, multi-level early warnings, and automated physical responses to fire hazards.

### Inputs

- **Environmental Data:** Temperature and air humidity sensor (DHT20).
- **Image Data:** Camera (laptop/smartphone) for real-time area monitoring.
- **Interaction Data:** User control commands from the Web Dashboard (e.g., system ON/OFF, fire drill mode).

### Outputs

- **Display Devices:** LCD screen (for local parameter display) and Web Dashboard (for remote status and real-time charts).
- **Actuation Signals:** Mini Fan (simulating a smoke exhaust ventilation system) and Mini Water Pump (simulating a fire sprinkler system).
- **Warning System:** RGB LED (changes color based on the danger level) and Alarm Siren (using laptop speakers).

## Functional Modules

1. **Monitoring:** Continuously measures and displays temperature and humidity on the LCD screen, and plots real-time data charts on the Web App.
2. **Multi-level Alert:**
   - _Level 1 (Early Warning):_ If the temperature exceeds a safe threshold (e.g., > 40°C), the system automatically turns on the ventilation fan and sends a "High Temperature" notification to the application.
   - _Level 2 (Fire Alarm):_ If there is a sudden temperature spike (e.g., > 55°C) or the AI camera detects fire, the system triggers the full alarm protocol (siren sounds, red lights flash, and the water pump is activated).
3. **Control:** Allows manual ON/OFF control of the fan/pump remotely via the Web Dashboard. Includes a "Fire Drill" function to activate all output devices and test system operability with a single button press.
4. **Logging:** Records the history of instances where the temperature exceeded thresholds and logs all AI fire detections (saving timestamps and the AI's confidence score).
5. **AI System:** Integrates an AI model into the application to continuously analyze the camera's live video feed, automatically detecting early-stage fires even before the room temperature rises significantly.

## AI & Machine Learning Approach

- **Problem Description:** Image Classification / Object Detection to determine whether fire is present in the current camera frame.
- **Machine Learning Type:** Supervised Learning.
- **Data:** Trained using a labeled fire image dataset from Kaggle.
- **Proposed Algorithms:** Convolutional Neural Networks (CNN) or YOLO (You Only Look Once).
- **Optimization:** Leverages Transfer Learning techniques with lightweight architectures to ensure fast, real-time detection speeds on an average personal computer.

## Submodules

- [`python-mqtt-adafruit/`](python-mqtt-adafruit/): Contains the Python scripts handling the AI model predictions, MQTT broker communication, and hardware serial connections.
- [`smart-fire-system/`](smart-fire-system/): Contains the backend API (FastAPI) handling state management, alerts, device routing, application database, and a frontend web dashboard (to be built).
