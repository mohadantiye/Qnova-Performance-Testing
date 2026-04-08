# 🚀 Qnova.uk Performance Analysis Report
**Project:** Load Testing & Scalability Audit  
**Tools:** Apache JMeter 5.6.3, Git, macOS  

## 📊 Executive Summary
This project evaluates the performance and stability of the `qnova.uk` web server under various concurrent user loads. The objective is to identify the system's breaking point and verify its ability to handle a peak load of 3,000 concurrent sessions.

## 🛠 Test Configuration
| Parameter | Value |
| :--- | :--- |
| **Target URL** | https://qnova.uk |
| **Protocol** | HTTPS / GET |
| **Ramp-up Period** | 60 - 300 Seconds |
| **Environment** | JMeter (Local Machine) |

## 📈 Test Results
| Test Phase | Threads (Users) | Avg Response Time | Error % | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Baseline** | 50 | 1253ms | 0.00% | ✅ PASSED |
| **Scalability** | 100 | 1258ms | 0.00% | ✅ PASSED |
| **Stress Test** | 500 | TBD | TBD | ⏳ PENDING |
| **Peak Load** | 3,000 | TBD | TBD | ⏳ PENDING |

## 📝 Observations
- The server currently shows linear scalability between 50 and 100 users.
- No bottlenecks identified in initial baseline testing.