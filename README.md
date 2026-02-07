# EE533_LAB4
EE533_LAB4
# NetFPGA Lab: Hardware Router & Mini-IDS Implementation

This repository contains the source code, scripts, and experimental results for the NetFPGA 1G Reference Router and Mini-Intrusion Detection System (IDS) labs.

## 📖 Project Overview

This project explores the performance differences between **Software Routing (kernel-space)** and **Hardware Routing (FPGA-based)**. It culminates in the design and implementation of a hardware-accelerated Mini-IDS capable of filtering malicious traffic at line rate.

### Key Features
* **Performance Benchmarking:** Comparison of throughput and latency between Reference NIC (Host CPU) and Reference Router (FPGA).
* **Hardware Acceleration:** Implementation of a full IPv4 Router on NetFPGA hardware.
* **Mini-IDS:** A custom Verilog module that inspects packet payloads in real-time to drop malicious patterns (e.g., "ABCDEFG").
* **Perl Control Interface:** A register interface (`idsreg`) to dynamically configure firewall rules.

---

## 🛠️ System Architecture

**Hardware Setup:**
* **1x NetFPGA Node (`nf2`):** Hosting the NetFPGA 1G card.
* **4x Traffic Generators (`n0` - `n3`):** PCs connected to the NetFPGA ports generating TCP/UDP traffic.
* **Topology:** Star topology where all traffic passes through the NetFPGA node.

**Software/Tools:**
* **OS:** CentOS / Ubuntu (with NetFPGA kernel modules)
* **Language:** Verilog (Hardware), C/Perl (Software), Bash (Scripts)
* **Testing Tools:** `iperf`, `tcpdump`, `ping`

---

## 🚀 Getting Started

### 1. Hardware Router Setup
To load the reference router bitfile and start the routing daemon:

```bash
# On NetFPGA Node (nf2)
nf_download /usr/local/netfpga/bitfiles/reference_router.bit
/usr/local/netfpga/lib/C/router/rkd -cpci &
