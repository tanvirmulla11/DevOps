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

