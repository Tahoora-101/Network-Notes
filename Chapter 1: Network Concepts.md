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



