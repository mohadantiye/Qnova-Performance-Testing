# 🚀 Qnova.uk Performance Analysis Report
**Project:** Load Testing & Scalability Audit  
**Author:** Muhammad Nasir Dantiye
**Tools:** Apache JMeter 5.6.3 (CLI Mode), Git, macOS  

## 📊 Executive Summary
This project evaluates the performance and stability of the `qnova.uk` web server. While the server showed excellent stability up to 500 users, the local testing environment reached a physical thread limit at 2,016 concurrent users.

## 🛠 Test Configuration
| Parameter | Value |
| :--- | :--- |
| **Target URL** | https://qnova.uk |
| **Protocol** | HTTPS / GET |
| **Ramp-up Period** | 60 - 300 Seconds |
| **Environment** | macOS (Local CLI Mode) |

## 📈 Test Results
| Test Phase | Threads (Users) | Avg Response Time | Error % | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Baseline** | 50 | 1253ms | 0.00% | ✅ PASSED |
| **Scalability** | 100 | 1258ms | 0.00% | ✅ PASSED |
| **Stress Test** | 500 | 1331ms | 0.00% | ✅ PASSED |
| **Peak Load** | 3,000 | 916ms* | 73.83%* | ⚠️ LIMIT REACHED |

## 🔍 Bottleneck Analysis
- **Hardware Limitation:** During the 3,000-user peak test, the local machine failed to spawn new threads after reaching **2,016 active users**. 
- **Error Log:** `pthread_create failed (EAGAIN)` - This indicates the macOS kernel limit for processes/threads was reached.
- **Server Response:** Up until the hardware crash, the server (`qnova.uk`) maintained an average response time of under **1.4s**, suggesting high server-side efficiency.

## 📝 Recommendations
1. **Distributed Testing:** To test the full 3,000-user capacity, a "Master-Slave" JMeter configuration using multiple load generators is required.
2. **Kernel Tuning:** For further local testing, macOS `maxfiles` and `maxproc` limits should be increased via `sysctl`.