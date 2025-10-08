# 🌐 OSI Model (1.1)

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

---

# 🔌 Networking Devices (1.2)

Networking devices are the **building blocks of a network**. Each device has a specific role in moving, securing, or managing traffic.

---

## 📡 Router
A **Router** connects different networks together and routes data based on IP addresses.  

- Works at **OSI Layer 3 (Network Layer)**  
- Chooses the best path for data to travel  
- Can connect diverse network types (LAN, WAN, fiber, copper)  

### Variants
- **Layer 2 = Switches** (forward traffic by MAC)  
- **Layer 3 = Routers** (forward traffic by IP)  
- **Layer 3 Switch = Hybrid** (switching + routing in one device)  

---

## 🔀 Switch
A **Switch** connects multiple devices within the same network and forwards traffic based on **MAC addresses**.  

- Works at **OSI Layer 2 (Data Link Layer)**  
- Uses **ASIC (Application-Specific Integrated Circuit)** for fast, hardware-based forwarding  
- Forms the **core of most enterprise networks**  

### Types
- **Standard Switch:** Forwards traffic based only on MAC  
- **PoE Switch:** Provides both **data and electrical power** over the same Ethernet cable (for IP phones, cameras, wireless APs)  
- **Multilayer Switch:** Adds Layer 3 routing functions on top of switching  

---

## 🔥 Firewall
A **Firewall** protects a network by filtering traffic based on rules.  

- Can operate at **Layer 3 (Network Layer)** and above  
- Traditionally filtered by **ports** (e.g., TCP 80 = web traffic)  
- **Next-Generation Firewalls (NGFW):** Can filter by **applications** (e.g., block Facebook, allow Gmail)  

### Extra Features
- **NAT (Network Address Translation):** Hides private IPs behind public IPs  
- **VPN Support:** Encrypts traffic between sites  
- **Dynamic Routing:** Some firewalls also act as routers  

---

## 🛡 IDS vs IPS
Security systems that monitor and respond to intrusions.  

- **IDS (Intrusion Detection System):** Detects malicious traffic and alerts admins (monitor only).  
- **IPS (Intrusion Prevention System):** Detects and blocks malicious traffic automatically (active protection).  

👉 Think of IDS as a **security camera** (watch + alert) and IPS as a **security guard** (watch + stop).  

---

## ⚖️ Load Balancer
A **Load Balancer** spreads incoming traffic across multiple servers so no single server gets overloaded.  

### Functions
- **High availability:** Keeps apps online even if one server fails  
- **SSL Offload:** Handles encryption/decryption so servers don’t have to  
- **Caching:** Serves repetitive requests directly for speed  
- **QoS:** Prioritizes certain traffic  
- **Content Switching:** Routes requests based on app type (e.g., API vs website)  

---

## 🌐 Proxy
A **Proxy server** acts as a middleman between clients and the internet.  

### Uses
- **Caching:** Saves bandwidth & speeds up browsing  
- **Security:** URL filtering, content scanning, access control  
- **Types:**  
  - **Explicit Proxy:** Users configure it manually in settings  
  - **Transparent Proxy:** Works silently, no user config needed  

---

## 💾 SAN vs NAS
Both are network storage solutions but work differently:  

- **SAN (Storage Area Network):**  
  - **Block-level storage** (like a dedicated storage database. The server sees it as a raw disk and can manage it however it wants)  
  - High speed, high control, heavy-duty use. 
  - Often used in enterprise data centers  

- **NAS (Network Attached Storage):**  
  - **File-level storage** (like a storage folder inside a shared network database. It’s already organized with files and folders; you just access what you need without worrying about how it’s stored underneath.)  
  - Easier setup, great for file sharing/home use  

⚡ Both require **high bandwidth** and often use **isolated networks**.  

---

## 📶 Wireless Networks
- Multiple **Access Points (APs)** cover an area so devices can connect anywhere. 
- Users can roam seamlessly between APs without losing connection. 
- Each AP needs security settings and access rules.  

### Wireless LAN Controller (WLC)
- Central management for all APs.  
- Pushes configurations, security updates, and monitors usage from one place.

---

## 🚀 Networking Functions

### CDN (Content Delivery Network)
- **Think of it like mini copies of a website or video stored closer to users.**
- Instead of everyone hitting the main server, users get content from the nearest edge server → faster loading. 
- Improves global performance  
- Example: Watching YouTube in Kuwait? You get the nearest YouTube server copy, not the origin server in the US.

---

### VPN (Virtual Private Network)
- Creates an **encrypted tunnel** for secure remote access (like a secure, invisible tunnel over the internet)
- **VPN Concentrator/Head-End:** Central hub for managing all tunnels, traffic, and authentication. 
- Can be:  
  - **Hardware appliance:** Used by big orgs for performance  
  - **Software/OS-integrated:** Common for smaller orgs or individuals
- Often works with firewalls for encryption (IPsec/SSL).

---

### QoS (Quality of Service)
- Prioritizes important traffic (like VoIP, video calls, real-time apps)  
- Also called **packet shaping**  
- Built into routers, switches, firewalls.
- Configurable per app, device, or network.
- **Analogy**: VIP cars get the fast lane, regular cars wait.

---

### TTL (Time To Live)
- Maximum lifetime of a data packet before it’s discarded. 
- Prevents **endless routing loops**   
- Decreases by 1 at each router hop  
- Defaults: **Windows = 128 hops, Linux/Mac = 64 hops**   

---

### Routing Loops
- Packet keeps bouncing between Router1 ↔ Router2 (back and forth)  
- TTL eventually drops the packet to stop looping (When TTL = 0 → packet is dropped)
- Often caused by **misconfigured static routes**  

---

### IP (Internet Protocol)
- Responsible for addressing & packet delivery  
- TTL is built into IP to stop looping packets  

---

