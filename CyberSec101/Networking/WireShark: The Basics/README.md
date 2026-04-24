# Introduction

## What is Wireshark

Wireshark is one of the most powerful traffic analysis tools available and is widely used for network analysis and cybersecurity investigations.

Some common uses of Wireshark include:

- Detecting and troubleshooting network problems such as network congestion, failure points, and connectivity issues.
- Detecting security anomalies such as rogue hosts, abnormal port usage, and suspicious traffic activity.
- Investigating and learning protocol details such as response codes, packet structures, and payload data.
  
### GUI & Data
#### Toolbar 	
The main toolbar contains multiple menus and shortcuts for packet sniffing and processing, including filtering, sorting, summarising, exporting and merging. 
#### Display 
Filter Bar	The main query and filtering section.
#### Recent Files	
List of the recently investigated files. You can recall listed files with a double-click. 
#### Capture Filter and Interfaces
Capture filters and available sniffing points (network interfaces).  The network interface is the connection point between a computer and a network. The software connection (e.g., lo, eth0 and ens33) enables networking hardware.
#### Status Bar	
Tool status, profile and numeric packet information.

<img width="1688" height="700" alt="image" src="https://github.com/user-attachments/assets/6de057ff-c2aa-4f90-8bf4-c2be18f18b13" />

 Packet Colouring

Wireshark uses packet colouring rules to help users quickly identify protocols and detect anomalies in traffic captures. Different colours represent different traffic types and conditions, making analysis faster and more efficient.

There are two types of colouring rules:
- **Temporary Rules** — only active during the current session.
- **Permanent Rules** — saved in the profile settings and available in future sessions.

Users can create custom colouring rules through:
- View → Coloring Rules
- Right-click context menus

The Colourise Packet List option can be used to enable or disable packet colouring.

# Traffic Sniffing

Wireshark allows users to capture live network traffic through packet sniffing.

- The **blue shark fin button** starts packet capture.
- The **red button** stops the capture.
- The **green restart button** restarts the capture process.

The status bar displays the active capture interface and the total number of captured packets.



# Merging PCAP Files

Wireshark can merge multiple pcap or pcapng files into a single capture file.

To merge files:
1. Navigate to File → Merge.
2. Select the additional capture file.
3. Wireshark will combine the packets into a new merged capture.

The merged file should be saved before further analysis.


# Viewing Capture File Details

Capture file details provide useful metadata when working with multiple packet captures.

Users can access file information through:
- Statistics → Capture File Properties
- The PCAP icon located in the bottom-left corner

Important details include:
- File hash values
- Capture timestamps
- File comments
- Interface information
- Packet statistics

# Answers

## Capture File Comment
TryHackMe_Wireshark_Demo

## Total Number of Packets
58620

## SHA256 Hash
f446de335565fb0b0ee5e5a3266703c778b2f3dfad7efeaeccb2da5641a6d6eb

# Packet Dissection

Packet dissection, also known as **protocol dissection**, is the process of analyzing packet details by decoding the protocols and fields contained within captured network traffic. Wireshark supports a large number of protocols for dissection, and users can also create custom dissector scripts for additional protocol analysis.

Packets are typically broken down into **5 to 7 layers** based on the OSI model. In this example, the packet contains seven distinct layers:

- Frame / Packet
- Source MAC Address
- Source IP Address
- Protocol
- Protocol Errors
- Application Protocol
- Application Data


## Layer 1 — Frame / Packet

The Frame layer provides information about the specific frame or packet being analyzed. It contains details related to the **Physical Layer** of the OSI model, such as frame number, arrival time, frame length, and encapsulation type.


## Layer 2 — Source and Destination MAC Addresses

This layer displays the **source and destination MAC addresses**. These addresses belong to the **Data Link Layer** of the OSI model and are used for communication between devices on the same local network.


## Layer 3 — Source and Destination IP Addresses

The third layer corresponds to the **Network Layer** of the OSI model. It shows the **source and destination IPv4 addresses**, which are used to route packets between different networks.


## Layer 4 — Protocol Information

The fourth layer contains information about the transport protocol being used, typically:

- **TCP (Transmission Control Protocol)**
- **UDP (User Datagram Protocol)**

This layer also shows the **source and destination port numbers** and belongs to the **Transport Layer** of the OSI model.


## Protocol Errors

This section is an extension of Layer 4 and mainly applies to TCP traffic. It shows TCP segments that needed to be reassembled or packets that may contain retransmissions or other communication issues.

TCP requires reliable delivery and guarantees data transmission, while UDP does not verify whether packets are fully received.


## Layer 5 — Application Protocol

The Application Protocol layer displays details specific to the protocol being used, such as:

- HTTP
- FTP
- SMB

This information belongs to the **Application Layer** of the OSI model.


## Application Data

Application Data is an extension of the Application Protocol layer and displays the actual application-specific content being transmitted within the packet.


# Exercise Answers

## Packet 38 Analysis

### Markup Language Used Under HTTP Protocol
eXtensible Markup Language

### Arrival Date of the Packet
05/13/2004

### TTL Value
47

### TCP Payload Size
424

