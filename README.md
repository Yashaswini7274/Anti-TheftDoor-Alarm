# Anti-TheftDoor-Alarm

Overview

This project is an Edge AI-powered security surveillance system developed using Raspberry Pi, Python, OpenCV, and Telegram Bot API. The system continuously monitors its surroundings using an IR motion sensor and camera module. Upon detecting motion, it captures an image, performs human detection locally on the Raspberry Pi, and sends a real-time alert notification with the captured image through Telegram.

The entire processing pipeline runs on the edge device, reducing latency, minimizing cloud dependency, and improving privacy.

Features
Real-time motion detection using IR sensor
Human detection using OpenCV Haar Cascade classifier
Automatic image capture through Raspberry Pi Camera Module
LED and buzzer activation during intrusion events
Instant Telegram alerts with captured image
Edge AI processing for low-latency response
Continuous surveillance and monitoring
Local image storage with timestamping
System Architecture
Hardware Components
Raspberry Pi
IR Motion Sensor
Raspberry Pi Camera Module
LED Indicator
Buzzer
Internet Connection
Software Components
Python
OpenCV
Raspberry Pi GPIO Library
Telegram Bot API
Haar Cascade Classifier
Workflow
System continuously monitors the IR sensor.
Motion is detected.
Raspberry Pi activates camera module.
Image is captured and stored locally.
OpenCV performs human detection.
LED and buzzer are activated.
If a human is detected:
Alert image is generated.
Telegram notification is sent.
User receives intrusion alert in Telegram.
System returns to monitoring mode.
Data Flow

Motion Detection → Camera Activation → Image Capture → Human Detection → Telegram Alert → User Notification

Project Structure
Edge-AI-Intrusion-Detection/
│
├── src/
│   ├── main.py
│   ├── human_detection.py
│   ├── telegram_alert.py
│   └── gpio_controller.py
│
├── images/
│   └── captured_intrusions/
│
├── models/
│   └── haarcascade_frontalface_default.xml
│
├── docs/
│   ├── block_diagram.png
│   ├── flowchart.png
│   └── report.pdf
│
├── requirements.txt
├── README.md
└── .gitignore
The system uses OpenCV Haar Cascade Classifier for human/face detection.

Steps:

Capture image
Convert image to grayscale
Load Haar Cascade model
Detect faces using detectMultiScale()
If one or more faces are detected:
Human detected
Otherwise:
Non-human object detected
Applications
Home Security
Office Surveillance
Smart Building Monitoring
Restricted Area Protection
Warehouse Security
IoT-Based Intrusion Detection
Future Enhancements
YOLO-based human detection
Face recognition and identification
Cloud storage integration
Mobile application support
Email and SMS notifications
Multi-camera surveillance



pseudo code
START

Import GPIO, Time, OS, OpenCV, DateTime, Requests

Set IR_SENSOR_PIN = 17
Set BUZZER_PIN = 22
Set LED_PIN = 18

Configure GPIO Pins

Set Telegram BOT_TOKEN
Set Telegram CHAT_ID

FUNCTION is_human(image_path)

    Load Haar Cascade XML File

    IF XML File Not Found THEN
        Return FALSE
    END IF

    Read Image

    Convert Image To Gray Scale

    Detect Faces Using Haar Cascade

    IF Face Count > 0 THEN
        Return TRUE
    ELSE
        Return FALSE
    END IF

END FUNCTION

FUNCTION send_telegram_message(photo_path, message)

    Open Photo File

    Create Telegram Request

    Send Photo And Message To Telegram Bot

END FUNCTION

Print "Anti-Theft System Active"

WHILE TRUE

    IF IR Sensor Detects Motion THEN

        Print "Motion Detected"

        Turn ON Buzzer

        Turn ON LED

        Generate Timestamp

        Create Image Path

        Capture Image Using Camera Module

        IF is_human(image_path) = TRUE THEN

            result ← "Human Detected"

        ELSE

            result ← "Object Detected"

        END IF

        Print result

        Send Captured Image And Result To Telegram

        Wait 5 Seconds

        Turn OFF Buzzer

        Turn OFF LED

        Print "Waiting For Object To Move Away"

        WHILE IR Sensor Still Detects Motion

            Wait 0.2 Seconds

        END WHILE

    END IF

    Wait 0.1 Seconds

END WHILE

IF Keyboard Interrupt Occurs THEN

    Print "Exiting System"

    Clean GPIO

END

STOP