### DNS (Domain Name System)
- Converts human-readable names (e.g., `google.com`) into IPs  
- Uses **TTL in seconds** for cache expiry  
- After TTL expires, DNS queries are refreshed  

---

# ☁️ Cloud & Virtual Networking (1.3)

Cloud computing allows organizations to run servers, networks, and applications **virtually** instead of relying solely on physical hardware.

---

## 🌐 Virtual Networks
- Virtualizes the entire physical network (routers, switches, cables, servers)  
- Server farms are shifted into virtualized environments  

### NFV (Network Function Virtualization)
- Converts physical devices (routers, switches, firewalls, load balancers) into **virtual devices**  
- Virtualized devices work just like physical ones  
- Managed centrally through a **hypervisor**  
- Can deploy **VMs, containers, and fault-tolerant setups**  

---

## 🏢 VPC (Virtual Private Cloud)
- A **private, isolated cloud environment** with virtual routers, switches, firewalls, and load balancers  
- Each component can be managed separately, like individual departments in a company  

### Communication
- **Cloud Router:** Connects devices **within the VPC**  
- **VPN:** Secure tunnel for external access to VPC  

---

## 🔗 Connecting to the Cloud
- **VPN:** Encrypted connection for secure access (private access)  
- **Internet Gateway / VPC Gateway:** Public access for internet users (open access)  
- **VPC NAT:** Allows cloud to access external networks while **hiding private IPs**  

---

## 🔌 VPC Endpoint
- Direct connection between **private cloud networks**  
- No internet middleman, just **private communication**  

---

## 🛡 Security in the Cloud

### Security Groups
- Rules applied to **individual virtual NICs (VNICs)**  
- Can target specific VMs, ports, IPs, protocols  
- **Flexible and granular**  

### Security Lists
- Rules applied **subnet-wide**  
- Less flexible, applies to all devices in the subnet  
- Harder to manage; misconfigurations can create **security holes**  

💡 **Best Practice:** Prefer Security Groups for fine-grained, safe control  

---

## ☁️ Cloud Deployment Models

### Private Cloud
- Fully controlled by you or provider  
- Used only by your organization  
- Example: Banks, government, large corporations  

### Public Cloud
- Managed by cloud provider  
- Shared infrastructure, isolated data  
- Examples: Gmail, Dropbox  

### Hybrid Cloud
- Combines private & public cloud  
- Example: Customer data stored privately, website hosted publicly  

---

## 💻 Cloud Service Models

### SaaS (Software as a Service)
- Use the application **without managing infrastructure**  
- Provider handles updates, servers, storage  
- Example: Office 365, Gmail, Dropbox  

### IaaS / HaaS (Infrastructure / Hardware as a Service)
- You manage: OS, storage, apps, updates  
- Provider manages: Physical servers, network, hardware  
- Example: Microsoft Azure VMs, Google Compute Engine  

### PaaS (Platform as a Service)
- Build, test, deploy apps without managing servers or OS  
- Focus is on **code**, not infrastructure  
- Example: Google App Engine, Heroku, Salesforce  

---

<details>
<summary>💡 Quick Analogy</summary>

- **NFV:** Think of your router or firewall as software now, not a physical box  
- **VPC:** Your private office in the cloud  
- **Security Groups:** Door locks for individual rooms (VMs)  
- **Security Lists:** One rule for the entire floor (subnet)  
- **VPN:** Secret tunnel into your office  
- **Public Cloud:** Shared office space; **Private Cloud:** Your personal office  
</details>

---

# 🌍 Intro to IP & Networking Protocols (1.4)

---

## 📦 IP Overview
Think of IP like **delivery trucks carrying packages**:

| Networking Term      | Analogy                                 |
|---------------------|----------------------------------------|
| **Network**         | The **road system** trucks use.        |
| **IP (Internet Protocol)** | The **truck** carrying your packages. |
| **TCP/UDP**         | The **packages** inside the truck.     |
| **IP Address**      | Your **house address**.                |
| **Ports**           | The **specific drop-off spot** (kitchen, bedroom, etc.). |

---

## 🚚 TCP vs UDP

| Feature | TCP (Transmission Control Protocol) | UDP (User Datagram Protocol) |
|---------|-----------------------------------|-----------------------------|
| **Delivery Guarantee** | ✅ Yes (acknowledgements, retries) | ❌ No (fire & forget) |
| **Use Cases** | Email, web, file transfer | Video calls, gaming, streaming |
| **Speed** | Slower, reliable | Faster, no checks |
| **Handshake** | 🔁 3-Way Handshake | 🚫 None |

### 🔍 TCP Details:
- **3-Way Handshake**: `SYN → SYN-ACK → ACK`
- **Acknowledgement System**: Confirms delivery; resends errors.
- **Flow Control**: Receiver can slow/speed packet flow.
- **Orderly Delivery**: Guarantees correct order.
- **Teardown**: Gracefully closes connection.

### ⚡ UDP Details:
- No error checks.
- No delivery confirmation.
- No guaranteed order.
- 🚀 **Super fast** → great for live calls/gaming.

---

## 🎯 Multiplexing
An app can use **both TCP & UDP simultaneously**.  
Example: **Zoom**  
- Video/audio call → `UDP`  
- Chat messages → `TCP`

---

## 🔑 Ports & Sockets

| Type                | Port Range | Used By |
|--------------------|-----------|--------|
| **Ephemeral Ports** | `1024–65535` | Temporary, often client side |
| **Non-Ephemeral Ports** | `0–1023` | Permanent, often server side |

💡 Both client & server **can use either range**.

### IPv4 Socket Structure:
- **Client Socket:** Client IP + protocol + client port
- **Server Socket:** Server IP + protocol + server port

---

## 🛠️ Key Notes on Ports
- TCP and UDP **can share the same port number** but are separate services.
- Ports are **not a security feature** — don’t rely on them for security.
- Server ports should be **well-known & predictable**.

