# Wireshark HTTP Packet Analysis Lab

## Project Overview

This laboratory exercise focuses on analyzing network traffic using **Wireshark**, a widely used packet capture and network protocol analysis tool. The lab was completed as part of **CNT 4713 – Net-Centric Computing** at **Florida International University (FIU)** under the instruction of **Professor Xavier Caddle**.

The exercise involved examining a provided packet capture (trace) and using Wireshark's interfaces to identify network protocols, inspect HTTP communication, determine endpoint IP addresses, identify the originating web browser, measure HTTP response time, and examine TCP transport-layer information.

The lab provides practical experience with how application-layer protocols such as **HTTP** interact with transport-layer protocols such as **TCP**, while demonstrating how packet analysis tools can be used to investigate network communication at a granular level.

---

## Objective

The primary objectives of this laboratory were to:

* Identify the protocols present within a network trace.
* Analyze an HTTP request and its corresponding server response.
* Determine the response time of an HTTP transaction.
* Identify the client and web server IP addresses.
* Examine HTTP request metadata, including the User-Agent field.
* Identify the TCP destination port associated with HTTP traffic.
* Develop practical skills in interpreting packet-level network communication.

---

## Technologies & Tools

* **Wireshark** – Network protocol analyzer and packet inspection tool
* **Packet Capture / Trace File** – `intro-wireshark-trace-1`

---

## Methodology

### 1. Load the Packet Trace

The provided `intro-wireshark-trace-1` packet capture was opened in Wireshark. The trace was obtained from the Wireshark trace archive associated with the Kurose and Ross networking laboratory materials.

The capture was then examined using Wireshark's:

* Packet List pane
* Packet Details pane
* Packet information fields

These views were used to investigate the different protocol layers and fields contained within the captured network traffic.

---

### 2. Identify the Protocols Present

The **Protocol** column in Wireshark's packet-listing interface was examined to determine which protocols were represented in the trace. The following protocols were identified:

| Protocol    | Layer / Role                | Observation                                            |
| ----------- | --------------------------- | ------------------------------------------------------ |
| **TCP**     | Transport layer             | Provides reliable transport for the HTTP communication |
| **HTTP**    | Application layer           | Carries the web request and server response            |
| **TLS 1.2** | Security / encryption layer | Represents encrypted traffic observed in the capture   |

This provided an initial overview of the different protocol layers involved in the communication.

---

### 3. Measure HTTP Response Time

The HTTP transaction was analyzed by locating the client's **HTTP GET request** and the corresponding **HTTP OK response** from the server.

Wireshark's packet timestamps were used to determine the elapsed time between the two packets.Therefore, the response time was calculated as:

**HTTP Response Time = Timestamp of HTTP OK − Timestamp of HTTP GET**
**HTTP Response Time = 8.501613 − 8.472728**

The resulting response time was:

**0.029 seconds (29 ms)**

This indicates that approximately 29 milliseconds elapsed between the observed HTTP request and the corresponding server response in the packet trace.

---

### 4. Identify the Web Server IP Address

The packet information associated with the HTTP communication was examined to determine the destination/server IP address. The web server was identified as:

**128.119.245.12**

This address corresponds to the `gaia.cs.umass.edu` server used by the laboratory trace.

---

### 5. Identify the Client IP Address

The source IP address associated with the HTTP request was examined to identify the client machine that initiated the communication. The client IP address was:

**10.0.0.44**

This address belongs to the private IPv4 address space and represents the client endpoint within the captured network environment.

---

### 6. Identify the Web Browser

The HTTP GET request was inspected in Wireshark's **Packet Details** pane. For that reason, the HTTP request headers were expanded to examine the **User-Agent** field, which provides information about the software that generated the request. The browser identified from the User-Agent information was:

**Mozilla Firefox**

This demonstrates how application-level metadata contained within network packets can be used to identify the client software responsible for generating a request.

---

### 7. Identify the TCP Destination Port

The TCP segment carrying the HTTP communication was examined by expanding the **Transmission Control Protocol** section in Wireshark's Packet Details pane. The destination port was identified as:

**Port 80**

TCP port 80 is the conventional port associated with unencrypted HTTP traffic. This observation demonstrates the relationship between the application-layer HTTP protocol and the transport-layer TCP protocol.

---

## Key Concepts Analyzed

### Packet Capture and Inspection

Wireshark captures and displays network packets, allowing individual protocol headers and fields to be inspected. This provides visibility into network communication that is normally abstracted away from the user.

### Protocol Layering

The trace demonstrates the interaction between different layers of the networking stack. In particular, the HTTP application-layer communication is transported using TCP at the transport layer.

### HTTP Request/Response Communication

The captured traffic illustrates the request/response model used by HTTP, where a client sends an HTTP request, and the server returns an HTTP response.

### IP Addressing

The analysis involved identifying the IPv4 addresses associated with the client and server endpoints.

### TCP Ports

The TCP destination port provides information about the application service to which the traffic is being directed. Port 80 is conventionally associated with HTTP.

### HTTP Headers and User-Agent Identification

HTTP headers contain metadata associated with an HTTP request. The User-Agent field can provide information about the software used by the client to generate the request.

### Network Timing Analysis

Packet timestamps can be used to measure the time elapsed between network events, such as an HTTP request and its corresponding response.

### Protocol Analysis

Examining packets at the protocol-field level provides a practical method for understanding how network applications communicate across the Internet.

---

## Skills Demonstrated

* Network traffic analysis
* Packet capture analysis
* Wireshark packet inspection
* TCP/IP protocol analysis
* HTTP request/response analysis
* IPv4 address identification
* TCP port identification
* HTTP header analysis
* User-Agent identification
* Network latency/response-time measurement
* Interpretation of packet-level network data
* Understanding of protocol layering

---

## Academic Context

The exercise is based on the Wireshark laboratory materials accompanying:

> Kurose, J. F., & Ross, K. W. *Computer Networking: A Top-Down Approach*, 9th Edition, Pearson, 2025.

The instructional materials and packet traces are provided by the authors as part of their **Wireshark Labs** resources. This repository contains my own analysis and observations performed for academic purposes; it is **not a reproduction of the textbook's original laboratory text or instructor solutions**. The packet trace used in this exercise, `intro-wireshark-trace-1`, was obtained from the trace archive referenced by the laboratory materials.

---

## Source & Attribution

**Primary textbook:**

Kurose, J. F., & Ross, K. W. (2025). *Computer Networking: A Top-Down Approach* (9th ed.). Pearson.

**Wireshark laboratory materials:**

Kurose and Ross, *Wireshark Labs*, associated with *Computer Networking: A Top-Down Approach*.

This repository acknowledges the original authors and publishers for the laboratory framework and packet-trace materials.

---

## Disclaimer

This repository is intended for **educational and portfolio purposes**. The original laboratory exercise, instructional materials, and packet traces are the property of their respective authors and publisher. The repository does not claim ownership of those materials.

---

## Conclusion

This laboratory provided hands-on experience analyzing real packet-level network traffic using Wireshark. By examining the captured communication, I was able to identify the protocols involved, analyze an HTTP transaction, determine client and server addressing information, inspect HTTP metadata, measure response time, and connect application-layer behavior with TCP transport-layer information. This exercise strengthened my practical understanding of **computer networking, TCP/IP, HTTP, packet analysis, and network troubleshooting methodologies**.
