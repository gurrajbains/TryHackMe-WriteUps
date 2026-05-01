# Introduction

Nmap is a open-source network scanner than can be adapted to various scenarious and setups which was first published in 1997

Nmap can be adapted for many different environments and scanning scenarios because of its large number of features and scanning options.

Some common uses of Nmap include:

* Discovering live hosts on a network
* Identifying open ports on target systems
* Detecting running services
* Detecting service versions
* Auditing network security
* Mapping network infrastructure

# Host Discovery: Who is online 

## Ways to Target

There are many ways to target systems in Nmap. Users can specify targets using IP ranges subnets or hostnames depending on what they want to scan.

### IP Range Use

If you want to scan a range of IP addresses you can use the - symbol and list the range.

Example:

nmap 192.168.0.1-10

This would scan all IP addresses from:

192.168.0.1 to 192.168.0.10

### IP Subnet Using 

If you want to scan an entire subnet you can use CIDR notation with /.

Example:

nmap 192.168.0.1/24

This would be equivalent to scanning:

192.168.0.0-255

### Hostname

Nmap can also target systems using hostnames instead of IP addresses which will produce the same effects as an IP.

Example:

nmap example.thm

### Answers

What is the last IP address that will be scanned when your scan target is 192.168.0.1/27?

Command --> nmap 192.168.0.1/27

Results : 192.168.0.31

# Port Scanning: Who is Listenining

## Overview

After discovering live hosts with Nmap the next step is finding what network services are running on those systems. A network service is any process listening for incoming connections on a TCP or UDP port.

Common examples include:

- Web servers usually running on TCP ports 80 and 443
- DNS servers usually running on UDP port 53
- SSH services usually running on TCP port 22

Both TCP and UDP contain 65,535 possible ports. Nmap helps identify which of these ports are open and what services are listening on them.

## Connect Scan

The TCP connect scan uses the -sT option.

This scan attempts to complete the full TCP three-way handshake with every target port. If the port is open the connection is established and then closed by Nmap.

Example:

nmap -sT MACHINE_IP

## SYN Scan Stealth Scan

The SYN scan uses the -sS option.

Instead of completing the full TCP three-way handshake Nmap only sends a SYN packet. If the target responds with SYN-ACK Nmap knows the port is open and sends a RST packet instead of completing the connection.

Example:

nmap -sS MACHINE_IP

## UDP Scan

Many services also use UDP such as:

- DNS
- DHCP
- NTP
- SNMP
- VoIP

UDP scanning can be performed using the -sU option.

Example:

nmap -sU MACHINE_IP

## Limiting Target Ports

The -F option scans only the 100 most common ports.

Example:

nmap -F MACHINE_IP

The -p option allows scanning specific ports or ranges.

Example:

nmap -p10-1024 MACHINE_IP

Example:

nmap -p- MACHINE_IP

## Summary

| Option | Explanation |
|---|---|
| -sT | TCP connect scan complete three-way handshake |
| -sS | TCP SYN scan only sends SYN packet |
| -sU | UDP scan |
| -F | Fast mode scans 100 common ports |
| -p[range] | Scan specific ports or ranges |

## Answers

### How many TCP ports are open on the target system at MACHINE_IP?

Command --> nmap -sS MACHINE_IP

Results : 6 open TCP ports found

### Find the listening web server on MACHINE_IP and access it with your browser. What is the flag that appears on its main page?

Command --> nmap -sS -sV MACHINE_IP

Results : Found HTTP service running on port 8008

Browser Access :

http://MACHINE_IP:8008

Flag :

THM{SECRET_PAGE_38B9P6}

# Version Detection: Extract More Information

## OS Detection

Nmap can detect the operating system running on a target machine using the -O option.

Example:

nmap -sS -O MACHINE_IP

## Service and Version Detection

Nmap can identify services and their versions running on open ports using the -sV option.

Example:

nmap -sS -sV MACHINE_IP

## Aggressive Scan

The -A option enables multiple advanced scanning features at once.