---

# 📜 Common Networking Protocols & Ports

<details>
<summary>📂 FTP (File Transfer Protocol) - <code>TCP 20/21</code></summary>

- Transfer files between systems.
- `20`: **Data transfer** (active mode).  
- `21`: **Control channel** (auth & commands).
- Username/password-based auth.
- Fully customizable: add, delete, edit files.

</details>

<details>
<summary>🔐 SSH (Secure Shell) - <code>TCP 22</code></summary>

- Secure remote command-line access.
- Encrypted communication for admin tasks.

</details>

<details>
<summary>📁 SFTP (Secure File Transfer Protocol) - <code>TCP 22</code></summary>

- Built on SSH → fully secure.
- Same flexibility as FTP but encrypted.

</details>

<details>
<summary>🖥️ Telnet - <code>TCP 23</code></summary>

- Legacy remote console access.
- ❌ No encryption → **Not recommended**.

</details>

<details>
<summary>📧 SMTP (Simple Mail Transfer Protocol)</summary>

| Port | Use |
|------|-----|
| `25/TCP` | Legacy SMTP (unsecure, outdated). |
| `587/TCP` | SMTP w/ TLS (secure). |

- Used to **send emails** (client → server or server → server).  
- **Receiving emails** handled by `POP3` or `IMAP`.

</details>

<details>
<summary>🌍 DNS (Domain Name System)</summary>

- Converts **domain names → IP addresses**.
- `53/UDP`: Small queries  
- `53/TCP`: Large queries

</details>

<details>
<summary>🎟️ DHCP (Dynamic Host Configuration Protocol) - <code>UDP 67/68</code></summary>

- Auto-assigns IP addresses to clients.
- **DHCP Reservation**: Permanent IP lease.
- `67`: Server side  
- `68`: Client side

</details>

<details>
<summary>📦 TFTP (Trivial File Transfer Protocol) - <code>UDP 69</code></summary>

- Lightweight, no authentication, no directory editing.
- Used in VoIP devices.

</details>

<details>
<summary>🌐 HTTP & HTTPS</summary>

| Protocol | Port | Security |
|----------|------|----------|
| HTTP | `80/TCP` | ❌ Unencrypted |
| HTTPS | `443/TCP` | ✅ TLS/SSL encrypted |

</details>

<details>
<summary>⏱️ NTP (Network Time Protocol) - <code>UDP 123</code></summary>

- Keeps all device clocks in sync → **critical for logs & security**.

</details>

<details>
<summary>📊 SNMP (Simple Network Management Protocol)</summary>

| Version | Security |
|---------|----------|
| v1 | None |
| v2 | Bulk queries, no encryption |
| v3 | ✅ Encrypted & secure |

- `161/UDP`: Device queries  
- `162/UDP`: SNMP Traps (device-initiated alerts)

</details>

<details>
<summary>👤 LDAP & LDAPS</summary>

| Protocol | Port | Security |
|----------|------|----------|
| LDAP | `389/TCP` | ❌ No encryption |
| LDAPS | `636/TCP` | ✅ SSL encrypted |

- Used for **directory services** & authentication.

</details>

<details>
<summary>🗂️ SMB (Server Message Block) - <code>TCP 445</code></summary>

- Built into Windows OS.
- File & printer sharing, file locking.
- Difference:  
  - **SMB** = Sharing (OS-integrated)  
  - **SFTP** = Secure transfer (SSH-based)

</details>

<details>
<summary>📝 Syslog - <code>UDP 514</code></summary>

- Logs messages from devices & services.
- Commonly fed into **SIEM systems**.
- Can take a LOT of storage.

</details>

<details>
<summary>💾 Database Protocols</summary>

| DB Type | Port |
|---------|------|
| Microsoft SQL Server | `1433/TCP` |

</details>

<details>
<summary>🖥️ RDP (Remote Desktop Protocol) - <code>TCP 3389</code></summary>

- Remote desktop control (Windows).

</details>

<details>
<summary>📞 SIP (Session Initiation Protocol)</summary>

| Port | Use |
|------|-----|
| `5060/TCP` | SIP (unencrypted) |
| `5061/TCP` | SIP over TLS (encrypted) |

- Sets up, modifies, tears down **real-time sessions** (voice, video).

</details>

---

# 🔐 Other Protocols

| Protocol | Layer | Purpose | Key Features |
|----------|------|---------|--------------|
| **ICMP** (Internet Control Message Protocol) | L3 | Diagnostics, error messages, status checks | Used by `ping`, `traceroute`; reports TTL expiry, unreachable hosts |
| **GRE** (Generic Routing Encapsulation) | L3 | Creates tunnels between endpoints | Encapsulates traffic; no encryption; point-to-point |
| **VPN** (Virtual Private Network) | L3/4 | Secure communication over public internet | Encryption via firewall/VPN concentrator; Site-to-Site or Remote Access |
| **IPSec** (Internet Protocol Security) | L3 | Encrypts/authenticates IP packets | Uses AH & ESP; anti-replay, integrity checks |
| **IKE** (Internet Key Exchange) | L3 | Negotiates IPSec keys securely | Uses Diffie-Hellman; Phase 1 (keys), Phase 2 (SA setup) |
| **Transport Mode** | L3 | Encrypts payload only | Original IP header visible; lightweight |
| **Tunnel Mode** | L3 | Encrypts entire packet | Adds new IP header; hides source/destination |

---

# 🌐 Network Communication

| Method       | Type               | How It Works | Common Uses                     | IPv4/IPv6       |
|--------------|-------------------|-------------|--------------------------------|-----------------|
| **Unicast**  | One-to-One        | One sender → one receiver | Web browsing, file transfers   | ✅ Both         |
| **Multicast**| One-to-Many (group)| Sends to selected devices | Router updates, stock alerts   | ✅ Both         |
| **Anycast**  | One-to-Nearest    | Closest receiver responds  | DNS, CDNs, DDoS mitigation     | ✅ Both         |
| **Broadcast**| One-to-All (local)| Sends to all devices      | ARP, routing updates          | ✅ IPv4 ❌ IPv6 |

