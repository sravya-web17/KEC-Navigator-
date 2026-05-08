# 🧭 KEC Indoor Campus Navigator

[![React Native](https://img.shields.io/badge/React_Native-20232A?style=for-the-badge&logo=react&logoColor=61DAFB)](https://reactnative.dev/)
[![Node.js](https://img.shields.io/badge/Node.js-339933?style=for-the-badge&logo=nodedotjs&logoColor=white)](https://nodejs.org/)
[![MongoDB](https://img.shields.io/badge/MongoDB-4EA94B?style=for-the-badge&logo=mongodb&logoColor=white)](https://www.mongodb.com/)
[![Socket.io](https://img.shields.io/badge/Socket.io-010101?style=for-the-badge&logo=socketdotio&logoColor=white)](https://socket.io/)
[![TypeScript](https://img.shields.io/badge/TypeScript-007ACC?style=for-the-badge&logo=typescript&logoColor=white)](https://www.typescriptlang.org/)

A high-precision, sensor-driven indoor navigation system designed for institutional campuses. This project solves the "indoor GPS blind-spot" by utilizing advanced **Pedestrian Dead Reckoning (PDR)** and custom spatial graph mapping to provide sub-meter accuracy in GPS-denied environments.

---

## 🌟 Key Features

*   **📍 Hardware-Agnostic Navigation:** Uses smartphone Accelerometers, Gyroscopes, and Magnetometers to track movement (step detection & heading) without requiring expensive BLE beacons or hardware infrastructure.
*   **🧠 Intelligent Pathfinding:** Implements **Dijkstra's Algorithm** on a custom spatial node graph to calculate the shortest paths across multiple floors, including stairs and elevators.
*   **🔄 Real-Time Synchronization:** Integrated with **Socket.io** for live position updates and seamless communication between the mobile client and navigation backend.
*   **🗣️ Multi-Lingual Voice Guidance:** Full turn-by-turn spoken instructions available in **English, Hindi, Telugu, Kannada, and Tamil**.
*   **🗺️ Interactive Vector Mapping:** Smooth, high-performance SVG-based floor plans with multi-touch support (zoom/pan).
*   **📴 Offline-First Reliability:** Robust local data handling ensures navigation continues even in campus Wi-Fi dead zones.

---

## 🏗️ System Architecture

The system follows a decoupled **Client-Server** architecture optimized for low latency and high reliability:

### **Mobile Client (React Native + Expo)**
*   **Core:** React Native (Expo) & TypeScript
*   **State Management:** Zustand (High-performance, lightweight state)
*   **Sensors:** Pedestrian Dead Reckoning (PDR) engine via `expo-sensors`
*   **UI/UX:** React Native SVG for map rendering & custom animation systems

### **Backend Engine (Node.js + Express)**
*   **Navigation Engine:** Dijkstra-based pathfinding service
*   **Database:** MongoDB Atlas for persistent storage of spatial nodes and floor data
*   **Real-time:** Socket.io for managing live navigation sessions

---

## 🚀 Getting Started

### **1. Prerequisites**
*   Node.js (v18.x or higher)
*   npm or yarn
*   Expo Go app (on your mobile device)
*   MongoDB instance (local or Atlas)

### **2. Backend Installation**
```bash
cd backend
npm install
# Create a .env file with your MONGODB_URI
npm run seed   # Populate the database with campus map data
npm start      # Launch the navigation engine
```

### **3. Mobile App Installation**
```bash
cd mobile
npm install
# Update API_URL in src/utils/constants.ts to your local IP
npx expo start
```
*Scan the QR code in the terminal using the **Expo Go** app to begin testing.*

---

## 🛠️ Technical Implementation Details

### **Sensor Fusion & PDR**
The application uses a **Kalman Filter** variant to fuse data from the accelerometer (for step counting) and the magnetometer/gyroscope (for heading estimation), creating a relative displacement vector that updates the user's position on the map.

### **Graph-Based Pathfinding**
The building is modeled as a weighted graph where rooms, hallways, and vertical transitions (stairs) are nodes, and the connections between them are edges with weights representing physical distance.

---

## 👥 Project Team

*   **Mr. K. Uday Bhaskar** — Lead Developer & Systems Architect
*   **Ms. P. Sravya** — Project Lead & UI/UX Designer

*Developed for the Department of Electronics & Communication Engineering, Kuppam Engineering College (KEC).*

---
<p align="center">
  Made with ❤️ for KEC
</p>
