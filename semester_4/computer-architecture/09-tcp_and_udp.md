# TCP & UDP Notes

## 1. Overview
- **TCP (Transmission Control Protocol)**: Connection-oriented, reliable protocol.
- **UDP (User Datagram Protocol)**: Connectionless, unreliable protocol.

## 2. Key Differences

| Feature               | TCP                          | UDP                          |
|-----------------------|------------------------------|------------------------------|
| **Connection**        | Connection-oriented          | Connectionless               |
| **Reliability**       | Reliable (ACK, retransmission)| Unreliable (No ACK)           |
| **Ordering**         | In-order delivery            | No ordering guarantees        |
| **Speed**            | Slower (overhead)             | Faster (low overhead)         |
| **Header Size**      | 20-60 bytes                  | 8 bytes                      |
| **Flow Control**     | Yes (window scaling)         | No                           |
| **Congestion Control**| Yes                          | No                           |
| **Use Cases**        | Web, email, file transfer    | Video streaming, gaming, DNS |

## 3. TCP Features
- **Three-way Handshake**:
  1. SYN
  2. SYN-ACK
  3. ACK
- **Error Recovery**: Retransmits lost packets.
- **Flow Control**: Uses window size to manage data flow.
- **Congestion Control**: Algorithms like Tahoe, Reno, CUBIC.

## 4. UDP Features
- **No Handshake**: Direct data transmission.
- **Lightweight**: Minimal header (only source/dest ports, length, checksum).
- **Multicast Support**: Can send to multiple hosts simultaneously.
- **No Congestion Control**: Can overwhelm networks if unchecked.

## 5. When to Use Which?
- **Use TCP** when:
  - Data integrity is critical (e.g., file downloads).
  - Ordered delivery matters (e.g., web pages).
- **Use UDP** when:
  - Low latency is priority (e.g., VoIP, live streaming).
  - Small, frequent packets are sent (e.g., DNS queries).

## 6. Port Ranges
- **Well-known ports**: 0-1023 (e.g., HTTP:80, HTTPS:443, DNS:53).
- **Registered ports**: 1024-49151 (assigned by IANA).
- **Dynamic/Private ports**: 49152-65535 (ephemeral ports).

## 7. Common Protocols
- **TCP Protocols**:
  - HTTP/HTTPS
  - FTP
  - SMTP
  - SSH
- **UDP Protocols**:
  - DNS (usually)
  - DHCP
  - SNMP
  - QUIC (HTTP/3)

## 8. TCP Header Structure