💡 **Key Notes:**  
- **Unicast** is your default everyday comms.  
- **Multicast** is efficient for groups, but not huge scale.  
- **Anycast** = “nearest server wins.”  
- **Broadcast** is dying; IPv6 doesn’t use it.  

<details>
<summary>📝 Analogy</summary>

Think of it like delivering mail:  
- **Unicast:** A letter to one friend.  
- **Multicast:** Invite letters to your club members only.  
- **Anycast:** You send it, and the *nearest* post office replies.  
- **Broadcast:** Yelling from the rooftop to everyone.  
</details>

---

# 📡 Wireless Networking (1.5)

## 📶 Wi-Fi & IEEE 802.11
Wi-Fi is standardized by the **IEEE LAN/MAN** group (802.11 standards).  
It's constantly updated to support higher speeds and frequencies.

| IEEE Standard | Wi-Fi Gen    | Frequencies             | Max Link Speed    |
|--------------|-------------|------------------------|------------------|
| **802.11a**  | Wi-Fi 1     | 5 GHz                  | 54 Mbps          |
| **802.11b**  | Wi-Fi 2     | 2.4 GHz                | 11 Mbps          |
| **802.11g**  | Wi-Fi 3     | 2.4 GHz                | 54 Mbps          |
| **802.11n**  | Wi-Fi 4     | 2.4 / 5 GHz            | 600 Mbps         |
| **802.11ac** | Wi-Fi 5     | 5 GHz                  | 1.3 Gbps         |
| **802.11ax** | Wi-Fi 6/6E  | 2.4 / 5 / 6 GHz        | 9.6 Gbps         |
| **802.11be** | Wi-Fi 7     | 2.4 / 5 / 6 GHz        | 46 Gbps          |

---

## 📱 4G & LTE
- **4G** = Fourth generation of mobile networking.  
- **LTE (Long Term Evolution)** = Marketing name for 4G; based on **GSM** and **EDGE** standards.  
- Unified **CDMA** and **GSM** technologies.  

---

## 🚀 5G
- **5th gen mobile networking** with massive performance jump.
- **Real-world speed:** 100–900 Mbps  
- **Theoretical max:** 10 Gbps  
- **Benefits:**  
  - Lightning-fast file transfers (seconds, not minutes).  
  - Better **cloud processing** → less strain on your device.  
  - Reduced bandwidth bottlenecks.  
  - Near real-time notifications & monitoring.  

---

## 🛰️ Satellite Networking
Used in rural or remote areas where cables can’t reach.  

| Feature                 | Details                          |
|------------------------|----------------------------------|
| **Latency**            | ~250 ms up + 250 ms down (space trip!) |
| **Speed**              | ~100 Mbps down, ~5 Mbps up       |
| **Cost**               | Too expensive 💸            |
| **Frequency**          | ~2 GHz (signal easily scattered) |
| **Rain Fade**          | Bad weather = weak/no signal    |

---

💡 **Key Takeaways:**
- Wi-Fi keeps evolving with **higher frequencies** & **multi-Gbps speeds**.  
- LTE is basically **4G marketing fluff**.  
- 5G makes cloud and AI integration seamless.  
- Satellites are great for **coverage**, terrible for **latency**.  

---

# 🖧 Ethernet Standards

## Overview
- **Ethernet**: Industry-standard networking technology used for wired LAN connections, cabling, and data transmission.
- Supports **copper and fiber cabling**, defined by **IEEE 802.3** standards.

---

## IEEE Ethernet Standards

| IEEE Standard  | Description               | Media  | Network Speed |
|----------------|---------------------------|--------|---------------|
| 1000BASE-T     | Gigabit Ethernet          | Copper | 1 Gbps        |
| 10GBASE-T      | 10 Gigabit Ethernet       | Copper | 10 Gbps       |
| 1000BASE-SX    | Gigabit Ethernet (Short)  | Fiber  | 1 Gbps        |

---

## Deciphering the Standard
- **Numbers** → represent speed (e.g., `1000BASE-T` = 1 Gbps)  
- **BASE** → Baseband (single frequency signal transmission)  
- **Media Indicators**:  
  - `T` = Twisted Pair Copper  
  - `F` = Fiber  
  - `SX` = Short Wavelength/Short Distance Fiber  
- ⚠️ **Note:** IEEE does not officially guarantee strict correlation between the acronym and specification details.

---

# 🔬 Optical Fiber Networking

## Key Characteristics
- No RF (radio frequency) interference which makes it difficult to tap or monitor.
-Data is transmitted by LIGHT.
-It’s signal degrades slowly over the length than copper. Eg: Copper can degrade quickly if the length keeps increasing but fiber does it more slowly.
-It does not have RF so basically it cannot leak signals or be interfered with.

---

## Fiber Cable Structure
1. **Core**: The central glass strand where light travels and bounces.  
2. **Cladding**: A glass layer surrounding the core. Has a lower refractive index to trap light inside the core via total internal reflection.  
3. **Coating (Buffer)**: A plastic (usually acrylic) protective layer that cushions the fragile core and cladding — first line of real protection.  
4. **Cable Jacket**: The tough outer covering that shields the entire assembly (can include multiple fibers, strength members, and ripcords).  


---

## Fiber Types

| Fiber Type        | Distance         | Core Size           | Light Source | Cost         |
|------------------|----------------|------------------|-------------|-------------|
| Multimode Fiber   | ~2 km (short)  | Thick (50–62.5 µm)| LED         | Low         |
| Single-mode Fiber | 100+ km (long) | Very thin (~9 µm) | Laser       | High        |

---

# 🖧 Copper Cabling & Network Transceivers

