# DetectandBlockMaliciousTrafficinSimulatedNetowrk

---

## 🧪 Lab Project: **"Detecting and Blocking Malicious Traffic in a Simulated Network"**

This project includes:
✅ Networking setup with **VLANs and routing**
✅ Simulated malicious traffic using **attack emulation tools** (e.g., Kali Linux ping flood, or Nmap scan)
✅ Defensive configuration: **ACLs**, **port security**, or **firewall rules**
✅ Basic **packet analysis** with **Wireshark**
✅ Final documentation for GitHub

---

### 🔧 Tools Needed:

* Cisco Packet Tracer (or GNS3 if you want more realism)
* Wireshark (for packet capture)
* Optionally, a Kali Linux VM or TryHackMe’s AttackBox (for simulated attacks)

---

## 🏗️ Lab Idea: "Stop the Attack – VLANs, ACLs, and Ping Floods"

### 🖼️ Scenario:

> A small company’s internal network is divided into VLAN 10 (Finance) and VLAN 20 (Engineering). An attacker plugs a device into an open port and floods the network with ICMP traffic, disrupting operations. As the network admin, your job is to:

* Detect the attack
* Isolate the attacker
* Prevent it from happening again using networking techniques

---

### 💡 Skills This Lab Demonstrates:

* VLAN creation and segmentation
* Inter-VLAN routing (Router-on-a-Stick)
* Basic access control lists (ACLs) for ICMP blocking
* Port security or MAC address filtering
* Wireshark packet analysis
* Attack detection mindset

---

## ✅ Step-by-Step Lab Plan

---

### 1. **Create the Network**

* 1 switch, 1 router
* PCs in:

  * VLAN 10 (Finance): PC0, PC1
  * VLAN 20 (Engineering): PC2, PC3
  * Attacker: PC4 (plugged into an unused switch port)

Use `interface range` and `switchport access vlan` to assign VLANs
Use `encapsulation dot1Q` for Router-on-a-Stick
Assign IPs:

* VLAN 10: `192.168.10.x`
* VLAN 20: `192.168.20.x`
* Router subinterfaces: `.1` for each VLAN

---

### 2. **Test Ping Between VLANs**

* Confirm PCs can ping each other
* Confirm inter-VLAN routing works

---

### 3. **Simulate an Attack**

* On PC4 (the attacker), continuously ping all IPs (`ping 192.168.10.1 -t`)
* Observe in Wireshark: capture traffic on the switch or router

---

### 4. **Detect the Attack**

* Use Wireshark to identify:

  * High ICMP traffic from PC4
  * Destination IPs being flooded
* Take a screenshot for GitHub

---

### 5. **Defend**

Pick one or more defenses:

* 🧱 **ACL on router** to block ICMP from attacker IP

  ```bash
  access-list 100 deny icmp host 192.168.30.4 any
  access-list 100 permit ip any any
  interface g0/0.30
  ip access-group 100 in
  ```
* 🛑 **Port Security** on switch

  ```bash
  interface fa0/5
  switchport port-security
  switchport port-security maximum 1
  switchport port-security mac-address sticky
  switchport port-security violation shutdown
  ```

---

### 6. **Retest and Document**

* Show that attack no longer works
* Show clean packet capture
* Document:

  * Network diagram
  * Configs
  * Wireshark screenshots
  * What you did + why it matters

---

## 📁 GitHub Folder Structure

```
cyber-network-defense-lab/
├── README.md
├── packet-tracer-files/
│   └── attack-defend-network.pkt
├── wireshark-captures/
│   ├── before-defense.pcapng
│   └── after-defense.pcapng
├── configs/
│   ├── switch-config.txt
│   └── router-config.txt
└── images/
    └── network-diagram.png
```

---

## ✅ Outcome

You’ll finish with:

* A portfolio-ready lab on GitHub
* Hands-on with VLANs, ACLs, and network defense
* Evidence of practical cybersecurity thinking

---

We can go one step at a time. I can walk you through the **Packet Tracer network setup**, then **attack simulation**, then **defense**, and finally the **GitHub writeup**.
Would you like to begin with step 1: **Building the network in Packet Tracer**?
