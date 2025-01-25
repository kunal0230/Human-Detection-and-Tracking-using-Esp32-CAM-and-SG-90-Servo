



# Human Detection and Tracking using ESP32-CAM and SG90 Servo Motors

## Project Overview
This project demonstrates a simple and effective **human detection and tracking system** using the **ESP32-CAM module** and a **pan-tilt servo assembly** with two SG90 servo motors. The system streams live video, detects motion in the camera feed, and adjusts the servos to track the detected motion, ensuring that the target remains centered in the camera's frame.

---

## Features
1. **Human Detection**: Uses the ESP32-CAM to detect motion in the video feed.
2. **Real-Time Tracking**: Automatically adjusts the pan and tilt servos to follow detected motion.
3. **Web-Based Interface**:
   - Live video streaming.
   - Manual control for moving the servos (Up, Down, Left, Right).
   - Buttons to enable/disable motion tracking.
4. **Compact and Affordable**: Built using easily available components.

---

## Hardware Requirements
- **ESP32-CAM Module**
- **SG90 Servo Motors** (2 units for pan and tilt)
- **Pan-Tilt Servo Bracket Assembly**
- **12V to 5V DC Converter** (for powering servos)
- **Power Supply** (5V/2A recommended for stable operation)
- Connecting wires

### Circuit Diagram
| Component         | ESP32-CAM Pin | Description               |
|-------------------|---------------|---------------------------|
| Pan Servo (SG90)  | GPIO 14       | Horizontal movement       |
| Tilt Servo (SG90) | GPIO 15       | Vertical movement         |
| Servo Power (+)   | 5V            | External power source     |
| Servo Ground (-)  | GND           | Common ground             |

---

## Software Requirements
- Arduino IDE (with ESP32 Board Manager installed)
- Libraries:
  - **ESP32Servo**
  - **esp_camera**
  - **WiFi**

---

## Getting Started

### 1. Clone the Repository
```bash
https://github.com/kunal0230/Human-Detection-and-Tracking-using-Esp32-CAM-and-SG-90-Servo.git
```

### 2. Setup the ESP32-CAM

1. Install the required libraries in the Arduino IDE.
2. Select the **"AI-Thinker ESP32-CAM"** board under Tools > Board.
3. Connect the ESP32-CAM to your computer using an FTDI programmer or similar module.

### 3. Modify the Code

Replace the following placeholders in the code with your Wi-Fi credentials:

```cpp
const char* ssid = "REPLACE_WITH_YOUR_SSID";
const char* password = "REPLACE_WITH_YOUR_PASSWORD";
```


### 4. Upload the Code
1. Connect the ESP32-CAM module in programming mode.
2. Select the correct COM port and upload the code.
3. Open the Serial Monitor (115200 baud rate) to view the IP address assigned to the ESP32-CAM.

## How It Works
1. Initialization:

- The ESP32-CAM initializes the camera and connects to the Wi-Fi network.
- The web server starts, providing live video streaming and control options.

2. Human Detection:

- The system captures consecutive frames and identifies motion using a basic frame-difference algorithm.
- The frame is divided into regions of interest (ROI) to pinpoint the motion’s location.

3. Servo Tracking:

- Based on the detected region of motion:
- If motion is on the left, the pan servo moves left.
- If motion is on the right, the pan servo moves right.
- If motion is in the center, no adjustment is made.
- Similarly, the tilt servo adjusts up or down for vertical motion.

### Web Interface:

Users can access the live stream and control the servos manually through an intuitive web-based interface.
Web Interface
The web interface includes the following:

### Live Video Stream: View the camera feed in real-time.
###Control Buttons:
- Up, Down, Left, Right: Move the servos manually.
- Track: Enable motion tracking.
- Track Off: Disable motion tracking.
  
## Folder Structure
```
project-folder/
├── esp32_cam_tracking.ino      # Main Arduino sketch
├── camera_pins.h               # Camera pin configuration
├── helpers.h                   # Helper functions for motion detection

└── README.md                   # Documentation (this file)
```
### Troubleshooting
1. Camera Not Detected:

- Ensure the camera ribbon cable is securely connected.
- Double-check pin configurations in camera_pins.h.

2. Servo Not Moving:

- Verify power supply to the servos.
- Ensure the correct GPIO pins are assigned.

3. Wi-Fi Connection Fails:

- Verify SSID and password in the code.
- Ensure your router supports 2.4 GHz (ESP32 does not support 5 GHz).