## 🪢 Importance of Cabling
- Cables are the **backbone of networking**; even wireless tech relies on wired infrastructure.
- **Proper planning** is crucial because once installed, cables are **hard and expensive** to remove or redo.

---

## 🧵 Twisted Pair Copper Cabling
- Pairs of wires carry '+' and '-' signals for transmit/receive.
- Twisting **reduces interference** and **crosstalk**; each pair has a unique twist rate.
- Multiple wire pairs ensure redundancy and higher data integrity. **This means the system can often correct errors or continue functioning even if one pair is degraded, by using the combined signal from all pairs**.
- Cable speed is determined by **signal quality and standards** (not just the cable itself).
- Cables must be manufactured by the standards of the IEEE to support the desired speed and distance.
- **Categories**:
  - **Cat5**: Up to `1 Gbps`.
  - **Cat6/Cat7**: Higher speeds, longer distances, better shielding.

---

## 📡 Coaxial Cable
- Inner conductor and outer shield **share the same axis** → improved signal integrity.
- Common type: `RG-6`.
- Used for **TV, digital cable, high-speed internet**.

---

## 🔗 Twinaxial Cable
- Has **two inner conductors** sharing the same axis.
- Used for **10 Gbps Ethernet (SFP+)**.
- **Duplex**: Can send and receive signals simultaneously.
- Pros: Low cost, low latency.
- Cons: **Short range** (`≤5m`).

---

## 🏢 Plenum & Cabling Spaces
- **Plenum space**: Ceiling area with HVAC air circulation.
- **Non-plenum space**: No active air circulation.
- **Plenum-rated cables**:
  - Made of **fire-rated materials** like FEP or low-smoke PVC.
  - **Expensive** and **less flexible**.
  - Installed **permanently** and hard to remove.

---

## 🔌 Network Transceivers

### 🔄 Transceivers
- **Definition**: A combo of transmitter and receiver in a single module.
- Supports either **fiber or copper**, but not both in the same module.

### 📦 SFP & SFP+
- **SFP (Small Form-factor Pluggable)**:
  - Up to `1 Gbps`.
  - Also available as **RJ45 SFP** for copper.
- **SFP+**:
  - Supports `10 Gbps` or more.
  - Same physical size as SFP.

### 📦 QSFP & QSFP+
- **QSFP (Quad SFP)**:
  - Combines 4x SFP channels → `4 Gbps` total.
- **QSFP+**:
  - Combines 4x SFP+ channels → `40 Gbps` total.

---


# 🖧 Fiber Connectors

## 🔦 Fiber Optic Connectors

### SC (Subscriber Connector)
- **Square Connector**: Nicknamed for its shape.
- **Standard Connector**: Very common in data centers and telecom infrastructure.
- **Locking Mechanism**: Push-pull design. Secure; requires intentional force to insert and remove.

### LC (Local Connector)
- **Little Connector**: Compact size, ideal for high-density patches (e.g., SFP modules).
- **Locking Mechanism**: Integrated latch (clip) that is pressed to unlock.
- **Duplex Format**: Almost always used in a paired (duplex) configuration for Tx/Rx.

### ST (Straight Tip Connector)
- **Bayonet Connector**: Uses a twist-and-lock bayonet coupling, unlike push-pull SC/LC.
- **Legacy Use**: Common in older installations and fiber distribution panels.

### MPO/MTP (Multi-Fiber Push-On)
- **High-Density**: Houses 12, 24, or more fibers in a single ferrule.
- **Space-Saving**: Essential for 40/100/400G parallel optic transceivers (e.g., QSFP).
- **Locking Mechanism**: Push-pull, similar to SC.
- **Note**: MTP is a specific, high-performance *branded* version of the MPO standard.

---

## 🔌 Copper Connectors

### RJ11 (Registered Jack 11)
- **Configuration**: Typically **6P2C** (6 Position, 2 Contact) 
- **Primary Use**: **Telephone** wiring and **DSL** modem connections.

### RJ45 (Registered Jack 45)
- **Configuration**: **8P8C** (8 Position, 8 Contact). This is the standard for networking.
- **Primary Use**: **Ethernet** (Twisted-Pair Copper) cabling (Cat5/6/6A/7/8).
- **Modular Connector**: The plastic plug is correctly called an **8P8C modular connector**, though "RJ45" is the universal term in networking.

### F-Type Connector
- **Threaded Coupling**: Must be screwed onto a port to ensure a solid connection.
- **Primary Use**: **Coaxial cabling** for:
    - **Cable Television (TV)**
    - **Cable Modems** (**DOCSIS** standard)
    - Satellite equipment
- **Common Cable**: Used with **RG-6** coaxial cable.

### BNC (Bayonet Neill–Concelman)
- **Bayonet Lock**: Insert and twist ~90 degrees to lock. Highly secure against vibration.
- **Primary Use**: **Legacy networking**, **radio antenna**, **RF video** (e.g., surveillance systems), and test equipment.
- **Clarification**: While sometimes used with Twinaxial, its most common historical network use was with ** coaxial** cabling.

---

# 🌐 Network Topologies (1.6)

Network topologies are **blueprints** of how devices and networks are physically or logically connected.  
They help in **designing networks** and make **troubleshooting easier** by showing how data flows.  

---

## ⭐ Star / Hub-and-Spoke
- Common in **small and large networks**.
- All devices connect to a **central device** (usually a switch).  
- **Switches > Hubs** (Hubs are outdated and dumb).  
- Easy to troubleshoot but a **central failure kills everything**.

---

## 🔗 Mesh
- Multiple routers placed strategically for **seamless connectivity**.  
- Great for **redundancy, load balancing, and fault tolerance**.  
- Used in **WANs**, either partial or fully meshed.  
- Example: Move around a building and stay connected to the Wi-Fi.

---

