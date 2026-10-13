# Functional Test Cases Checklist

This document contains structured, professional test cases designed to evaluate the functional requirements of the Child Monitoring and Location Tracking platform.

---

## 1. Authentication & Security (Login Module)

| Test Case ID | Test Description | Test Steps | Expected Result | Status |
| :--- | :--- | :--- | :--- | :--- |
| **TC_LOGIN_01** | Verify successful login with valid parent credentials. | 1. Open the application landing page.<br>2. Enter a registered email.<br>3. Enter the correct password.<br>4. Click the "Login" button. | System grants access and navigates seamlessly to the live tracking map dashboard. | Pass |
| **TC_LOGIN_02** | Verify system blocks access when using an incorrect password (Negative Test). | 1. Open the application landing page.<br>2. Enter a registered email.<br>3. Enter an incorrect password.<br>4. Click the "Login" button. | System safely blocks access, keeps the user on the login screen, and triggers an error alert: "Invalid password." | Pass |

---

## 2. Device Limits & Inputs (Boundary Value Analysis)

| Test Case ID | Test Description | Test Steps | Expected Result | Status |
| :--- | :--- | :--- | :--- | :--- |
| **TC_LIMIT_01** | Verify system boundary handling when hitting maximum device limit. | 1. Navigate to the "Add Device" configuration screen.<br>2. Successfully register 5 active child devices.<br>3. Attempt to register a 6th child device. | System blocks the 6th addition and displays an explicit error message: "Maximum limit of 5 devices reached." | Pass |
| **TC_LIMIT_02** | Verify mandatory input field validation for device setup. | 1. Navigate to the "Add Device" configuration screen.<br>2. Leave the "Child Device ID" input field completely blank.<br>3. Click the "Submit" button. | System prevents submission and highlights the empty input block with an error prompt: "Enter child's device ID." | Pass |

---

## 3. Location Telemetry & Geofencing (System Logic)

| Test Case ID | Test Description | Test Steps | Expected Result | Status |
| :--- | :--- | :--- | :--- | :--- |
| **TC_MAP_01** | Verify real-time GPS coordinate mapping. | 1. Log into the parent dashboard.<br>2. Access the main live map view.<br>3. Track the simulated movement of the child device. | The map pin updates location parameters smoothly and displays accurate street coordinates. | Pass |
| **TC_MAP_02** | Verify perimeter alert handling (Geofencing exception). | 1. Configure a safe-zone boundary radius limit at 1km.<br>2. Simulate the child device moving 1.5km away.<br>3. Observe parent interface. | System detects the boundary breach instantly, triggers a vibration notification, and flashes a prominent red safety alert. | Pass |
