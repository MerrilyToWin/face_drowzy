# Driver Drowsiness Detection System

## Overview
This system is designed to detect driver drowsiness using computer vision and facial landmarks detection. It monitors the driver's eyes in real-time and provides escalating alerts when signs of drowsiness are detected, including audio warnings, SMS notifications, and emergency calls.

## Features
- Real-time face and eye detection
- Multiple drowsiness detection stages
- Escalating alert system:
  1. Local audio buzzer warning
  2. SMS notification to emergency contact
  3. Automated phone call with voice alert
- Visual status display with color-coded warnings
- Text-to-speech alerts

## Prerequisites
- Python 3.x
- OpenCV (`cv2`)
- NumPy
- dlib
- imutils
- Twilio
- pyttsx3
- Windows OS (for `winsound`)

## Required Files
- `shape_predictor_68_face_landmarks.dat` (facial landmark predictor model)
- Valid Twilio account credentials

## Installation

1. Install required Python packages:
```bash
pip install opencv-python numpy dlib imutils twilio pyttsx3
```

2. Download the facial landmark predictor file (`shape_predictor_68_face_landmarks.dat`)

3. Configure Twilio credentials in the code:
```python
TWILIO_SID = "your_twilio_sid"
TWILIO_AUTH_TOKEN = "your_twilio_auth_token"
TWILIO_PHONE_NUMBER = "your_twilio_phone_number"
PARENT_PHONE_NUMBER = "emergency_contact_number"
```

## How It Works

### Detection System
- Uses dlib's facial landmark detection to track 68 facial points
- Calculates eye aspect ratio (EAR) to determine eye state
- Monitors both eyes independently for improved accuracy

### Alert Levels
1. **Level 1 - Drowsy Detection**
   - Triggers local buzzer warning
   - Reset after alert

2. **Level 2 - Continued Drowsiness**
   - Sends SMS to emergency contact
   - Includes status message

3. **Level 3 - Critical Alert**
   - Initiates automated phone call
   - Plays voice alert message
   - Resets monitoring cycle

### Status Indicators
- **Active**: Normal driving state
- **Drowsy**: Initial warning state
- **Sleeping**: Critical warning state

## Usage
1. Run the script:
```bash
python drowsiness_detection.py
```

2. Position yourself in front of the camera
3. Press 'q' to quit the application

## Safety Notes
- This system is designed as an assistive tool and should not be relied upon as the sole measure of driver safety
- Regular breaks and proper rest are essential for safe driving
- The system should be tested thoroughly before deployment in real-world conditions

## Technical Specifications
- Camera input: Default system camera (index 0)
- Frame processing: Real-time grayscale conversion
- Face detection: dlib frontal face detector
- Eye blink ratio threshold: 0.25 (active), 0.21-0.25 (drowsy)
- Alert timing: Configurable through sleep/drowsy counters

## Troubleshooting
- Ensure proper lighting conditions for accurate face detection
- Verify Twilio credentials and phone number formatting
- Check camera permissions and connectivity
- Confirm installation of all required dependencies

## Dependencies Version Requirements
- OpenCV: 4.x or higher
- dlib: 19.x or higher
- Python: 3.7 or higher
- Twilio: Latest stable version
- pyttsx3: Latest stable version

## Support
For issues related to:
- Face detection: Check lighting and camera position
- Alert system: Verify Twilio credentials and network connectivity
- System performance: Ensure minimum hardware requirements are met
