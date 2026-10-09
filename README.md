<h1 align="center">🛡️ AI Network Threat Intelligence Platform</h1>

<p align="center">
  <img src="https://img.shields.io/badge/Python-3.8+-3776AB?style=for-the-badge&logo=python&logoColor=white" alt="Python Version">
  <img src="https://img.shields.io/badge/FastAPI-0.68.0+-009688?style=for-the-badge&logo=fastapi&logoColor=white" alt="FastAPI">
  <img src="https://img.shields.io/badge/Scikit--Learn-Random%20Forest-F7931E?style=for-the-badge&logo=scikit-learn&logoColor=white" alt="Scikit Learn">
  <img src="https://img.shields.io/badge/Database-SQLite-003B57?style=for-the-badge&logo=sqlite&logoColor=white" alt="SQLite">
  <img src="https://img.shields.io/badge/DSA-Graph%20%2B%20Heaps-blueviolet?style=for-the-badge" alt="DSA">
</p>

<p align="center">
  <strong>Production-grade, asynchronous backend system bridging Machine Learning classification with classical graph algorithms to simulate, intercept, and mitigate cyber threats in real-time.</strong>
</p>

---

## 📄 Abstract

The **AI Network Threat Intelligence Platform** is an intelligent network security system designed to simulate, analyze, and detect malicious network activities in real time. The system integrates machine learning, data structures and algorithms, network simulation, database management, and a FastAPI-based backend to provide an end-to-end framework for network threat monitoring.

The system uses a **network traffic simulator** to generate both normal and malicious traffic, including **DDoS, Port Scan, and Brute Force attacks**, using features such as packet count, byte volume, connection count, packet rate, byte rate, duration, and communication protocol. The generated traffic is analyzed by a **Random Forest Classifier**, which predicts the type of network activity and provides a confidence score for the prediction.

To complement machine learning-based detection, the platform incorporates **graph-based network analysis**. Routers and their connections are represented as a weighted graph, enabling **BFS and DFS traversal, Dijkstra's shortest-path routing, connected-component analysis, and identification of affected nodes** in a compromised network. The system also uses a **priority queue** to organize security alerts according to threat severity and a counter-based mechanism to identify frequently occurring attacking IP addresses.

Detected traffic and security alerts are persistently stored using an **SQLite database**, maintaining traffic logs, attack types, alert confidence, and source IP information. The entire system is exposed through a **FastAPI backend**, providing APIs for network information, graph traversal, shortest-path analysis, traffic generation, threat prediction, alert retrieval, traffic logs, top attackers, and prioritized alerts.

Overall, the project demonstrates how **Artificial Intelligence and classical Data Structures and Algorithms can be integrated into a practical cybersecurity system**. By combining automated traffic generation, machine learning-based threat classification, graph-based network analysis, prioritized alert management, and persistent monitoring, the platform provides a modular foundation for intelligent network security and threat intelligence applications.

---

## 🏗️ System Architecture & Workflow

```text
       [ Network Traffic Generator ]
                     │
      (Packet / Byte / Protocol Flow)
                     ▼
         [ Feature Preprocessing ]
                     │
        ┌────────────┴────────────┐
        ▼                         ▼
[ ML Threat Classifier ]    [ Graph Topology Engine ]
  • Random Forest Model       • Dijkstra Optimal Path
  • Anomaly Prediction        • BFS / DFS Reachability
  • Confidence Scoring        • Blast Radius Analysis
        │                         │
        └────────────┬────────────┘
                     ▼
       [ Priority Alert Queue (Heap) ]
                     │
        ┌────────────┴────────────┐
        ▼                         ▼
 [ SQLite Audit Store ]     [ FastAPI REST Endpoints ]
  • Traffic History          • Real-time Inference API
  • Alert Logs               • Interactive Swagger UI
```

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
