# CS 6250 Key Concepts Reference

## Networking Models

### OSI Model (7 Layers)
| Layer | Name | PDU | Key Protocols |
|-------|------|-----|---------------|
| 7 | Application | Data | HTTP, DNS, SMTP, FTP |
| 6 | Presentation | Data | SSL/TLS, JPEG, ASCII |
| 5 | Session | Data | NetBIOS, RPC |
| 4 | Transport | Segment | TCP, UDP |
| 3 | Network | Packet | IP, ICMP, OSPF, BGP |
| 2 | Data Link | Frame | Ethernet, ARP, PPP |
| 1 | Physical | Bits | USB, Bluetooth, DSL |

### TCP/IP Model (4 Layers)
| Layer | Corresponds To |
|-------|----------------|
| Application | OSI 5-7 |
| Transport | OSI 4 |
| Internet | OSI 3 |
| Network Access | OSI 1-2 |

## Core Protocols

### Ethernet (IEEE 802.3)
- Frame structure: Preamble | Dest MAC | Src MAC | Type/Length | Payload | FCS
- Minimum frame size: 64 bytes (to detect collisions)
- Maximum frame size: 1518 bytes (without jumbo frames)
- MAC address: 48-bit unique hardware identifier

### ARP (Address Resolution Protocol)
- Maps IP addresses to MAC addresses
- ARP Request: broadcast to all hosts on LAN
- ARP Reply: unicast response from target host
- ARP cache: temporary storage of IP-MAC mappings
- Gratuitous ARP: host announces its own IP-MAC mapping

### IPv4
- 32-bit addresses written as dotted decimal (e.g., 192.168.1.1)
- Classful addressing: Class A (0-127), B (128-191), C (192-223), D (multicast), E (reserved)
- Subnet mask divides network and host portions
- CIDR notation: IP/prefix length (e.g., 192.168.1.0/24)

### IPv6
- 128-bit addresses written as hexadecimal groups
- Simplified header format for faster processing
- No broadcast; uses multicast and anycast
- Built-in IPsec support
- Auto-configuration via SLAAC

## Routing Concepts

### Forwarding vs Routing
- **Forwarding**: Moving packet from input to output port (data plane)
- **Routing**: Determining path from source to destination (control plane)

### Longest Prefix Match
- Forwarding table lookup finds longest matching prefix
- More specific routes take priority
- Example: /24 matches before /16 for same destination

### Distance-Vector Routing (RIP)
- Each router shares routing table with neighbors
- Uses hop count as metric (max 15 hops)
- Bellman-Ford algorithm for path calculation
- Vulnerable to count-to-infinity problem
- Split horizon and poison reverse as countermeasures

### Link-State Routing (OSPF)
- Each router floods link-state information to all routers
- Dijkstra's algorithm builds shortest path tree
- Faster convergence than distance-vector
- Supports hierarchical routing with areas
- Uses cost (typically bandwidth-based) as metric

### BGP (Border Gateway Protocol)
- Path-vector protocol for inter-domain routing
- AS (Autonomous System) path determines routing
- Policy-based routing decisions
- TCP port 179 for communication
- iBGP (within AS) vs eBGP (between ASes)

## Transport Layer

### TCP (Transmission Control Protocol)
- Connection-oriented, reliable, ordered delivery
- 3-way handshake: SYN → SYN-ACK → ACK
- 4-way teardown: FIN → ACK → FIN → ACK
- Flow control: receiver window size
- Congestion control:慢启动, AIMD, 快速恢复

#### TCP Congestion Control Algorithms
1. **Slow Start**: exponential growth until threshold
2. **Congestion Avoidance**: linear growth (additive increase)
3. **Fast Retransmit**: retransmit after 3 duplicate ACKs
4. **Fast Recovery**: reduce window by half, not to 1

### UDP (User Datagram Protocol)
- Connectionless, unreliable, unordered
- No overhead for connection management
- Used for DNS queries, streaming, VoIP, gaming
- Checksum optional in IPv4, mandatory in IPv6

## Application Layer

### DNS (Domain Name System)
- Hierarchical naming: root → TLD → authoritative
- Recursive resolver queries on behalf of client
- Record types: A, AAAA, CNAME, MX, NS, TXT, SOA
- Caching at multiple levels (browser, OS, ISP)
- TTL controls cache duration

### HTTP (Hypertext Transfer Protocol)
- Request-response model (client-server)
- Methods: GET, POST, PUT, DELETE, PATCH, HEAD, OPTIONS
- Status codes: 1xx (info), 2xx (success), 3xx (redirect), 4xx (client error), 5xx (server error)
- Headers: metadata exchange
- HTTP/2: multiplexing, header compression, server push
- HTTP/3: QUIC protocol, UDP-based, 0-RTT connection

### TLS (Transport Layer Security)
- Provides encryption, authentication, integrity
- Handshake: ClientHello → ServerHello → Certificate → Key Exchange → Finished
- Symmetric encryption for data transfer
- Asymmetric encryption for key exchange
- Certificate authority (CA) trust model

## Network Security

### Attack Types
- **DDoS**: Distributed denial of service (volumetric, protocol, application)
- **Man-in-the-Middle**: intercepting communications
- **Spoofing**: impersonating legitimate source
- **SYN Flood**: exhausting server resources with half-open connections
- **ARP Poisoning**: redirecting traffic via fake ARP replies

### Defense Mechanisms
- **Firewalls**: packet filtering, stateful inspection, application-level
- **IDS/IPS**: intrusion detection and prevention systems
- **VPN**: encrypted tunnels (IPsec, OpenVPN, WireGuard)
- **Network Address Translation**: hiding internal addresses
- **Access Control Lists**: traffic filtering rules

## Wireless Networking

### IEEE 802.11 (Wi-Fi)
- CSMA/CA: carrier sense multiple access with collision avoidance
- Hidden terminal problem: RTS/CTS mechanism
- Standards: 802.11a/b/g/n/ac/ax (Wi-Fi 6)
- Channels and frequency bands (2.4 GHz, 5 GHz, 6 GHz)

### Cellular Networks
- 4G LTE: all-IP network, OFDMA
- 5G: higher bandwidth, lower latency, network slicing
- Handoff: maintaining connection during mobility
- Mobile IP: triangular routing through home agent

## Performance Metrics

### Bandwidth
- Maximum theoretical data rate
- Measured in bits per second (bps)

### Latency
- Time for packet to travel from source to destination
- Components: propagation delay, transmission delay, processing delay, queuing delay

### Throughput
- Actual rate of successful data transfer
- Always less than or equal to bandwidth

### Bandwidth-Delay Product
- BDP = Bandwidth × RTT
- Determines optimal TCP window size
- Represents "in-flight" data capacity
