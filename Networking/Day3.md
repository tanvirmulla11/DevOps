# 📘 TCP/IP Reference Model
## The TCP/IP (Transmission Control Protocol / Internet Protocol) suite is a set of communication protocols used for connecting network devices on the Internet. It also serves as the communication backbone for private networks such as intranets and extranets.

## 🌐 What is the IP Protocol?

At the Network Layer, the Internet is viewed as a collection of subnetworks or Autonomous Systems (AS) connected together.
The protocol used at this layer is Internet Protocol (IP).

## 🧩 Main Responsibilities of IP

Provides best-effort delivery of datagrams from source to destination

Does not guarantee delivery, ordering, or reliability

Handles fragmentation and reassembly as data travels across networks

Delivers packets across multiple heterogeneous networks

## 📦 How IP Communication Works

A datagram arrives from the Transport Layer.

IP may fragment it into smaller pieces depending on network MTU.

Each fragment travels independently through routers.

At the destination, fragments are reassembled into the original datagram.

## 📌 Datagram (IP Packet)

In IP, packets are called datagrams.

A datagram contains two parts:
| Part       | Description                                           |
| ---------- | ----------------------------------------------------- |
| **Header** | 20–60 bytes; contains routing and control information |
| **Data**   | The actual payload                                    |

Maximum datagram size: 65,536 bytes (64 KB)

## 🧱 IPv4 Header Fields (Explained)
### 1. Version
Specifies the IP version.
Current version: IPv4 → Binary: 0100.

### 2. Header Length (HLEN)

Length of header in multiples of 4 bytes

4-bit value → max 15 × 4 = 60 bytes

### 3. Service Type (Type of Service – ToS)

Defines how a datagram should be handled:

Priority

Throughput

Reliability

Delay characteristics

(Modern equivalent: DSCP)

### 4. Total Length

16-bit field

Specifies the full length of datagram (header + data)

Maximum: 65,535 bytes

### 5. Identification

Used during fragmentation.
All fragments of a datagram carry the same identification value.

### 6. Flags

Indicate fragmentation behavior:

Can fragment?

Last fragment?

More fragments pending?

### 7. Fragmentation Offset

Points to the position of a fragment relative to the original datagram.

### 8. Protocol

Specifies which Transport Layer protocol the datagram carries.

### Examples:

6 → TCP

17 → UDP

1 → ICMP

### 9. Time to Live (TTL)

Indicates how many hops/routers a packet can pass

Decremented by each router

When TTL reaches zero → packet discarded

Prevents routing loops

### 10. Header Checksum

A 16-bit checksum used to verify only the header, not data.

### 11. Source Address

32-bit field

Identifies the origin of the packet

### 12. Destination Address

32-bit field

Identifies the target of the packet

### 13. Options 

Provides extra functionality such as:

Routing control

Timestamps

## 🏷️ IP Addressing

In addition to physical (MAC) addresses, the Internet requires a logical addressing scheme.

An IPv4 address = 32 bits (4 bytes)
It contains 3 parts:

Class Type

Network ID (NetID)

Host ID (HostID)

The size of each part varies by address class (A, B, C, D, E).
Security

Alignment

Not commonly used in modern networks.
