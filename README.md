# Project SAMS (Student Attendence Management System)

## Project Overview

This project implements an advanced automated attendance system that leverages multiple biometric modalities—specifically facial recognition and fingerprint scanning—to record student attendance securely and accurately. The system is designed to operate both at the classroom entrance and during scheduled sessions. It adapts dynamically to uploaded timetables, captures attendance with real-time analytics, and employs advanced techniques (including GraphRAG for data retrieval and anomaly detection) to provide comprehensive reporting and enhanced security.

## Key Features & Functionalities

### 1. Biometric Attendance at Entry
- **Registration:** Students enroll by submitting facial images and fingerprint samples.
- **Verification:** At the classroom entrance, students authenticate using a live fingerprint scan or facial recognition with integrated liveness detection to prevent spoofing.
- **Timestamp Logging:** Each successful verification is recorded with a precise timestamp and logged in an exportable Excel sheet.

### 2. Session-Based Attendance Verification with Buzzer Alert
- **Dynamic Scheduling:** The system parses an uploaded timetable to divide the day into distinct class sessions and breaks.
- **Buzzer Notification:** A buzzer is activated approximately 10 minutes before the end of each session, alerting students to prepare for the attendance capture.
- **Delayed Image Capture:** After a configurable 3–5 minute delay following the buzzer alert, a classroom camera captures a group image.
- **Real-Time Recognition:** The captured image is processed using robust facial recognition algorithms with integrated liveness detection to verify that faces are live.
- **Attendance Update:** Detected live faces are cross-referenced with the registered database to mark students as present or absent.

### 3. Timetable Integration & Automated Adaptation
- **Automatic Adaptation:** The system automatically adjusts its operations based on the uploaded timetable, ensuring that biometric checks occur only during scheduled sessions.
- **Efficiency:** This dynamic adaptation prevents unnecessary processing during breaks or non-class periods.
- **Time Sector Division:** Attendance is categorized into predefined segments (e.g., Morning Session 1: 8:30–9:30 AM) with specific logic to handle late arrivals, early departures, and partial attendance.

### 4. Advanced Attendance Analysis & Reporting
- **Duration Analysis:** The system calculates the total attendance time for each student, comparing it against scheduled class durations.
- **Irregularity Detection:** Partial attendance, late arrivals, or early departures are flagged, ensuring deviations from the timetable are noted.
- **Comprehensive Reporting:** Detailed daily reports—including timestamps, session records, and analytical insights—are generated and exportable to Excel.
- **GraphRAG-Enhanced Insights:** An integrated GraphRAG module leverages graph-based retrieval techniques to correlate biometric data with timetable information. This enables sophisticated anomaly detection and trend analysis, revealing hidden patterns in attendance behavior and providing actionable insights.

## Technology Stack & Implementation Details

### Hardware Requirements
- **Central Controller:** Raspberry Pi 4 or an equivalent edge computing device.
- **Biometric Sensors:** High-quality fingerprint scanner and an HD camera (or ESP32-CAM) for facial recognition.
- **Buzzer Module:** An electronic buzzer or speaker for audible notifications.
- **Optional Depth Sensor:** For enhanced liveness detection to thwart spoofing attempts.
- **Network Modules:** Wi-Fi for real-time data communication and a GSM module as a backup connectivity option.

### Software & Frameworks
- **Facial Recognition:** Implemented with OpenCV integrated with deep learning frameworks (e.g., TensorFlow/Keras) for real-time face detection and verification.
- **Liveness Detection:** Uses anti-spoofing techniques such as blink detection and micro-expression analysis.
- **Fingerprint Authentication:** Processed via dedicated libraries tailored for biometric analysis.
- **Buzzer & Timing Control:** Managed with Python scripts or ROS2 nodes to trigger alerts and control delayed image capture based on the timetable.
- **Data Management:** Uses lightweight databases (SQLite or MySQL) to store biometric data and attendance logs.
- **Automation & Analysis:** Employs Python-based tools (e.g., Pandas) for data processing and exporting logs.
- **GraphRAG Integration:** Leverages graph-based retrieval techniques to correlate biometric data with timetable information, enhancing anomaly detection and trend analysis.

### System Architecture
- **Modular Design:** The system is divided into independent modules for biometric registration, live verification with liveness detection, buzzer alerts with delayed capture, timetable integration, and attendance reporting.
- **Real-Time Processing:** Sensor data is processed in real time to ensure prompt and accurate attendance recording.
- **User Interface:** A web-based dashboard or lightweight desktop application facilitates system configuration, live monitoring, and report generation.
- **GraphRAG Module:** Embedded within the data analysis layer, the GraphRAG module uses structured graph-based data to detect anomalies and generate insights.

## Expected Outcomes

- **Accurate and Secure Attendance:** Live biometric verification minimizes spoofing risks and ensures high data integrity.
- **Dynamic Session Monitoring:** Buzzer alerts and delayed image capture are tightly synchronized with class schedules, ensuring timely attendance logging.
- **Efficient Operation:** Automatic adaptation to timetables prevents unnecessary processing during non-class periods.
- **Comprehensive Reporting:** Detailed analytics—including attendance duration, irregularities, and trend analysis—support informed decision-making.
- **Advanced Data Insights:** The GraphRAG module provides an additional layer of data correlation and anomaly detection, offering strategic insights that can optimize operational efficiency.

