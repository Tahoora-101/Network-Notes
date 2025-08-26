# OSI Model

The **Open Systems Interconnection (OSI) Model** is a framework that explains how data moves through a network using **7 layers**.

---

## Layers
**1. Application (Layer 7)** – User interface *(browsers, email)*  
**2. Presentation (Layer 6)** – Data format, encryption *(SSL/TLS)*  
**3. Session (Layer 5)** – Manages sessions  
**4. Transport (Layer 4)** – Reliable delivery *(TCP/UDP)*  
**5. Network (Layer 3)** – Routing & addressing *(IP)*  
**6. Data Link (Layer 2)** – Node-to-node transfer *(Ethernet, MAC)*  
**7. Physical (Layer 1)** – Hardware, cables, signals  

---

## Mnemonic
👉 **All People Seem To Need Data Processing**

<p align="center">
  <img src="https://github.com/user-attachments/assets/90be3546-4386-4d98-a062-27ad9b573138" alt="OSI model" width="800"/>
</p

---

## Layer 1 – Physical

The **Physical Layer** is the foundation of networking.  
It handles the **physical transmission of data** through cables, signals, and hardware.  

### Key Points
- Concerned with **signaling, cabling, connectors**  
- Devices: **hubs, repeaters, media converters**  
- Focuses on *hardware, not protocols*  

### Issues
- “Physical layer problem” = bad cables, connectors, or adapters  

### Troubleshooting
- Run **loopback tests**  
- Test/replace **cables**  
- Swap **adapter cards**  
- Fix **punch-downs/physical connections**

---

## Layer 2 – Data Link (Switching)

The **Data Link Layer** handles the **basic network communication** between devices on the same network segment. It defines how data is formatted for transmission and how access to the physical medium is controlled.  

### Key Points
- Provides the **foundation of communication** at this layer  
- Uses **Data Link Control (DLC) protocols**  
- **MAC (Media Access Control)** is key in Ethernet  
- Known as the **“switching” layer**  

### Issues
- Collisions and broadcast storms  
- Duplicate MAC addresses  
- Faulty switches or misconfigurations  

### Troubleshooting
- Check switch configurations  
- Verify **MAC address tables**  
- Replace faulty cables/switches  
- Monitor for **excessive broadcasts**

---

## Layer 3 – Network (Routing)

The **Network Layer** is the **“routing” layer**, responsible for moving data between different networks. It uses logical addressing to decide where packets go.  

### Key Points
- Uses the **Internet Protocol (IP)** for addressing and delivery  
- Handles **routing** across multiple networks  
- **Fragments frames** into smaller IP packets so data can traverse networks with different size limits  

### Issues
- Incorrect IP addressing/subnetting  
- Routing loops or unreachable networks  
- Packet fragmentation causing drops  

### Troubleshooting
- Verify IP addresses and subnet masks  
- Check routing tables and configurations  
- Use tools like **ping**, **traceroute** to test connectivity  
- Monitor for excessive fragmentation

---

## Layer 4 – Transport

The **Transport Layer** is the **“post office”** of networking. It ensures data is delivered correctly, either reliably or quickly depending on protocol.  

### Key Points
- **TCP (Transmission Control Protocol):** Reliable, connection-oriented  
- **UDP (User Datagram Protocol):** Fast, connectionless  
- Breaks data into segments and reassembles them at the destination  

### Issues
- Port misconfigurations  
- Dropped or out-of-order packets  
- Application not responding on correct port  

### Troubleshooting
- Use `netstat` or `ss` to check active ports  
- Packet analysis with **Wireshark**  
- Verify firewall/ACL rules  

---

## Layer 5 – Session

The **Session Layer** manages communication between devices—establishing, maintaining, and ending sessions.  

### Key Points
- Controls dialogue between two systems  
- Supports **control protocols** and **tunneling protocols**  
- Handles start, stop, and restart of sessions  

---

## Layer 6 – Presentation

The **Presentation Layer** is the **translator**. It formats and secures data for the application layer.  

### Key Points
- Character encoding (ASCII, Unicode)  
- Data compression  
- Application-level encryption (**SSL/TLS**)  
- Often combined with the Application Layer in practice  

---

## Layer 7 – Application

The **Application Layer** is what users interact with directly—the services and apps we see.  

### Examples
- **HTTP/HTTPS** – Web browsing  
- **FTP** – File transfers  
- **DNS** – Domain name resolution  
- **SMTP/POP3/IMAP** – Email

---
## OSI Layers – Reference

| Layer | Function | Key Components / Protocols | Real-World Example | Encapsulation Unit |
|-------|---------|----------------------------|------------------|------------------|
| Application (7) | Interface with user & apps | HTTP, FTP, DNS, POP3, SMTP | Web browsing, email | Data |
| Presentation (6) | Data formatting & encryption | SSL/TLS, character encoding | Application encryption | Data |
| Session (5) | Session management | Control protocols, tunneling protocols | Login sessions, remote desktop | Data |
| Transport (4) | Reliable or fast delivery | TCP, UDP | File transfer, streaming | Segment |
| Network (3) | Routing & addressing | IP, ICMP, Router | Internet traffic, packet forwarding | Packet |
| Data Link (2) | Node-to-node transfer | MAC address, Switch, Bridge, NIC, ARP | LAN communication | Frame |
| Physical (1) | Physical transmission | Cables, fibers, Hub, Repeater, Media Converter | Wired & wireless connectivity | Bits |




