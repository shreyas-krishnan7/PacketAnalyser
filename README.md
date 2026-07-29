# 🚀 DPI Engine — Multi-Threaded Deep Packet Inspection Framework

> **C++17 | Multithreading | PCAP | TCP/IP | TLS | SNI | CMake**

A high-performance Deep Packet Inspection (DPI) engine that processes offline PCAP captures, parses network protocols, identifies application traffic, tracks flows using the Five-Tuple, extracts TLS SNI information, and applies configurable filtering policies. The project includes both a single-threaded reference implementation and a scalable multithreaded processing pipeline.

---

# 📌 Overview

This project demonstrates the core building blocks of a modern DPI system:

- Offline PCAP packet processing
- Ethernet, IPv4, TCP and UDP parsing
- Stateful flow tracking
- TLS Server Name Indication (SNI) extraction
- Application identification
- Rule-based packet filtering
- Multi-threaded packet processing architecture

---

# ✨ Features

- PCAP Reader
- Ethernet / IPv4 / TCP / UDP Parser
- TLS Client Hello SNI Extraction
- HTTP Host Header Parsing
- Five-Tuple Flow Tracking
- Rule-based Filtering (IP, Domain, Application)
- Application Classification
- Producer–Consumer Architecture
- Thread-safe Queues
- Scalable Multi-threaded Execution
- Processing Statistics & Reports

---

# 🏗️ System Architecture

```text
                Input PCAP
                     │
                     ▼
              Packet Reader
                     │
         ┌───────────┴───────────┐
         ▼                       ▼
   Load Balancer 1         Load Balancer 2
         │                       │
    ┌────┴────┐             ┌────┴────┐
    ▼         ▼             ▼         ▼
 FastPath  FastPath     FastPath  FastPath
    │         │             │         │
    └─────────┴─────────────┴─────────┘
                    │
                    ▼
              Output Writer
                    │
                    ▼
              Filtered PCAP
```

---

# ⚙️ Packet Processing Pipeline

```text
Input PCAP
     │
     ▼
Read Packet
     │
     ▼
Parse Ethernet/IP/TCP/UDP
     │
     ▼
Generate Five-Tuple
     │
     ▼
Flow Lookup
     │
     ▼
Extract TLS SNI / HTTP Host
     │
     ▼
Application Classification
     │
     ▼
Rule Evaluation
     │
     ▼
Forward or Drop Packet
```

---

# 📂 Repository Structure

```text
packet_analyzer/
│
├── include/
│   ├── pcap_reader.h
│   ├── packet_parser.h
│   ├── sni_extractor.h
│   ├── connection_tracker.h
│   ├── rule_manager.h
│   ├── fast_path.h
│   ├── load_balancer.h
│   ├── dpi_engine.h
│   └── thread_safe_queue.h
│
├── src/
│   ├── main_working.cpp
│   ├── dpi_mt.cpp
│   ├── packet_parser.cpp
│   ├── pcap_reader.cpp
│   ├── sni_extractor.cpp
│   └── types.cpp
│
├── test_dpi.pcap
├── generate_test_pcap.py
└── README.md
```

---

# 🛠️ Technology Stack

| Category | Technology |
|----------|------------|
| Language | C++17 |
| Networking | Ethernet, IPv4, TCP, UDP |
| Security | TLS, SNI Inspection |
| Packet Capture | PCAP |
| Concurrency | std::thread, mutex, condition_variable |
| Build | CMake / g++ |
| Version Control | Git |

---

# 🚀 Build

## Linux / macOS

```bash
mkdir build
cd build
cmake ..
make
```

## Windows

```bash
mkdir build
cd build
cmake ..
cmake --build .
```

---

# ▶️ Run

```bash
./dpi_engine input.pcap output.pcap
```

Block applications

```bash
./dpi_engine input.pcap output.pcap --block-app YouTube
```

Block domains

```bash
./dpi_engine input.pcap output.pcap --block-domain facebook
```

Block IP

```bash
./dpi_engine input.pcap output.pcap --block-ip 192.168.1.100
```

---

# 🔍 Core Components

| Module | Responsibility |
|---------|----------------|
| PCAP Reader | Reads packets from capture files |
| Packet Parser | Parses Ethernet/IP/TCP/UDP headers |
| Flow Tracker | Maintains connection state |
| SNI Extractor | Extracts TLS Server Name |
| Rule Manager | Applies filtering policies |
| Fast Path | Packet processing workers |
| Load Balancer | Distributes packets across workers |

---

# 📊 Sample Report

```text
Packets Processed : 77
Forwarded         : 69
Dropped           : 8

Detected Applications
---------------------
HTTPS
YouTube
Facebook
Google
DNS
Unknown

Detected Domains
----------------
www.youtube.com
www.facebook.com
github.com
```

---

# 🚀 Technical Highlights

- Stateful Five-Tuple flow tracking
- TLS SNI based application detection
- HTTP Host header extraction
- Rule-based packet filtering
- Concurrent packet processing using producer–consumer queues
- Consistent hashing for flow affinity
- Thread-safe queue implementation
- Offline PCAP traffic analysis

---

# 📈 Future Improvements

- HTTP/3 & QUIC support
- IPv6 packet parsing
- Live interface packet capture
- Web dashboard
- Rule persistence
- Performance benchmarking
- IDS/IPS integration

---

# 📄 License

This repository is intended for educational and research purposes.