### E-Tag Value
9a01a-4696-7e354b00

# Packet Navigation & Analysis Features

## Packet Numbers

Wireshark automatically assigns a unique number to every captured packet. Packet numbering helps analysts keep track of events within large captures and makes it easier to revisit specific packets during an investigation.


## Go To Packet

The **Go To Packet** feature allows users to quickly navigate to a specific packet number within the capture. This feature can also help analysts follow conversations and jump between related packets during analysis.

Users can access this feature through:
- Go menu
- Toolbar navigation options



## Finding Packets

Wireshark allows users to search for packets based on packet content and specific values.

This feature can be accessed through:
- Edit → Find Packet

Wireshark supports multiple search types, including:

- Display Filters
- Hex Values
- Strings
- Regular Expressions (Regex)

String and regex searches are commonly used during investigations.

Searches can be performed in different sections of the interface:

- Packet List Pane
- Packet Details Pane
- Packet Bytes Pane

Choosing the correct pane is important because some information may only exist in a specific section of the packet view.



## Marking Packets

Packet marking helps analysts identify packets of interest for future investigation.

Marked packets appear highlighted in black regardless of their original colouring rule. Packet marks are temporary and are removed once the capture file session is closed.

Packets can be marked through:
- Right-click context menu
- Edit menu



## Packet Comments

Wireshark allows analysts to add comments to packets for documentation and collaboration purposes.

Unlike packet marking, comments can remain saved within the capture file until manually removed.

This feature is useful for:
- Documenting suspicious activity
- Leaving notes for other analysts
- Highlighting important packets during investigations



## Exporting Packets

Large packet captures may contain thousands of packets. Wireshark allows users to export selected packets into a separate capture file for focused analysis.

This helps reduce unnecessary data and makes investigations easier to manage.

Exporting packets can be done through:
- File menu options



## Exporting Objects

Wireshark can extract files transferred across network traffic from supported protocols.

Supported protocols include:
- HTTP
- SMB
- TFTP
- IMF
- DICOM

This feature is valuable during forensic investigations because analysts can recover transferred files for deeper inspection.


## Time Display Format

By default, Wireshark displays packet timestamps as:

- Seconds Since Beginning of Capture

Users can change the timestamp format for easier analysis through:

- View → Time Display Format

UTC time formatting is commonly preferred during investigations.


## Expert Information

Wireshark includes an **Expert Information** feature that identifies possible anomalies and protocol issues within packet captures.

These alerts are grouped by severity:

| Severity | Colour | Description |
|---|---|---|
| Chat | Blue | General workflow information |
| Note | Cyan | Notable events or application responses |
| Warning | Yellow | Suspicious or unusual behaviour |
| Error | Red | Malformed packets or major issues |

Common alert categories include:

| Group | Description |
|---|---|
| Checksum | Checksum-related errors |
| Comment | Packet comment detection |
| Deprecated | Deprecated protocol usage |
| Malformed | Malformed packet detection |

Expert Information can be accessed through:
- Analyse → Expert Information
- Status bar notifications

# Answers 


## Search the "r4w" string in packet details

### Name of Artist 1
r4w8173


## Packet 12 Comments

### MD5 Hash Answer
911cd574a42865a956ccde2d04495ebf <=== Done by go to packet 12, extracting the pcked and than converting to MD5 via command or website



## Exported `.txt` File

### Alien Name
PACKETMASTER <=== Go to File , Go to Export Objects, filter for .txt. select the packet, and save it to your desktop and read it 


## Expert Information

### Number of Warnings
1636

# Packet Filtering

Wireshark has a powerful filtering engine that helps analysts narrow down traffic and focus on events of interest. There are two main types of filters:

- Capture Filters — used to capture only packets matching specific conditions.
- Display Filters — used to display packets matching conditions after capture.

Display filters help reduce noise and isolate important traffic.

## Apply as Filter

The "Apply as Filter" feature allows users to quickly create filters by right-clicking a field within a packet.

Accessible through:
- Right-click menu
- Analyse → Apply as Filter


## Conversation Filter

Conversation filters isolate all packets related to a communication stream based on IP addresses and ports.

Accessible through:
- Right-click menu
- Analyse → Conversation Filter

## Colourise Conversation

This feature highlights packets belonging to the same conversation without filtering out other traffic.

Accessible through:
- Right-click menu
- View → Colourise Conversation


## Prepare as Filter

Creates a filter query without immediately applying it. The query is added to the filter bar for further editing.


## Apply as Column

Allows users to create custom columns from packet fields to simplify analysis across multiple packets.


## Follow Stream

The "Follow Stream" feature reconstructs communication streams at the application level.

This helps analysts inspect:
- usernames
- passwords
- files
- application data

Supported stream types include:
- TCP
- UDP
- HTTP


# Simple Display Filters

## Filter by Protocol Name

http
ftp
smtp
arp

## Filter by Port Number

tcp.port == 80
udp.port == 53

## Filter by IP Address

ip.addr == 192.168.1.2

# Exercise Answers

## HTTP Filter Query

http

## Number of Displayed Packets

1089

## Total Number of Artists

3

## Name of the Second Artist

Blad3
