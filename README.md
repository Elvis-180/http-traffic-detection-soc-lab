# HTTP Traffic Monitoring with Snort and Splunk

## Table of Contents
1. [Project Overview](#project-overview)
2. [Objective](#objective)
3. [Architecture / Environment Setup](#architecture--environment-setup)
4. [Tools Used](#tools-used)
5. [Attack / Simulation Scenario](#attack--simulation-scenario)
6. [Detection & Analysis](#detection--analysis)
7. [Key Findings](#key-findings)
8. [Screenshots](#screenshots)
9. [Lessons Learned](#lessons-learned)

---

## project Overview
This project simulates HTTP traffic monitoring within a segmented virtual network environment using Snort IDS and Splunk SIEM. The objective was to generate, detect, and analyze HTTP-based network activity in order to improve visibility into web traffic patterns and potential malicious behavior.

---

## Objective
- Monitor HTTP traffic across a controlled lab network
- Detect suspicious or abnormal web activity using Snort rules
- Centralize and analyze IDS alerts in Splunk
- Improve understanding of network-based detection and traffic analysis workflows

---

## Architecture / Environment Setup
The lab environment was built using a segmented virtual network architecture consisting of:

- pfSense firewall for traffic routing and segmentation
- Ubuntu Server running Snort IDS
- Splunk SIEM for centralized log collection and analysis
- Windows server with web server (IIS)
- Kali linux as attacker machine
- windows 10 as domain computer
- Ubuntu server, Windows server, windows 10 are in thesame network (Internal network (LAN)) with with ip range 192.168.1.0/24 and kali linux is external network (OPT1) with ip range 192.168.2.0/24

Traffic generated from the client system traversed the firewall and was inspected by Snort before logs were forwarded into Splunk for analysis.

---

## Tools Used
- Splunk SIEM
- Snort IDS
- pfSense
- Ubuntu Server
- Windows Server / Windows Client
- Kali Linux

---

## Attack / Simulation Scenario
From Kali linux, an attack is simulated on web server (IIS) found in Windows server machine, HTTP traffic was generated from a Windows system to simulate web activity across the network. 

The generated alerts were forwarded to Splunk (SIEM), were it  monitored activity and analyze traffic behavior in real time.

---

## Detection & Analysis

### IDS Analysis (Snort)
- Configured custom HTTP detection rules
- Monitored inbound and outbound HTTP requests
- Generated alerts based on detected traffic patterns

### SIEM Analysis (Splunk)
- Ingested Snort logs into Splunk
- Queried HTTP-related events from the `main` index
- Visualized traffic activity using and SPL queries
- Analyzed source IP behavior and traffic frequency

---

## Key Findings
- Snort successfully detected HTTP traffic generated within the lab environment
- Splunk provided centralized visibility into IDS-generated alerts
- Traffic analysis improved understanding of IDS and SIEM integration workflows

--- 

## Screenshots
- HTTP Alerts
  <img width="1920" height="1080" alt="Screenshot 2026-05-08 132035" src="https://github.com/user-attachments/assets/a71a22e7-d7a7-448a-87d0-5ec266f31f1f" />

---

## Lessons Learned
- IDS tools provide packet-level visibility while SIEM platforms provide centralized analysis
- Proper log forwarding and indexing are critical for effective monitoring
- Network segmentation impacts how traffic is observed and interpreted
- Detection engineering requires both technical configuration and analytical validation