## 🔀 Hybrid
- A **mix of topologies** (e.g., Mesh + Star + Point-to-Point).  
- Flexible and scalable but **complex**.

---

## 🌿 Spine-and-Leaf
- Common in **data centers**.  
- **Spine = Core switches**  
- **Leaf = Access switches**  
- Leafs connect to all Spines (**no Spine↔Spine or Leaf↔Leaf** links).  

| Feature     | Benefit                     |
|------------|----------------------------|
| **Redundant** | No single point of failure |
| **Fast**      | High-speed connectivity    |
| **Scalable**  | Easy to add devices        |
| **Expensive** | Costs can skyrocket ⚠️    |

---

## 🔌 Point-to-Point
- Direct connection between **two networks or sites**.  
- Example: HQ ↔ Branch Office.  
- Simple, reliable, **not scalable**.

---

💡 **Key Takeaways:**  
- **Star** is simple but switch-dependent.  
- **Mesh** = best for redundancy and coverage.  
- **Hybrid** = flexible combo of designs.  
- **Spine-and-Leaf** = data center favorite.  
- **Point-to-Point** = simple site-to-site link.

---

# 🏛️ Network Architecture

Network architecture defines **how layers and devices are structured** in a network, making management and scalability easier.  

---

## 🔺 Three-Tier Architecture

| Layer           | Purpose                                                      |
|----------------|--------------------------------------------------------------|
| **Core**       | - The backbone of the network. <br> - Hosts **servers, databases, and apps**. <br> - High-speed connections for heavy traffic. |
| **Distribution**| - Acts as a **middle layer** between Core and Access. <br> - Uses **switches** to connect Access devices to Core. |
| **Access**     | - The entry point for users. <br> - **End stations, printers, and devices** connect here. |

💡 **Why Three-Tier?**  
- Scalable and well-structured.  
- Easier to manage in **large organizations**.  

---

## 🗜️ Collapsed Core

When **Core + Distribution** are merged into one layer.  

| Feature        | Benefit                       |
|---------------|------------------------------|
| **Ideal for** | Small to mid-size networks   |
| **Pros**      | Cheaper, simpler, easier to manage |
| **Cons**      | Less resilient; a failure can disrupt everything ⚠️ |

---

## 🔀 Traffic Flow

| Flow Type           | Description                                                 |
|--------------------|-------------------------------------------------------------|
| **East–West**      | - Traffic inside the data center. <br> - **Fast, secure**, and internal. |
| **North–South**    | - Traffic entering or exiting the data center. <br> - More exposure to **security risks**. |

---

💡 **Key Takeaways:**  
- **Three-Tier** = Best for large orgs.  
- **Collapsed Core** = Budget-friendly, simple networks.  
- **East–West Traffic** stays internal; **North–South Traffic** needs strong security.

---

# 🌐 IPv4 Addressing (1.7)

The **Internet Protocol version 4 (IPv4)** is a core networking protocol that provides an addressing system for identifying devices on a network.

---

## 🏘️ Networking with IPv4: Neighborhood Analogy

Think of networking with IPv4 like organizing a neighborhood:

| Networking Concept | Real-World Analogy |
|-------------------|-------------------|
| **IP Network** | The entire neighborhood |
| **IP Address** | Your unique house number |
| **Subnet** | A single street/block where houses can communicate directly |
| **Subnet Mask** | The fence line showing where your block starts and ends |
| **Default Gateway** | The main gate out of your neighborhood (e.g., `192.168.1.1`) |

---

## 🔑 Special IPv4 Addresses

| Address Type | Range | Purpose |
|-------------|-------|---------|
| **Loopback (localhost)** | `127.0.0.1` to `127.255.255.254` | Testing your own device's network stack |
| **Reserved (Class E)** | `240.0.0.0` to `255.255.255.254` | Reserved for future use and testing |
| **Virtual IP (VIP)** | Varies | Not tied to physical hardware; used for VMs, internal router addresses |

---

## 📊 IPv4 Structure Overview

- **OSI Layer**: 3 (Network Layer)
- **Total Bits**: 32 bits = 4 bytes (octets)
- **Octet Range**: 0-255 (e.g., `192.168.1.131`)
- **Maximum Value**: 255 per octet (2⁸ = 256 values, 0-255)

---

## ⚙️ Automatic IP Configuration

### DHCP (Dynamic Host Configuration Protocol)
- Automatically assigns IP addresses and network configurations
- Eliminates need for manual IP configuration
- Uses ports: `UDP 67` (server), `UDP 68` (client)

### APIPA (Automatic Private IP Addressing)
- Self-assigns an IP when DHCP fails
- **Range**: `169.254.0.1` to `169.254.255.254` (first/last 256 addresses reserved)
- Uses ARP to ensure address isn't already in use

---

## 🌍 Public vs Private Addresses

### The IPv4 Address Problem
- Too many devices for available addresses
- Inefficient, non-contiguous address blocks
- Near complete depletion of available addresses

### RFC 1918 Private IPv4 Addresses

| Class | Range | Subnet Mask | CIDR | Typical Use | Available Addresses |
|-------|-------|------------|------|------------|---------------------|
| **Class A** | `10.0.0.0` to `10.255.255.255` | `255.0.0.0` | `/8` | Large networks (ISPs, governments) | 16.7 million |
| **Class B** | `172.16.0.0` to `172.31.255.255` | `255.240.0.0` | `/12` | Campuses, large organizations | 1 million |
| **Class C** | `192.168.0.0` to `192.168.255.255` | `255.255.0.0` | `/16` | Home networks, small businesses | 65,536 total |

### Public IP Addresses
- Used for internet communication
- Requires NAT (Network Address Translation) to convert private→public IPs

---

## 🗂️ IPv4 Address Classes (Classful Subnetting)

