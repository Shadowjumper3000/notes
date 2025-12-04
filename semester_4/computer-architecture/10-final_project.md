# Networking
## IP Addressing Scheme
### IPv4
We will use /28 Network Mask to allow for 14 adresses
- Netword Address, Broadcast Adddress and Default Gateway
- 11 hosts -> 10 Drones, 1CC
To maintain stable connection, especially with a VPN (Wireguard), we will use Static Addressing.

### IPv6
We will include IPv6/64 for Future Proofing of the Project, /64 allows for plenty of addresses. It will allow for easier Network Merging later on as IPv6 has Private addressing and Unique Identifiers. In a VPN Mesh Network this reduces Overhead.

## Routing Configuration
### VPN Routing
- Wireguard will be used as a VPN due to low overhead and simple automatic connection management.
- For direct connection mesh topology, we must enter each peer in an allowed peer config for each device. This will result in more difficult scaling later on but can be centralized with server. As we don't want to have a Hub-and-Spoke setup where all traffic is forced through hub.
### Internet Routing
#### Split Tunnel
- Traffic bound for the Internet is not routed through the CC, which reduces bottlenecking and throtteling but increases security risks.
#### Full Tunnel
- All Traffic bound for outside the VPN network is routed through the CC which makes Security/Monitoring easier and reduces outbound attack vectors. It increases bottlenecks.
#### IP Forwarding
- If Direct Connection fails between two nodes and traffic must be relayed, or traffic must be routed from one network to another, VPN to LAN. Then
### Secure Communication
#### WireGuard