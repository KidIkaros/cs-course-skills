# CS 6250 Practice Exercises

## Module 1: Network Fundamentals

### Exercise 1.1: Protocol Stack Identification
For each of the following scenarios, identify which protocol layer is primarily involved:

1. An Ethernet switch forwarding a frame based on MAC address
2. A router determining the best path using BGP
3. A web browser establishing a TLS connection
4. A network card converting bits to electrical signals
5. DNS resolving a domain name to an IP address

**Answers**: 1) Data Link, 2) Network, 3) Transport/Application, 4) Physical, 5) Application

### Exercise 1.2: Performance Calculations
A link has a bandwidth of 100 Mbps and a one-way propagation delay of 10 ms:

1. What is the bandwidth-delay product in bits?
2. If packets are 1000 bytes, how many packets can be "in flight"?
3. What is the minimum TCP window size needed to fully utilize this link?

**Answers**: 1) 1,000,000 bits, 2) ~125 packets, 3) 1,000,000 bits (125 KB)

## Module 2: Link Layer

### Exercise 2.1: Ethernet Frame Analysis
Given an Ethernet frame with the following hex dump:
```
FF FF FF FF FF FF 00 1A 2B 3C 4D 5E 08 00 45 00
00 3C 1C 46 40 00 40 06 B1 E6 AC 10 0A 63 AC 10
0A 0C
```

1. What is the destination MAC address?
2. What is the source MAC address?
3. What is the EtherType?
4. What protocol does this EtherType indicate?

### Exercise 2.2: ARP Scenario
Host A (192.168.1.10) wants to send a packet to Host B (192.168.1.20) on the same subnet. Host A's ARP cache is empty.

1. What ARP message does Host A send?
2. What is the destination MAC address of this ARP message?
3. What information does the ARP reply contain?
4. How long do ARP cache entries typically last?

## Module 3: Network Layer

### Exercise 3.1: Subnetting Practice
Given the network 10.0.0.0/8, create subnets for the following departments:

- Engineering: 500 hosts
- Marketing: 100 hosts
- Finance: 50 hosts
- Executive: 10 hosts

For each subnet, provide:
- Network address
- Subnet mask
- First usable host
- Last usable host
- Broadcast address

### Exercise 3.2: CIDR Aggregation
Can the following routes be summarized into a single CIDR route?

- 192.168.16.0/24
- 192.168.17.0/24
- 192.168.18.0/24
- 192.168.19.0/24

If yes, what is the summary route? If no, what is the most specific summary possible?

**Answer**: Yes, they can be summarized as 192.168.16.0/22

## Module 4: Routing

### Exercise 4.1: Distance-Vector Calculation
Given the following network topology with hop counts:

```
    A ---2--- B ---3--- C
    |         |         |
    4         1         2
    |         |         |
    D ---2--- E ---1--- F
```

Router A's routing table initially shows:
- A: 0, B: 2, D: 4, others: infinity

After receiving routing updates from B (B knows: A:2, C:3, E:1) and D (D knows: A:4, E:2):

1. What is A's updated route to C?
2. What is A's updated route to F?
3. What is A's updated route to E?

### Exercise 4.2: OSPF Cost Calculation
A router has three paths to a destination:

- Path 1: Links with bandwidths 100 Mbps, 100 Mbps, 10 Mbps
- Path 2: Links with bandwidths 50 Mbps, 50 Mbps, 50 Mbps
- Path 3: Links with bandwidths 1 Gbps

Using OSPF cost = 10^8 / bandwidth:

1. Calculate the cost for each path
2. Which path will OSPF select?
3. Is this always the best path in terms of throughput?

## Module 5: TCP

### Exercise 5.1: TCP Sequence Numbers
Host A sends a 4000-byte file to Host B using TCP with MSS = 1000 bytes. The initial sequence number is 1000.

1. What are the sequence numbers for each segment?
2. How many segments are sent?
3. If segment 2 is lost, what does Host B ACK?
4. Describe the retransmission process.

