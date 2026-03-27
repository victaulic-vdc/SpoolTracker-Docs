# Getting Started with SpoolTracker Mobile

## Introduction

This guide provides a quick overview and step-by-step navigation for conducting spool tracing and tracking using the SpoolTracker application. The application digitizes the tracking process for Installation Engineers by leveraging mobile devices.

SpoolTracker is available on two platforms: **Android** and **iOS**. Installation Engineers from Victaulic and its customers should reference this guide for navigating through the application.

## Need for the Solution

Currently, spools are tracked through their journey from fabrication shop to loading onto the truck, to shipping and delivery at the customer site. However, Victaulic did not previously have visibility into spool status after delivery. The key requirements were:

- Digitalize the tracing and tracking process of spools by leveraging mobile devices
- Gain insight into spool installation status and time taken for installation
- Improve productivity and optimize operations

## Solution Overview

SpoolTracker is a smartphone solution that enables Installation Engineers to update the installation status of spools using QR codes, with automatic capture of geolocation and timestamps.

## User Roles

In SpoolTracker, the following roles are defined:

- **Installation Engineers** — Access the application on smartphones (Android / iOS) to scan and track spools in the field

> **Note:** Admin roles for project configuration are managed through the [web dashboard](../dashboard/getting-started.md).

## Salient Features

- Login to the application using a valid **Project code** or **Organization code**
- View previous spool scan history for an Organization or Project
- Perform single or multiple scanning of QR code(s) on spools using the mobile camera
- Automatic capture of geolocation and date-time of each scan
- Record installation task status with textual notes and images
- Record time spent on tasks and enter add/deduct time in case of discrepancies
- Perform manual scans from the spool details page
- Filter scan history by spool name and date range
- Offline access on both platforms
- Automatic sync of offline records when network is available and the app is in the foreground
- Set maximum QR count, device name, and default status using the Settings feature

## Assumptions

The following assumptions apply:

- Users can take a maximum of **4 images** with each scan
- Auto sync works only when the application is in the **foreground**
- In case of multiple QR scans, **25** is the default maximum limit for all users, but this can be changed to any number between 2 and 100

## Offline Usage Disclaimer

To use the application offline, the user must first log in with a valid Project or Organization code while connected to a network. After the initial login, the application can be used in offline mode.

> **Important:** Offline records will sync automatically when the device regains network connectivity and the application is open in the foreground.
