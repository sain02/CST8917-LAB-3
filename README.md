# FleetBook — Serverless Vehicle Booking System
### CST8917 — Serverless Applications | Lab 3 (Winter 2026)
### Name- Saizal Saini<br> Student Number- 041168394

### YouTube Video Link
https://youtu.be/Fm2IqF-TPRI


FleetBook is a complete end‑to‑end **serverless vehicle booking workflow** built using:

- **Azure Service Bus** (Queue + Topic + Filtered Subscriptions)
- **Azure Logic Apps** (workflow + branching + notifications)
- **Azure Functions** (Python backend for booking evaluation)
- **Static Web Client** (`client.html`) to submit and track bookings

This repository contains all files required for Lab 3.

---

## Overview

FleetBook processes a customer booking request through a fully serverless architecture:

1. Web client sends booking → **Service Bus Queue**
2. Logic App triggers on queue message
3. Logic App calls Azure Function (`check-booking`)
4. Function evaluates:
   - Vehicle availability (based on lab's fleet data)
   - Pricing (daily rate + add‑ons + weekly discount)
5. Logic App:
   - If **confirmed** → send confirmation email
   - If **rejected** → send rejection email
6. Logic App publishes result → **Service Bus Topic**
7. Web client polls:
   - `confirmed-sub`
   - `rejected-sub`
8. Web UI updates status live

---

## Features

- Fully serverless  
- Event‑driven workflow  
- Message routing with **Service Bus filters**  
- Automatic email notifications  
- Real‑time booking result tracking  
- Clean and secure architecture  
- Zero backend servers

---

### FleetBook — Serverless Vehicle Booking System
This project implements FleetBook, a serverless workflow that processes vehicle booking requests using Azure Service Bus, Logic Apps, Azure Functions, and a lightweight web client. The system demonstrates event-driven architecture, message routing, asynchronous processing, and cloud-native orchestration as part of CST8917 — Serverless Applications (Lab 3).

### Project Description
FleetBook allows customers to submit booking requests for vehicles, which are then evaluated automatically. A Service Bus queue receives incoming requests, a Logic App orchestrates processing, an Azure Function performs availability checks and pricing logic, and results are published to a Service Bus topic with filtered subscriptions for confirmed and rejected bookings. A small web client polls these subscription endpoints and updates the booking status in real time.

### Key Components

-Service Bus Queue — Accepts booking messages from the web client.

-Azure Logic App — Handles workflow orchestration: decoding messages, calling the Azure Function, branching on results, sending emails, and publishing final decisions.

-Azure Function (check-booking) — Evaluates fleet availability and computes pricing.

-Service Bus Topic with Subscriptions — Routes confirmed and rejected bookings using SQL filters.

-Web Client (client.html) — Sends requests to the queue and listens for booking results.

### Repository Contents

-function_app.py — Azure Function code for booking evaluation (provided in lab).

-requirements.txt — Python package requirements.

-test-function.http — Test cases for local function execution.

-client.html — Front-end interface for sending bookings and viewing results.

-local.settings.example.json — Template for local Azure Function configuration (no secrets).

-README.md — Project documentation.

### What the System Does

Accepts booking requests through a web form.
Sends requests securely to Azure Service Bus.
Executes serverless workflow via Logic Apps.
Evaluates bookings with Python logic in an Azure Function.
Determines whether a booking is confirmed or rejected.
Notifies customers through email.
Publishes results to Service Bus topic subscriptions.
Displays outcomes live in the web client.

### Technologies Used

-Azure Service Bus (Queue & Topic)

-Azure Logic Apps (Consumption)

-Azure Functions (Python)

-SAS Token Authentication

-Static HTML/JavaScript client

-REST API polling

## CONCLUSION

The FleetBook project successfully demonstrates how serverless technologies can be combined to build a scalable, event‑driven cloud application without traditional servers. By integrating Azure Service Bus, Logic Apps, and Azure Functions, the system provides a fully automated workflow for processing vehicle booking requests, evaluating availability, determining pricing, and routing results to the appropriate consumers. The use of filtered topic subscriptions ensures efficient message distribution, while the simple web client enables real‑time interaction with the underlying architecture.
This lab highlights the strengths of serverless design including flexibility, maintainability, cost‑efficiency, and resilience and provides hands‑on experience with building distributed cloud workflows. Overall, FleetBook is an effective end‑to‑end example of how modern serverless components can work together to solve real‑world problems with minimal infrastructure overhead.

---
---

# THANKS