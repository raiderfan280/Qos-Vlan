
# VLAN-Based QoS for VoIP Traffic in Cisco Packet Tracer

## 📚 Overview

This lab demonstrates how to configure Quality of Service (QoS) in a small office network using VLANs to prioritize VoIP traffic. The environment is built in Cisco Packet Tracer and aligns with concepts tested in the **CompTIA Network+** certification.

---

## 🎯 Objective

To gain hands-on experience configuring:

- VLANs for voice and data separation
- Basic QoS through VLAN prioritization
- DHCP for automatic IP assignment
- Trunking and access ports for VoIP-enabled ports
- VoIP support using Cisco IP Phones in Packet Tracer

---

## 🖥️ Lab Topology

- **1 Router (DHCP + Inter-VLAN Routing)**
- **1 Layer 2 Switch**
- **2 IP Phones + PCs (connected through IP Phone passthrough)**
- **VLANs**
  - VLAN 1: Data
  - VLAN 10: Voice (QoS prioritization)

---

## 📁 File Structure

```
vlan-qos-voip-lab/
├── VoIP_QoS_Lab.pkt               # Packet Tracer project file
├── README.md                      # This file
├── configs/
│   ├── router-config.txt          # Router configuration
│   └── switch-config.txt          # Switch configuration
└── screenshots/
    ├── phone_vlan_config.png      # Screenshot of phone config
    └── dhcp_binding_check.png     # Screenshot of DHCP bindings
```

---

## ⚙️ Key Configurations

### 🛠️ Switch Port Setup (example for Fa0/2)
```shell
mls qos

interface FastEthernet0/2
 switchport mode access
 switchport access vlan 1
 switchport voice vlan 10
 mls qos trust device cisco-phone
 mls qos trust cos
 spanning-tree portfast
```

### 🌐 Router Subinterface & DHCP
```shell
interface g0/0.10
 encapsulation dot1Q 10
 ip address 10.10.10.1 255.255.255.0

ip dhcp pool VOICE
 network 10.10.10.0 255.255.255.0
 default-router 10.10.10.1
```

---

## 🧪 How to Use This Lab

1. Open the `.pkt` file in Cisco Packet Tracer.
2. Power on devices and wait for phones to register IPs.
3. Check IP Phone VLAN settings and DHCP assignment.
4. Use `show vlan`, `show ip dhcp binding`, and `show interfaces trunk` for verification.
5. Modify and expand the lab for advanced scenarios (e.g., inter-VLAN routing, more phones, video QoS).

---

## ✅ Learning Outcomes

- Understand VLAN-based QoS in constrained simulation environments.
- Configure voice VLANs and trust settings.
- Troubleshoot IP phones stuck in DHCP or VLAN registration.
- Align lab work with Network+ exam topics.

---

## 🔐 Notes

Due to Packet Tracer limitations, advanced QoS features like DSCP marking or class-based shaping are not implemented. This lab uses **VLAN-based traffic separation** to simulate prioritization of VoIP traffic.

---

## 📸 Screenshots

| IP Phone VLAN Settings | DHCP Binding Table |
|------------------------|---------------------|
| ![](screenshots/phone_vlan_config.png) | ![](screenshots/dhcp_binding_check.png) |

---

## 📜 License

This lab is free to use for educational and certification study purposes.

---

## 🙋‍♂️ Author

Maintained by [@raiderfan280](https://github.com/raiderfan280) — feel free to fork, star ⭐, or submit PRs!
