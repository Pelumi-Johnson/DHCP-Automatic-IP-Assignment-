# 🖧 Day 5 | DHCP (Automatic IP Assignment)

## 🎯 Objective
Understand how devices automatically receive IP addresses and how networks eliminate manual configuration through DHCP.

---

## 🧠 Core Idea
DHCP allows the network to assign identity to devices automatically.

Instead of manually configuring each device, the network provides IP addressing dynamically.

---

## 🌐 How DHCP Works (DORA Process)

- Discover → device asks for an IP address  
- Offer → DHCP server provides an available IP  
- Request → device accepts the offer  
- Acknowledge → server confirms the assignment  

This process allows devices to join the network without manual setup.

### 📸 DHCP Process Visualization
![DHCP Flow](dhcp-flow.png)

---

## 🧪 Lab Setup
Rebuilt the network from memory using:
- 1 Router
- 1 Switch
- 2 PCs

### 📸 Network Topology
![Topology](topology.png)

---

## ⚙️ DHCP Configuration (Router as Server)

Configured the router to act as a DHCP server:

enable  
configure terminal  

ip dhcp pool NETWORKPOOL  
network 192.168.1.0 255.255.255.0  
default-router 192.168.1.1  
dns-server 8.8.8.8  
exit  

interface gigabitEthernet 0/0  
ip address 192.168.1.1 255.255.255.0  
no shutdown  

### 📸 DHCP Configuration on Router
![Router DHCP Config](router-dhcp.png)

---

## 🧠 What Was Done

- Created a DHCP pool
- Defined the network range
- Assigned default gateway and DNS
- Enabled the router interface

This transformed the router into a DHCP server.

---

## 🖥️ Automatic IP Assignment

Set both PCs to DHCP:

Desktop → IP Configuration → DHCP

### 📸 PC Receiving IP Automatically
![PC DHCP Assignment](pc-dhcp.png)

---

## 📡 Connectivity Test

Tested communication between devices using ping.

### 📸 Successful Communication
![Ping Test](ping-success.png)

---

## 💥 Failure Scenario (DHCP Disabled)

Disabled DHCP on the router:

no ip dhcp pool NETWORKPOOL  

Then set PCs to DHCP again.

### 📸 APIPA Address (No DHCP)
![APIPA Address](apipa.png)

---

## 🧠 What Happened

Devices assigned themselves IPs in the range:
169.254.x.x

This is APIPA (Automatic Private IP Addressing).

It indicates that no DHCP server is available on the network.

---

## 🧠 Key Concepts Learned

- DHCP automatically assigns IP addresses to devices
- The DORA process enables communication between client and server
- Routers can function as DHCP servers
- Without DHCP, devices fall back to APIPA addressing
- DHCP reduces manual configuration and simplifies network management

---

## 🔁 Practical Reinforcement

- Rebuilt the network from memory
- Configured DHCP on the router
- Verified automatic IP assignment
- Tested connectivity
- Disabled DHCP to observe failure behavior
- Identified APIPA as fallback mechanism

---

## ✅ Outcome

Developed a clear understanding of how DHCP enables automatic IP assignment and how network services provide intelligence and scalability.

This lab reinforced how modern networks manage identity without manual configuration.
