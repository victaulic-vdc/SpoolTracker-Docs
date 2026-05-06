# New Scan

## Starting a New Scan

The user can initiate a new scan by tapping the **New Scan** button on the dashboard.

## Location Permission

The application requests location permission to capture geolocation data. It is recommended to grant this permission for accurate location tracking. If the user does not wish to share their location, they can disallow the permission.

<p>
  <img src="./images/location-permission-android.jpeg" width="200" alt="Location permission on Android">
  <img src="./images/location-permission-android-2.jpeg" width="200" alt="Location permission on Android — result">
</p>

<p>
  <img src="./images/location-permission-ios.jpeg" width="200" alt="Location permission on iOS">
  <img src="./images/location-permission-ios-2.jpeg" width="200" alt="Location permission on iOS — result">
</p>

## Camera Permission

The application requests camera permission, which is **required** for scanning QR codes.

<p>
  <img src="./images/camera-permission-android.jpeg" width="200" alt="Camera permission on Android">
  <img src="./images/camera-permission-ios.jpeg" width="200" alt="Camera permission on iOS">
</p>

## QR Code Scanning

The user can scan single or multiple QR codes in one session.

### Single QR Scanning

Scan one QR code at a time by pointing the camera at a spool's QR label.

<p>
  <img src="./images/single-qr-scan-android.jpeg" width="200" alt="Single QR scanning on Android">
  <img src="./images/single-qr-scan-ios.jpeg" width="200" alt="Single QR scanning on iOS">
</p>

### Multiple QR Scanning

Scan multiple QR codes in sequence. The maximum number of QRs per multi-scan session can be configured in [Settings](login-and-dashboard.md#settings) (default is 25, range is 2–100).

<p>
  <img src="./images/multi-qr-scan-android.jpeg" width="200" alt="Multiple QR scanning on Android">
  <img src="./images/multi-qr-scan-ios.jpeg" width="200" alt="Multiple QR scanning on iOS">
</p>

## Scan Form

If the QR code is valid, the application navigates to the **New Scan** form with the following data pre-filled:

- **Spool Name** — from the QR code
- **Location** — captured geolocation
- **Date/Time** — current timestamp

### Single QR Scan Form

<p>
  <img src="./images/scan-form-single-android.jpeg" width="200" alt="Single QR scan form on Android">
  <img src="./images/scan-form-single-ios.jpeg" width="200" alt="Single QR scan form on iOS">
</p>

### Multiple QR Scan Form

<p>
  <img src="./images/scan-form-multi-android.jpeg" width="200" alt="Multiple QR scan form on Android">
  <img src="./images/scan-form-multi-ios.jpeg" width="200" alt="Multiple QR scan form on iOS">
</p>

## Timer for Timed Tasks

If the selected status is a **timed task**, a timer is displayed. The user can:

- **Start** the timer to begin recording time spent on the task
- **Pause** or **Stop** the timer at any time
- Enter values in **Add Time** or **Deduct Time** fields to adjust the recorded duration

> **Tip:** Use the Add/Deduct time fields to correct for any discrepancies, such as time spent away from the task. For more on configuring timed vs. non-timed tasks, see [Project Settings](../dashboard/project-settings.md).

<p>
  <img src="./images/timer-android.jpeg" width="200" alt="Timer for timed task on Android">
  <img src="./images/timer-ios.jpeg" width="200" alt="Timer for timed task on iOS">
</p>

## Adding Photos

The user can add photos by tapping the **"+"** button. Up to **4 images** can be attached per scan.

<p>
  <img src="./images/add-photos-android.jpeg" width="200" alt="Adding photos on Android">
  <img src="./images/add-photos-ios.png" width="200" alt="Adding photos on iOS">
</p>

## Confirming a Scan

The user taps the **Confirm** button to save the scan. The scan is recorded and appears in the [scan history](login-and-dashboard.md#dashboard-and-scan-history).

<p>
  <img src="./images/confirm-scan-android.jpeg" width="200" alt="Confirm scan on Android">
  <img src="./images/confirm-scan-ios.jpeg" width="200" alt="Confirm scan on iOS">
</p>

## Duplicate Scan Error

If a scan already exists with the same spool name and task, the application displays an error.

<p>
  <img src="./images/duplicate-error-android.jpeg" width="200" alt="Duplicate scan error on Android">
  <img src="./images/duplicate-error-ios.jpeg" width="200" alt="Duplicate scan error on iOS">
</p>

## Cancelling a Scan

The user can tap the **Cancel** button to discard the scan without saving.

<p>
  <img src="./images/cancel-scan-android.jpeg" width="200" alt="Cancel scan on Android">
  <img src="./images/cancel-scan-ios.png" width="200" alt="Cancel scan on iOS">