This includes:

- OS detection
- Service version detection
- Traceroute
- Additional scan features

Example:

nmap -A MACHINE_IP

## Forcing the Scan

The -Pn option forces Nmap to treat hosts as online even if they do not respond.

Example:

nmap -Pn MACHINE_IP

## Summary

| Option | Explanation |
|---|---|
| -O | Operating system detection |
| -sV | Service and version detection |
| -A | Enables OS detection version detection and additional features |
| -Pn | Scan hosts that appear to be down |

## Answers

### What is the name and detected version of the web server running on MACHINE_IP?

Command --> nmap -sS -sV MACHINE_IP

Results : lighttpd 1.4.74

# Timing: How Fast is Fast

## Timing Templates

Nmap allows users to control scan timing using different timing templates.

Available timing templates include:

- T0 paranoid
- T1 sneaky
- T2 polite
- T3 normal
- T4 aggressive
- T5 insane

Example:

nmap -T4 MACHINE_IP

or

nmap -T aggressive MACHINE_IP

## Parallel Probes

Nmap can control how many probes run simultaneously using:

--min-parallelism

and

--max-parallelism

## Packet Rate Control

Users can also control packet sending speed using:

--min-rate

and

--max-rate

## Host Timeout

The --host-timeout option sets the maximum time Nmap waits for a target host.

## Summary

| Option | Explanation |
|---|---|
| -T0 to -T5 | Timing templates from paranoid to insane |
| --min-parallelism | Minimum number of parallel probes |
| --max-parallelism | Maximum number of parallel probes |
| --min-rate | Minimum packet sending rate |
| --max-rate | Maximum packet sending rate |
| --host-timeout | Maximum time to wait for a host |

## Answers

### What is the non-numeric equivalent of -T4?

Command --> nmap -T4 MACHINE_IP

Results : -T aggressive

# Output: Controlling What You See

## Verbose Output

The -v option enables verbose output during scans.

Example:

nmap -v MACHINE_IP

Users can increase verbosity further using:

- -vv
- -vvvv
- -v2
- -v4

## Debugging Output

Nmap provides debugging output using the -d option.

Example:

nmap -d MACHINE_IP

Higher debugging levels can also be used such as:

-d9

## Saving Scan Reports

### Normal Output

Example:

nmap -oN report.txt MACHINE_IP

### XML Output

Example:

nmap -oX report.xml MACHINE_IP

### Grepable Output

Example:

nmap -oG report.gnmap MACHINE_IP

### Save All Formats

Example:

nmap -oA report MACHINE_IP

## Summary

| Option | Explanation |
|---|---|
| -v | Verbose output |
| -d | Debugging output |
| -oN | Save normal output |
| -oX | Save XML output |
| -oG | Save grepable output |
| -oA | Save all major output formats |

## Answers

### What option must you add to your nmap command to enable debugging?

Command --> nmap -d MACHINE_IP

Results : -d

# Conclusion and Summary

## Overview

In this room we learned how to use Nmap to discover live hosts scan ports identify services detect operating systems and control scan timing and output formatting.

Running Nmap with sudo privileges allows access to more advanced scan types such as SYN scans while running as a local user limits some advanced functionality.

## Important Options Summary

| Option | Explanation |
|---|---|
| -sL | List targets without scanning |
| -sn | Host discovery only |
| -sT | TCP connect scan |
| -sS | TCP SYN scan |
| -sU | UDP scan |
| -F | Scan 100 common ports |
| -p[range] | Specify port range |
| -Pn | Treat hosts as online |
| -O | Operating system detection |
| -sV | Service version detection |
| -A | Aggressive scan with extra detection |
| -T0 to -T5 | Timing templates |
| -v | Verbose output |
| -d | Debugging output |
| -oN | Save normal output |
| -oX | Save XML output |
| -oG | Save grepable output |
| -oA | Save all output formats |

## Answers

### What kind of scan will Nmap use if you run nmap MACHINE_IP with local user privileges?

Results : Connect Scan
