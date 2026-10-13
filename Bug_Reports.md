# Defect & Bug Tracking Logs (Jira-Style)

This document archives the critical software defects discovered and logged during the integration testing phase of the Child Monitoring platform. 

---

### 🐜 BUG-001: Live Tracking Map Interface Freezes on Pinch-to-Zoom
* **Severity:** High (Breaks core application functionality)
* **Component:** Map UI Module
* **Environment:** Android 14 / Emulator Profile

#### Steps to Reproduce:
1. Log into the parent mobile dashboard using valid registered credentials.
2. Select the primary "Live Tracking Map" tab from the lower navigation deck.
3. Perform a rapid double-tap or pinch gesture directly on the map surface to zoom in on the active child location marker pin.

#### Expected Result:
The map interface scales smoothly, loads detailed street telemetry vectors, and maintains full responsiveness.

#### Actual Result:
The map view freezes completely. The application window becomes totally unresponsive to touch events and must be force-closed by the operating system.

---

### 🐜 BUG-002: System Fails to Trigger Vibration Alert on Geofence Breach
* **Severity:** Medium (Functional requirement mismatch)
* **Component:** Notification Engine
* **Environment:** iOS 17 / Cross-Platform Build

#### Steps to Reproduce:
1. Access account settings and configure a custom safe-zone geofence boundary at 1000 meters.
2. Force a telemetry state update that causes the child tracking node to position at 1500 meters (outside the safety limit).
3. Observe the parent mobile device.

#### Expected Result:
The device rings, triggers the physical haptic vibration motor continuously, and flashes a visual red safety notification ribbon.

#### Actual Result:
The visual red safety ribbon flashes perfectly, but the physical haptic engine fails to engage. The device remains completely silent and does not vibrate.

---

### 🐜 BUG-003: App Allows Unrestricted Submissions of Empty Device Setup Profiles
* **Severity:** High (Data validation failure / Potential database contamination)
* **Component:** Account Registration Deck
* **Environment:** Web Interface / Chrome Core

#### Steps to Reproduce:
1. Navigate to the "Add New Tracking Device" configuration wizard page.
2. Leave the mandatory "Unique Child Device ID" text input form blocks completely blank.
3. Click the "Submit Registration" button.

#### Expected Result:
The frontend input validation script intercepts the action, stops submission, and alerts the user: "Enter child's device ID."

#### Actual Result:
The application allows the empty form to execute, bypasses validation completely, and saves a broken, blank user entry directly into the system architecture.
