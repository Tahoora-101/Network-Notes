# 🌐 OSI Model

The **Open Systems Interconnection (OSI) Model** is a framework that explains how data moves through a network using **7 layers**.  
Think of it like a recipe: each layer has a job, and together they let data travel from one device to another.

---

## 📝 Mnemonic
**All People Seem To Need Data Processing** ✅  
*(Top → Bottom: Application → Physical)*

---

<details>
<summary><strong>💡 Beginner Analogy</strong> (Click to expand)</summary>

Imagine sending a **letter**:

1. **Application:** You write the letter.  
2. **Presentation:** You format it and choose the language.  
3. **Session:** You make sure the recipient is ready to receive.  
4. **Transport:** You use a courier that guarantees delivery.  
5. **Network:** The courier decides the best route.  
6. **Data Link:** The courier packs the letter safely in an envelope.  
7. **Physical:** The letter travels via truck, plane, or bike.

</details>

---

## <details><summary>1️⃣ Layer 1 – Physical</summary></details>

Handles the **physical transmission of data**: cables, signals, and hardware.  

### Key Points
- Signals, cabling, connectors  
- Devices: **hubs, repeaters, media converters**  
- Focuses on *hardware, not protocols*  

### Issues
- Bad cables, connectors, adapters  

### Troubleshooting
- Loopback tests  
- Replace/test cables & adapter cards  
- Fix physical connections

---

## <details><summary>2️⃣ Layer 2 – Data Link (Switching)</summary></details>

Manages **node-to-node communication** on the same network segment.

### Key Points
- Provides communication foundation  
- Uses **Data Link Control (DLC) protocols**  
- **MAC addresses** control access  
- “Switching” layer  

### Issues
- Collisions, broadcast storms  
- Duplicate MAC addresses  
- Faulty switches  

### Troubleshooting
- Check switch configs & MAC tables  
- Replace faulty cables/switches  
- Monitor excessive broadcasts

---

## <details><summary>3️⃣ Layer 3 – Network (Routing)</summary></details>

The **“routing layer”**: moves data between networks using logical addressing.

### Key Points
- Uses **IP addresses**  
- Handles routing across networks  
- Fragments frames into IP packets  

### Issues
- Wrong IP/subnet  
- Routing loops  
- Packet fragmentation  

### Troubleshooting
- Verify IP addresses & subnets  
- Check routing tables  
- Test with `ping` / `traceroute`

---

## <details><summary>4️⃣ Layer 4 – Transport</summary></details>

The **“post office” layer**: ensures data is delivered correctly.

### Key Points
- **TCP:** Reliable, connection-oriented  
- **UDP:** Fast, connectionless  
- Breaks data into segments  

### Issues
- Port misconfigurations  
- Dropped/out-of-order packets  

### Troubleshooting
- Check active ports (`netstat`, `ss`)  
- Packet analysis (Wireshark)  
- Verify firewall rules

---

## <details><summary>5️⃣ Layer 5 – Session</summary></details>

Manages **communication sessions** between devices.

### Key Points
- Controls dialogues (start, stop, restart)  
- Supports control/tunneling protocols  

### Examples
- Remote desktop sessions  
- Login/authentication processes

---

## <details><summary>6️⃣ Layer 6 – Presentation</summary></details>

The **translator layer**: formats and secures data for the application.

### Key Points
- Character encoding: ASCII, Unicode  
- Data compression  
- Encryption (SSL/TLS)  

### Examples
- Application encryption  
- File format conversion (JPEG → PNG)

---

## <details><summary>7️⃣ Layer 7 – Application</summary></details>

The **user-facing layer**: services and apps users interact with.

### Examples
- **HTTP/HTTPS** – Web browsing  
- **FTP** – File transfers  
- **DNS** – Domain resolution  
- **SMTP/POP3/IMAP** – Email  

---

## 🗂 OSI Layers – Summary Table

| Layer | Function | Key Components / Protocols | Real-World Example | Encapsulation Unit |
|-------|---------|----------------------------|------------------|------------------|
| Application (7) | User interface | HTTP, FTP, DNS, POP3, SMTP | Web browsing, email | Data |
| Presentation (6) | Data formatting & encryption | SSL/TLS, character encoding | App encryption, file format conversion | Data |
| Session (5) | Session management | Control & tunneling protocols | Login sessions, remote desktop | Data |
| Transport (4) | Reliable/fast delivery | TCP, UDP | File transfer, streaming | Segment |
| Network (3) | Routing & addressing | IP, ICMP, Router | Internet traffic | Packet |
| Data Link (2) | Node-to-node transfer | MAC, Switch, Bridge, NIC, ARP | LAN communication | Frame |
| Physical (1) | Physical transmission | Cables, fibers, Hub, Repeater, Media Converter | Wired & wireless connectivity | Bits |

---

<p align="center">
  <img src="https://github.com/user-attachments/assets/90be3546-4386-4d98-a062-27ad9b573138" alt="OSI model" width="800"/>
</p>
