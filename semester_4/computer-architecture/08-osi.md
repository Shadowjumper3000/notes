# OSI Model vs. TCP/IP Protocol Suite

## OSI Model (7 Layers)
A theoretical framework for network communication, standardized by ISO.

| Layer          | Function                                                                                     | Protocols/Examples                          |
|----------------|---------------------------------------------------------------------------------------------|--------------------------------------------|
| **7. Application**  | User-facing services (APIs, interfaces).                                                    | HTTP, FTP, SMTP, DNS, SSH                  |
| **6. Presentation** | Data translation (encryption, compression, encoding).                                        | SSL/TLS, JPEG, ASCII, MPEG                 |
| **5. Session**      | Manages connections (establish, maintain, terminate).                                        | NetBIOS, RPC, SIP                          |
| **4. Transport**    | End-to-end data delivery (reliability, flow control).                                        | TCP (reliable), UDP (unreliable)           |
| **3. Network**      | Logical addressing and routing (path determination).                                         | IP, ICMP, OSPF, BGP, ARP                   |
| **2. Data Link**    | Framing, MAC addressing, error detection (local network).                                    | Ethernet, Wi-Fi (802.11), PPP, MAC addresses |
| **1. Physical**     | Raw bit transmission (cables, signals, hubs).                                               | Fiber, Copper, RF, Repeaters               |

### Key Points:
- **Layer 7–5**: "Upper layers" (software-oriented).  
- **Layer 4–1**: "Lower layers" (hardware/network-oriented).  
- **Encapsulation**: Data flows down (headers added) and up (headers removed).  

---

## TCP/IP Model (4 Layers)
A practical implementation used in the modern internet.

| Layer              | OSI Equivalent          | Key Protocols                              | Function                                   |
|--------------------|-------------------------|--------------------------------------------|--------------------------------------------|
| **Application**    | App, Presentation, Session | HTTP, FTP, SMTP, DNS, Telnet, SNMP, RIP   | Combines OSI Layers 5–7 for simplicity.    |
| **Transport**      | Transport               | TCP (connection-oriented), UDP (connectionless) | Ensures data integrity or speed.           |
| **Internet**       | Network                 | IP, ICMP, IGMP                             | Routing and logical addressing (IPs).      |
| **Network Access** | Data Link + Physical    | Ethernet, Wi-Fi, PPP, ATM, Frame Relay    | Hardware addressing (MAC) and transmission.|

### Key Differences from OSI:
1. **Fewer Layers**: TCP/IP merges OSI’s top 3 layers into **Application** and bottom 2 into **Network Access**.  
2. **Focus on IP**: Designed around the Internet Protocol (IP).  
3. **No Session/Presentation**: Handled by applications (e.g., TLS in HTTPS).  

---

## Key Protocols Explained
### Application Layer (TCP/IP)
| Protocol | Purpose                          | Port  |
|----------|----------------------------------|-------|
| **HTTP**  | Web page transfer (unencrypted). | 80    |
| **HTTPS** | Secure HTTP (TLS encryption).    | 443   |
| **FTP**   | File transfer.                   | 20/21 |
| **SMTP**  | Email sending.                   | 25    |
| **DNS**   | Domain → IP resolution.          | 53    |
| **SNMP**  | Network monitoring.              | 161   |
| **RIP**   | Routing updates (legacy).        | 520   |

### Transport Layer
| Protocol | Reliability | Use Case                          |
|----------|------------|-----------------------------------|
| **TCP**  | ✅ (ACKs)  | Web browsing, emails, file transfers. |
| **UDP**  | ❌ (fast)  | Video streaming, VoIP, gaming.    |

### Internet Layer
- **IP** (v4/v6): Delivers packets best-effort (no reliability).  
- **ICMP**: Diagnostics (e.g., `ping`, `traceroute`).  
- **ARP**: Maps IP → MAC addresses (local network).  

### Network Access Layer
- **Ethernet (802.3)**: Wired LANs (MAC addresses).  
- **Wi-Fi (802.11)**: Wireless LANs.  
- **ATM/Frame Relay**: Legacy WAN technologies.  

---

## Data Flow Example: Loading a Website
1. **Application**: Browser sends HTTP request (Layer 7).  
2. **Transport**: TCP splits data into segments (Layer 4).  
3. **Internet**: IP adds source/dest addresses (Layer 3).  
4. **Network Access**: Ethernet frames packets for LAN (Layer 2–1).  
5. **Router**: Strips Ethernet header, routes via IP (Layer 3).  
6. **Destination**: Reverse process (decapsulation).  

---

## Why Two Models?
- **OSI**: Theoretical, for education/design.  
- **TCP/IP**: Practical, powers the modern internet.  

> 💡 **Fun Fact**: The TCP/IP model is older (1970s, ARPANET) but simpler. OSI (1984) was an attempt to standardize globally.