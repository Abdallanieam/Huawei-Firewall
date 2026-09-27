# 🛡️ Huawei Firewall Hot Standby (VRRP/HRP) & NAT Lab

## 📌 Student Details

**Student Name:** Abdalla Mohamed Nieam
**Platform:** Huawei eNSP
**Task:** Task 3

---

## 📖 Overview

This project demonstrates the configuration and verification of a Huawei Firewall network using **VRRP, HRP, Source NAT, and Static NAT**.

The lab was implemented using **Huawei eNSP** and focuses on firewall high availability, network segmentation, NAT configuration, and connectivity verification.

---

## 🏗️ Network Topology

The network is divided into three main security zones:

### 🔵 Trust Zone

**Network:** `10.1.0.0/16`

Contains the internal network clients from **PC1 to PC7**.

The virtual gateway for the Trust zone is:

`10.1.0.254`

### 🟢 DMZ Zone

**Network:** `10.2.2.0/24`

The DMZ contains the internal servers:

* **FTP Server:** `10.2.2.1`
* **HTTP Server:** `10.2.2.3`
* **Virtual Gateway:** `10.2.2.254`

### 🔴 Untrust Zone

**Network:** `30.3.3.0/24`

This zone represents the external/public network.

---

## 🔄 High Availability – VRRP & HRP

Two Huawei firewalls are configured in a High Availability design:

* **FW1:** Master
* **FW2:** Backup

VRRP provides virtual gateway addresses for the internal networks.

### Virtual Gateways

| Zone  | Virtual Gateway |
| ----- | --------------- |
| Trust | `10.1.0.254`    |
| DMZ   | `10.2.2.254`    |

Under normal operation, **FW1** handles the active traffic.

If FW1 or its active link fails, **FW2** takes over the virtual gateway through VRRP.

### HRP Synchronization

**HRP (Huawei Redundancy Protocol)** is used to synchronize firewall state information between FW1 and FW2.

The HRP heartbeat is configured through:

`GE 1/0/3`

This allows the firewalls to synchronize information such as session and state information.

---

## 🌐 NAT Configuration

### Source NAT

Source NAT is configured to allow internal Trust network hosts to access external networks.

The internal network:

`10.1.0.0/16`

is translated to public addresses in the range:

`2.2.2.2 – 2.2.2.3`

This allows internal clients to communicate with external networks without exposing their private IP addresses.

---

## 🖥️ Static Server NAT

Static NAT is configured to publish internal DMZ servers to the external network.

### FTP Server

Internal address:

`10.2.2.1`

Public address:

`30.3.3.100`

### HTTP Server

Internal address:

`10.2.2.3`

Public address:

`30.3.3.200`

This allows external users to access the required services using the public IP addresses.

---

## 🧪 Verification & Testing

Several tests were performed to verify the configuration.

### 1. Firewall Session Verification

Firewall sessions were checked using:

`display firewall session table`

This command was used to verify active network sessions passing through the firewall.

### 2. Connectivity Testing

Ping tests were performed between the different network zones to verify connectivity between:

* Trust
* DMZ
* Untrust

### 3. High Availability Testing

A failure test was performed by shutting down:

`GE 1/0/1`

on **FW1**.

After the failure, **FW2** took over the active role through the configured VRRP/HRP high-availability mechanism.

---

## 📊 Network Address Summary

| Device / Service      | IP Address          |
| --------------------- | ------------------- |
| Trust Virtual Gateway | `10.1.0.254`        |
| DMZ Virtual Gateway   | `10.2.2.254`        |
| FTP Server            | `10.2.2.1`          |
| HTTP Server           | `10.2.2.3`          |
| FTP Public IP         | `30.3.3.100`        |
| HTTP Public IP        | `30.3.3.200`        |
| Source NAT Range      | `2.2.2.2 – 2.2.2.3` |

---

## 📸 Lab Screenshots

### 🔹 Huawei eNSP Topology

The following screenshot shows the complete network topology implemented in Huawei eNSP.

![Huawei eNSP Topology](./images/topology.png)

### 🔹 Firewall Configuration

This screenshot shows the firewall configuration used in the lab.

![Firewall Configuration](./images/firewall-configuration.png)

### 🔹 VRRP & HRP

This screenshot demonstrates the High Availability configuration between FW1 and FW2.

![VRRP and HRP](./images/vrrp-hrp.png)

### 🔹 NAT Configuration

This screenshot shows the Source NAT and Static NAT configuration.

![NAT Configuration](./images/nat.png)

### 🔹 Verification

The following screenshot shows the verification commands and connectivity tests.

![Verification](./images/verification.png)

---

## 📁 Repository Files

### 📄 Complete Report

[**Huawei-Firewall.pdf**](./Huawei-Firewall.pdf)

Contains the complete step-by-step configuration, screenshots, and command outputs.

### 📦 eNSP Project

[**Huawei-Firewall.rar**](./Huawei-Firewall.rar)

Contains the Huawei eNSP topology and project files.

---

## 🛠️ Technologies & Tools

* Huawei eNSP
* Huawei Firewall USG
* VRRP
* HRP
* Source NAT
* Static NAT
* FTP
* HTTP
* Network Security
* High Availability

---

## 👨‍💻 Author

**Abdalla Mohamed Nieam**

Network & Security Engineer

GitHub: [@Abdallanieam](https://github.com/Abdallanieam)

---

## ⭐ Project Summary

This lab demonstrates a practical Huawei Firewall implementation combining **High Availability, VRRP, HRP, Network Address Translation, DMZ services, and connectivity testing** in a simulated enterprise network environment.