| Class | Leading Bits | Range | Subnet Mask | Network Bits | Host Bits | Available Addresses |
|-------|-------------|-------|------------|-------------|----------|---------------------|
| **Class A** | `0xxx` | `0-127` | `255.0.0.0` | 8 | 24 | 16.7 million |
| **Class B** | `10xx` | `128-191` | `255.255.0.0` | 16 | 16 | 65,536 |
| **Class C** | `110x` | `192-223` | `255.255.255.0` | 24 | 8 | 254 |
| **Class D (Multicast)** | `1110` | `224-239` | Not defined | Not defined | Not defined | Not defined |
| **Class E (Reserved)** | `1111` | `240-255` | Not defined | Not defined | Not defined | Not defined |

> **Note**: `127.0.0.0` is reserved for loopback addresses. Classful subnetting is largely historical but helps understand IP structure.

### Identifying IP Classes
- **17.22.90.7** → First octet = 17 → **Class A**
- **128.90.10.2** → First octet = 128 → **Class B**  
- **220.10.77.40** → First octet = 220 → **Class C**

---

## 🔧 Modern Subnetting (Classless)

### CIDR (Classless Inter-Domain Routing)
- Introduced circa 1993
- Removes restrictions of class-based subnet masks
- Allows flexible subnet masks using CIDR notation (`/8`, `/24`, `/32`, etc.)
- Supported by most modern operating systems

### Why Subnet?
- Manage large networks efficiently
- Improve performance and organization
- Enhance security through segmentation
- Make networks more scalable and reliable

### VLSM (Variable Length Subnet Mask)
- Allows administrators to subnet networks flexibly
- Example: Breaking `10.0.0.0/8` (Class A) into `10.0.0.0/24` or `10.0.0.0/26` subnets
- Maximizes address space efficiency

---

## 📋 Concept Coverage Check

<details>
<summary><strong>✅ Click to verify covered concepts</strong></summary>

| Concept | Covered |
|---------|---------|
| Public vs Private Addresses | ✅ |
| APIPA | ✅ |
| RFC 1918 | ✅ |
| Loopback/Localhost | ✅ |
| Subnetting | ✅ |
| VLSM | ✅ |
| CIDR | ✅ |
| IPv4 Address Classes (A, B, C, D, E) | ✅ |

</details>

---

<p align="center">
  <em>IPv4 addressing provides the foundation for modern networking despite address limitations</em>
</p>

---

# 🖥️ Software Defined Networking (SDN) (1.8)

SDN separates a network device’s functions into **logical planes**:  
- **Data Plane** → Handles the actual traffic.  
- **Control Plane** → Decides *how* traffic should flow.  
- **Management Plane** → Allows administrators to manage and configure devices.  

---

## 🧱 Functional Planes

| Plane              | Role                                                       | Examples                                    |
|-------------------|------------------------------------------------------------|---------------------------------------------|
| **Data Plane**    | Does the heavy lifting: forwarding & processing packets     | Forwarding, NAT, Encryption, Trunking       |
| **Control Plane** | Manages decisions for the Data Plane                        | Routing tables, NAT tables, Session tables  |
| **Management Plane** | Administrator control over the device                     | Browser GUI, SSH, APIs                      |

---

## 🌐 SD-WAN (Software Defined Wide Area Network)

- Extends SDN to **Wide Area Networks**.  
- Designed for the **cloud era**: apps connect directly to the cloud instead of through a central data center.  

### ✨ Characteristics
- **App-aware routing** → Decisions based on application, QoS, priority.  
- **ZTP (Zero-Touch Provisioning)** → Devices auto-configure themselves.  
- **Dynamic routing** → Chooses the best path in real time.  
- **Transport agnostic** → Works over 5G, fiber, DSL, cable, etc.  
- **Centralized management** → Single controller for the entire WAN.  

---

## 🏢 Data Center Interconnect

- Connects multiple data centers across different locations.  
- Enables:  
  - Customer segmentation  
  - Application distribution (high availability)  
  - Workload mobility (apps can move between sites)  

---

## 🕸️ VXLAN (Virtual Extensible LAN)

VXLAN extends VLAN capabilities for large-scale, cloud-driven networks.  
Think of it as **“VLAN on steroids.”**

| Feature             | VLAN                     | VXLAN                        |
|---------------------|--------------------------|------------------------------|
| **Max Networks**    | ~4,000                   | ~16 million                  |
| **Encapsulation**   | OSI Layer 2              | OSI Layer 3 (tunneled)       |
| **Use Case**        | Small orgs / local nets  | Large corps / data centers   |

💡 **Key Benefits of VXLAN**:  
- Flexibility and scalability far beyond VLANs.  
- Supports data center interconnects across regions.  
- Ensures workloads and applications run smoothly despite IP differences.  

---

💡 **Key Takeaways:**  
- SDN = Separates **Data, Control, and Management** planes.  
- SD-WAN = Cloud-first WAN, app-aware and transport agnostic.  
- Data Center Interconnect = Connects workloads globally.  
- VXLAN = Scalable Layer 3 overlay, way beyond VLAN limits.
- Two **virtualization servers**, each with its own **virtual switch**.

**VLAN Encapsulation**
<p align="center" style="margin:0;padding:0;">
  <img src="https://github.com/user-attachments/assets/fcd00591-564b-4527-a46f-0ca9f2fa9cad" alt="vxlan" width="100%"/>
<br style="margin:0;padding:0;"/>

### ⚙️ Setup
- Two **virtualization servers**, each with its own **virtual switch**.  
- Each virtual switch has a **VTEP (VXLAN Tunnel Endpoint)**:  
  - 🖥️ **Server 1** → `VTEP = 1.1.1.1`  
  - 🖥️ **Server 2** → `VTEP = 2.2.2.2`  
- Each server hosts **3 virtual machines (VMs)**:  
  - **Server 1:** VM A1, VM B1, VM C1  
  - **Server 2:** VM A2, VM B2, VM C2  