### Exercise 5.2: TCP Congestion Control
A TCP connection has cwnd = 4 KB and ssthresh = 32 KB. Trace the congestion window evolution for:

1. Slow start phase (5 RTTs)
2. What happens when cwnd reaches ssthresh?
3. If packet loss occurs at cwnd = 40 KB, what are the new values of cwnd and ssthresh?

## Module 6: DNS

### Exercise 6.1: DNS Resolution
Trace the DNS resolution process for www.example.com when the local cache is empty:

1. List each DNS query in order
2. Identify the type of each DNS server queried
3. What DNS record types are used?
4. How does caching affect subsequent lookups?

### Exercise 6.2: DNS Record Types
For a mail server at mail.example.com, what DNS records are needed?

1. A record for example.com
2. MX records for example.com
3. PTR record for reverse lookup
4. CNAME record for www.example.com pointing to example.com

## Module 7: HTTP

### Exercise 7.1: HTTP Request Analysis
Analyze the following HTTP request:

```
GET /index.html HTTP/1.1
Host: www.example.com
Accept: text/html,application/xhtml+xml
Accept-Encoding: gzip, deflate
Connection: keep-alive
If-Modified-Since: Wed, 21 Oct 2024 07:28:00 GMT
```

1. What HTTP method is used?
2. What version of HTTP?
3. What is the purpose of the If-Modified-Since header?
4. If the resource hasn't changed, what status code is returned?

### Exercise 7.2: HTTP Performance
Calculate the time to download a 10 MB file with the following conditions:

- RTT = 50 ms
- Bandwidth = 10 Mbps
- HTTP/1.1 with persistent connections
- 4 parallel TCP connections

1. What is the transmission delay?
2. How long for a single connection to download?
3. How long with 4 parallel connections?

## Module 8: Network Security

### Exercise 8.1: TLS Handshake Analysis
Describe each step in a TLS 1.3 handshake:

1. ClientHello message contents
2. ServerHello and certificate
3. Key exchange mechanism
4. How many round trips are needed?

### Exercise 8.2: Security Scenario
A company has the following network security requirements:

1. Encrypt all web traffic
2. Block incoming SSH connections
3. Allow VPN access from remote employees
4. Detect intrusion attempts

Match each requirement to the appropriate security mechanism:
- TLS certificates
- Firewall rules
- VPN gateway
- IDS/IPS

## Module 9: Wireless

### Exercise 9.1: Wi-Fi Channel Planning
A building has three Wi-Fi access points. Available channels in 2.4 GHz band: 1, 6, 11.

1. Which channels should be assigned to minimize interference?
2. If a fourth AP is needed, what channels can be reused?
3. How does 5 GHz band help in this scenario?

### Exercise 9.2: Hidden Terminal Problem
Two stations (A and C) are both within range of an access point (B) but not within range of each other.

1. Why can't A and C detect each other's transmissions?
2. What problem does this cause?
3. How does RTS/CTS solve this problem?
4. What is the overhead of RTS/CTS?

## Programming Assignments

### Assignment 1: Socket Programming
Implement a simple HTTP client in Python that:
1. Establishes a TCP connection
2. Sends an HTTP GET request
3. Parses the response headers
4. Downloads and saves the response body

### Assignment 2: Routing Simulation
Implement a distance-vector routing simulator that:
1. Creates a network topology
2. Exchanges routing tables between neighbors
3. Detects count-to-infinity scenarios
4. Implements split horizon optimization

### Assignment 3: Packet Analyzer
Using Python and raw sockets or Scapy:
1. Capture network packets
2. Parse Ethernet, IP, and TCP headers
3. Identify protocol types
4. Display packet contents in human-readable format

### Assignment 4: DNS Client
Build a DNS client that:
1. Sends DNS queries to recursive resolvers
2. Parses DNS responses
3. Handles different record types (A, AAAA, MX, CNAME)
4. Implements DNS caching
