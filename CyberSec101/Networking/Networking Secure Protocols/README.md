# TLS

### What is TLS?

Transport Layer Security (TLS) is a cryptographic protocol released in 1999 by the IEFT designed to provide secure communication over an insecure network. TLS was developed as an improved replacement for SSL (Secure Sockets Layer) and helps protect data by ensuring confidentiality and integrity during transmission. It prevents attackers from reading or modifying sensitive information such as passwords, emails, and financial data while it travels across the network.

### How TLS is Applied

TLS is commonly applied to many modern internet protocols to secure communication between clients and servers. For example, HTTP becomes HTTPS, allowing web traffic to be encrypted and protected from interception. TLS is also used in secure email and messaging protocols such as SMTPS and IMAPS, ensuring that sensitive data remains private and authentic during transmission. If a protocol ends in S it most likely because it use SLS or TLS.

### How TLS is set up & used

The first step for every server that needs to identify itself is to get a signed TLS certificate. This is done by the server administrator creating a Certificate Signing Request (CSR) and submitting it to a Certificate Authority (CA) for verification, after which the CA issues a digital certificate. After the certificate is issued, the certificates from the signing authorities must be installed on the host so the authenticity of the certificate can be verified. 

### What is the protocol name that TLS upgraded and built upon?

Answer: S 

### Which type of certificates should not be used to confirm the authenticity of a server?

Answer: self-signed certificate

# HTTP

### HTTP Basics

  HTTP relies on TCP and use port 80 by defauil, and HTTP was able to be esaily intercepted and monitored as it was transmitted as clear text. For the web browser to request a page over HTTP it must do 2 things. 
  1) Establish a TCP three-way handshake with the target server
  2) Communicater using the HTTP protocl; =====> issue requests, such as GET/HTTP/1.1

# HTTPS

### HTTPS Basics

HTTPS is fundementally the same as HTTP however no we are eestablishing a TLS session which is how we obtain the secure. In accordance the number of steps for establishing a connection is a total of 3 steps.
  1) Establish a TCP three way handshake with the target server
  2) Establish a TLS session
  3) Communicate using the HTTP protocol

The benefits of doing this is that bad parties can no longer view the content of the exchanged packets unless you have a private key thus addressing the main issue of HTTP.

### How many packets did the TLS negotiation and establishmnet take in the WIRESHARK HTTPS screenshots above?

Answer: 8

### What is the number of the packet that contain the GET /login when accessing the website over HTTPS?

Answer: 10
# Secure Email Protocols

### TLS with Email Protocols

Just like HTTP becomes HTTPS when TLS is added, email protocols can also use TLS for secure communication. SMTP, POP3, and IMAP become SMTPS, POP3S, and IMAPS when combined with TLS. This encryption protects sensitive information such as usernames, passwords, and email content from being intercepted during transmission.

#### If you capture network traffic, in which of the following protocols can you extract login credentials: SMTPS, POP3S, or IMAP?

Answer: IMAP

# SSH

  ### What is SSH?

Secure Shell (SSH) is a secure network protocol developed to safely access and manage remote systems over an insecure network. SSH was created as a secure replacement for TELNET, which transmitted data such as usernames and passwords in plaintext. 

### Benefits of SSH

SSH provides several security advantages including secure authentication, encrypted communication, and protection against man-in-the-middle attacks. It also supports tunneling, which allows other protocols to securely pass through an SSH connection, and X11 forwarding for running graphical applications remotely.

#### What is the name of the open-source implementation of the SSH protocol?

Answer: OpenSSH

# SFTP & FTPS

  ### What is SFTP & FTPS

SFTP stands for SSH File Transfer Protocol and allows secure file transfers between systems over an encrypted SSH connection. Since it is part of the SSH protocol suite SFTP uses port 22 and provides secure authentication and encrypted communication during file transfers.

FTPS stands for File Transfer Protocol Secure and is a secure version of FTP that uses TLS encryption similiar to how HTTPS secures HTTP traffic. Unlike SFTP, FTPS typically uses port 990 and requires TLS certificates to establish secure communication between the client and server.

### FLAG
THM{Protocols_secur3d}

# VPN

### What is a VPN?

A Virtual Private Network (VPN) allows users or remote offices to securely connect to a private network over the Internet. A VPN creates an encrypted tunnel between the client and the VPN server, allowing sensitive data to travel securely across public networks. This makes remote users appear as if they are connected directly to the main company network or acess stuff that is region based

### Benefits of a VPN

VPNs provide privacy and security by encrypting network traffic and protecting it from interception or monitoring. They can also hide a user’s public IP address by routing traffic through the VPN server, which can make the user appear to be browsing from another geographical location.

### How VPNs Work

A VPN client connects to a VPN server and establishes an encrypted tunnel for communication. Once connected, traffic is routed securely through the VPN tunnel before reaching its destination. This protects the confidentiality and integrity of transmitted data while using public Internet infrastructure.

### What would you use to connect the various company sites so that users at a remote office can access resources located within the main branch?

VPN

# Closing Section
### One of the packets contains login credentials. What password did the user submit?

First, we loaded the randy-chromium.pcapng file into Wireshark. Afterward, we followed the instructions provided in the screenshots to decrypt the TLS traffic so the encrypted packets could be analyzed. Once the traffic was decrypted, I began scrolling through the packets and noticed that packet 365 contained a POST request related to a login attempt, which suggested that this packet and the surrounding packets could contain useful information. After inspecting packet 365 and not finding anything relevant, I moved to packet 366 and expanded all its section for more details. While scrolling through the packet contents I found the flag located under the HTTP/2 headers with the flag being THM{B8WM6P}