- VM correspondence:  
  - A1 ↔ A2  
  - B1 ↔ B2  
  - C1 ↔ C2

### 🧩 VNI (Virtual Network Identifier)

Each virtual network is assigned a **VNI (Virtual Network Identifier):**

| Virtual Network | Assigned VNI |
|-----------------|--------------|
| **A** | 2000 |
| **B** | 3000 |
| **C** | 4000 |

> These VNIs are **identical on both servers**, ensuring that each side knows which VXLAN segment the traffic belongs to.

### 🚀 VXLAN Tunnel

When **A1** wants to communicate with **A2**, VXLAN encapsulation is used:

1. The **virtual switch** encapsulates A1’s Ethernet frame.  
2. It wraps the frame with the following headers:  
   - **VXLAN Header** → contains `VNI 2000`  
   - **UDP Header** → VXLAN rides over UDP  
   - **IP Header** → source `1.1.1.1`, destination `2.2.2.2`  
   - **Ethernet Header** → outer frame for physical transport  

### 🎯 At the Destination VTEP

1. The **outer headers** (Ethernet, IP, UDP, VXLAN) are **removed**.  
2. The **original Ethernet frame** is delivered to the target VM (**A2**).  
3. This allows **Layer 2 communication** to occur **over a Layer 3 infrastructure** — bridging networks virtually.

---

# 🔒 Zero Trust

## What is Zero Trust?

- **Zero Trust** literally means *zero trust*.  
- As technology grows, so do the threats — and to keep up, we adopt Zero Trust.  
- In Zero Trust, once you pass the firewall, you still can’t access anything beyond what your role allows.  
- **Everything must be verified:** people, devices, and processes.  
- You may have to go through **MFA**, **encryption**, **monitoring**, and **system permissions** every step of the way.

---

## 🧩 Policy-Based Authentication

### Adaptive Identity

- Considers the **context** — source, device, and requested resource.  
- Example:  
  If you log in from another device other than the company's device, a new location, or an odd time, **adaptive identity** will still allow access but with extra **MFA**.

### Policy-Based Access Control (PBAC)

- Similar to adaptive identity, but uses **predefined rules**.  
- Think of it like a **rulebook**:  
  - Using a non-company device → ❌ Denied.  
  - Logging in at odd hours or suspicious location → ❌ Blocked.  
  - Same company device, normal hours → ✅ Granted access.

---

## 🔐 Authorization

- Kicks in **after authentication** is complete.  
- Determines **what systems, apps, or data** you can access — and **how much**.  
- Example:  
  - *Helpdesk Technician* → hardware systems only.  
  - *Helpdesk Manager* → can modify databases or systems.  
  - *User* → access limited to their desktop.  
- Access is also controlled by **time**, **location**, and **device**:  
  - Remote + odd hours + unknown device → limited access.  
  - Office + company device + work hours → full access.

---

## ⚙️ Least Privilege Access

- Means giving **only the minimum required permissions** to perform your job.  
- Example:  
  - Helpdesk Manager → no access to Networking.  
  - Networking → no access to Finance.  
  - Everyone stays within their lane.  
- If everyone had admin rights and a **malware** breach occurred, the malware would gain admin-level control — total disaster.  
  👉 Hence, *least privilege is mandatory.*

---

## 🌐 SASE (Secure Access Service Edge)

- Think of SASE as a **next-gen VPN** — but stronger.  
- It combines:  
  - VPN  
  - Firewall  
  - Zero Trust  
  - Threat Protection  
  - Secure Web Gateway  
  — all in one **cloud-delivered** package.  
- Built into **all company-provided devices**.  
- Works for:  
  - Remote workers  
  - Field agents  
  - Corporate office employees  
- You don’t need to toggle it on or off — it’s **always active**, running **before your apps** like cloud services, data centers, SaaS platforms, and the internet.

---

🧭 *Zero Trust is not about paranoia — it’s about precision. Verify everything. Trust nothing.*

---

# 🏗️ Infrastructure as Code (IaC)

## ⚙️ What is IaC?

- **Infrastructure as Code (IaC)** means managing and provisioning your network and systems through **code** instead of manual setup.  
- You can **create, deploy, test, and modify** entire environments using scripts.  
- Once your code works, you can **reuse or clone** it to build identical infrastructures anytime.  
- IaC is a **core part of modern cloud computing** — automating configuration, scaling, and maintenance.

---

## 📘 Playbook

- A **playbook** acts as a **response guide** when something goes wrong — like a **security breach** or **ransomware recovery**.  
- It provides **step-by-step recovery actions**, ensuring consistent and quick responses.  
- Playbooks are **reusable** and **modifiable** — you can tweak them anytime to match new procedures.  
- Integrated into:  
  - **SOAR (Security Orchestration, Automation & Response)**  
  - **SIEMs**, **threat intelligence**, and **third-party tools**

---

## 🔐 Automation & Configuration Use Case

- Suppose you have **100 routers** with different firmware versions — instead of updating manually, you can **automate all upgrades** through one IaC script.  
- IaC allows:  
  - Automated **patching** and **deployment**  
  - Testing existing infrastructure setups  
  - Real-time **configuration management** and **change control**  
- You can modify network or software systems with **a single line of code**, scaling or reverting instantly as needed.

---

## 🗂️ Source Control

- Multiple **definition files (IaC scripts)** evolve over time — source control ensures you always use the **latest, verified version**.  
- With **version control systems** like **Git**, changes can be tracked, reviewed, and rolled back when needed.  
- In collaborative environments:  
  - Changes from multiple users are **automatically merged and tracked**.  
  - Updates are stored in a **central repository** to prevent loss or conflicts.

---

### 🧩 Controlling the Source Code

- When several developers edit the same code simultaneously, conflicts can occur.  
- Sometimes merges are automatic — other times, **manual selection** is required to keep the best version.  
- To minimize chaos, use the **branching workflow**:  



