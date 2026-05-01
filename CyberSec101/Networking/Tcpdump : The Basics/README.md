# Tcpdump Introduction

## Overview

This section introduces tcpdump a command-line packet analysis tool used for capturing and inspecting network traffic. By analyzing captured packets we can better understand how network protocols communicate and observe the network conversations that are usually hidden behind graphical user interfaces.

## What is Tcpdump

Tcpdump is a packet capture and analysis tool written in C and C++ for Unix-like systems. It allows users to capture packets apply filters and analyze network traffic directly from the command line. Tcpdump is widely used in networking and cybersecurity for troubleshooting and traffic analysis.

### Associated Library

Tcpdump relies on the libpcap library for packet capturing functionality. This library became the foundation for many modern networking and packet analysis tools.

# Question

## What is the name of the library that is associated with tcpdump?

### Answer

libpcap

# Tcpdump Basic Usage

## Overview

Tcpdump is a command-line packet capture and network analysis tool used to inspect network traffic in real time. It allows users to capture packets from network interfaces save captures to files and analyze packet data for troubleshooting or security analysis.

## Specifying a Network Interface

Before capturing traffic a network interface must be selected using the -i option. Users can capture traffic from a specific interface such as eth0 or listen on all available interfaces using -i any.

Example:

tcpdump -i eth0

## Capturing on All Interfaces

Users can listen on all available interfaces by using:

tcpdump -i any

## Saving Captured Packets

Captured traffic can be saved into a .pcap file using the -w option. These files can later be opened and analyzed in Wireshark.

Example:

tcpdump -i eth0 -w capture.pcap

## Reading Packets from a File

Tcpdump can also read previously captured packet files using the -r option. This is useful for analyzing saved network traffic or investigating attacks after they occur.

Example:

tcpdump -r capture.pcap

## Limiting Packet Capture

The -c option limits the number of packets captured before stopping automatically.

Example:

tcpdump -i eth0 -c 10

## Numeric Output

By default tcpdump attempts to resolve IP addresses and port numbers into names. The -n option disables hostname resolution and displays only numeric IP addresses.

Example:

tcpdump -i eth0 -n

## Verbose Output

The -v option increases the amount of detail displayed for captured packets. Additional verbosity can be enabled using -vv or -vvv.

Example:

tcpdump -i eth0 -v

# Question

## What option can you add to your command to display addresses only in numeric format?

### Answer

-n
