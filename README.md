<h1 align="center">🛡️ AI Network Threat Intelligence Platform</h1>

<p align="center">
  <img src="https://img.shields.io/badge/Python-3.8+-blue.svg" alt="Python Version">
  <img src="https://img.shields.io/badge/FastAPI-0.68.0+-green.svg" alt="FastAPI">
  <img src="https://img.shields.io/badge/Database-SQLite-lightgrey.svg" alt="SQLite">
  <img src="https://img.shields.io/badge/ML-Threat%20Detection-orange.svg" alt="Machine Learning">
</p>

<p align="center">
  <strong>An intelligent, real-time network monitoring and threat detection system powered by Machine Learning and Graph Algorithms.</strong>
</p>

---

## 🌟 Overview

The **AI Network Threat Intelligence Platform** is a robust backend system designed to simulate, monitor, and analyze network traffic. By combining traditional graph-based network traversal algorithms (BFS, DFS, Dijkstra) with Machine Learning, this platform can dynamically detect anomalies, classify potential threats (e.g., DDoS, Port Scans, Brute Force attacks), and prioritize security alerts in real-time.

Whether you're a cybersecurity enthusiast, a network engineer, or just curious about AI-driven security, this project serves as a comprehensive playground for threat intelligence.

---

## ✨ Key Features

- **🧠 Machine Learning Integration**: Detects and classifies anomalous network behavior in real-time.
- **🌐 Network Graph Algorithms**: Maps and traverses the network topology using Breadth-First Search (BFS) and Depth-First Search (DFS).
- **🛤️ Optimal Routing**: Finds the most efficient path between network nodes using Dijkstra's Algorithm.
- **🚨 Priority Alert System**: Automatically ranks threats based on severity (e.g., DDoS = High Priority) using a custom Priority Queue.
- **📊 Traffic Simulation & Logging**: Generates realistic network traffic patterns and logs them securely into a persistent SQLite database.
- **⚡ High-Performance API**: Built on top of FastAPI for lightning-fast, asynchronous API endpoints.

---

## 🏗️ Architecture & Modules

1. **`main.py`**: The core FastAPI application that orchestrates routing, algorithm execution, and API endpoints.
2. **`database.py`**: Manages the SQLite database schemas (`traffic_logs` and `alerts`) and handles all CRUD operations safely.
3. **`algorithms.py`**: Implements the network graph structure and algorithms (`BFS`, `DFS`, `Dijkstra`), as well as data structures like `AlertPriorityQueue`.
4. **`simulator.py`**: Contains the `TrafficSimulator` which mocks real-world network packets and metadata.
5. **`ml_model.py`**: Houses the `ThreatDetectionModel` which analyzes traffic parameters to predict cyber attacks.

---

## 🚀 Getting Started

### Prerequisites

Make sure you have Python 3.8+ installed.

### Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/SubhamKumarSingh2114/networking_project.git
   cd networking_project
   ```

2. Install the required dependencies:
   ```bash
   pip install fastapi uvicorn requests
   ```
   *(Note: Ensure you have your custom `algorithms`, `simulator`, and `ml_model` modules in your working directory)*

### Running the Server

Start the FastAPI server using Uvicorn:
```bash
uvicorn main:app --reload
```
The server will start at `http://127.0.0.1:8000`.

---

## 🔌 API Endpoints Documentation

Once the server is running, you can access the interactive API documentation (Swagger UI) at `http://127.0.0.1:8000/docs`.

### Core Endpoints

| Method | Endpoint | Description |
| :--- | :--- | :--- |
| `GET` | `/` | Health check and welcome message. |
| `GET` | `/network` | Returns the current network topology (Graph representation). |
| `GET` | `/bfs/{start}` | Performs a Breadth-First Search traversal starting from a specific node. |
| `GET` | `/dfs/{start}` | Performs a Depth-First Search traversal starting from a specific node. |
| `GET` | `/route?source={s}&destination={d}` | Calculates the shortest path between two nodes using Dijkstra's algorithm. |
| `POST`| `/generate` | Generates simulated traffic, runs ML inference, and logs threats/alerts if detected. |
| `GET` | `/alerts` | Retrieves all historical security alerts from the database. |
| `GET` | `/traffic` | Fetches the latest 100 network traffic logs. |
| `GET` | `/top-attackers` | Returns a list of the most frequent malicious IP addresses. |
| `GET` | `/priority-alerts` | Retrieves alerts sorted by their critical severity score. |

---

## 🔒 Security & Data Storage

All network logs and detected threats are securely stored in a local SQLite database (`network.db`). 
- **Traffic Logs**: Captures Source IP, Protocol, Duration, Packet Count, Bytes transferred, and Attack Classification.
- **Alerts Table**: Stores Threat Name, AI Confidence Score, and the Source IP of the attacker.

---

## 🤝 Contributing

Contributions, issues, and feature requests are welcome! Feel free to check the [issues page](https://github.com/SubhamKumarSingh2114/networking_project/issues). 

1. Fork the Project
2. Create your Feature Branch (`git checkout -b feature/AmazingFeature`)
3. Commit your Changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the Branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

---

<p align="center">
  <i>Built with ❤️ by Subham Kumar Singh</i>
</p>
