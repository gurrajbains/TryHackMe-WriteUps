# Public Key Cryptography Basics

### Overview

Public key cryptography is known as asymmetric encryption, as it uses two separate keys for encryption and decryption. A public key is shared openly and used to encrypt data, while a private key is kept secret and used to decrypt the data. This allows secure communication without needing to share the private key publicly.

### Security Goals

Public key cryptography helps provide authentication, authenticity, integrity, and confidentiality. It is commonly used in secure communications, digital signatures, SSH authentication, TLS certificates, and encrypted messaging.

# Common Uses of Asymmetric Encryption

### Key Exchange

Asymmetric encryption is commonly used to securely exchange symmetric encryption keys over insecure networks. Once the symmetric key is exchanged securely, symmetric encryption can be used for faster communication.

### Analogy

Imagine a locked box, the lock represents the public key, while the key used to open the lock represents the private key. Anyone can place data into the locked box using the public key, but only the owner with the private key can unlock and read the contents.

### Question

#### In the analogy presented, what real object is analogous to the public key?

Answer: `Lock`

---

# RSA

### What is RSA?

RSA is one of the most widely used public key cryptography algorithms and it relies on mathematical operations involving very large prime numbers to generate secure encryption keys.

### How RSA Works

RSA uses a public key for encryption and a private key for decryption. The difficulty of factoring extremely large numbers helps make RSA secure.

### Questions

#### Knowing that `p = 151` and `q = 257`, what is `n`?

Answer: `38807`

#### Knowing that `p = 17`, `q = 23`, and `e = 65537`, what is `d`?

Answer: `305`

---

# Diffie-Hellman Key Exchange

### Overview

Diffie-Hellman is a key exchange method that allows two parties to securely establish a shared secret over an insecure network.

### How It Works

Both users agree on public values and privately generate secret numbers & through mathematical operations, both sides independently calculate the same shared secret without directly transmitting it.

### Questions

#### Consider `g = 3`, `p = 29`, Alice's secret is `10`, and Bob's secret is `7`. What is Alice's public key?

Answer: `5`

#### What is Bob's public key?

Answer: `12`

#### What is the shared secret?

Answer: `17`

---

# SSH

### SSH Authentication

SSH allows secure remote access to systems using encrypted communication. Authentication can be performed using passwords or SSH key pairs.

### SSH Key Pairs

SSH key authentication uses a public and private key pair. The public key is placed on the remote server, while the private key remains on the client system.

### Benefits

SSH key authentication is generally more secure than password authentication and helps prevent brute-force attacks.

### Question

#### Which SSH key is commonly used with modern systems?

Answer: `ed25519`

---

# Digital Signatures and Certificates

### Digital Signatures

Digital signatures verify the authenticity and integrity of data. A sender signs data using their private key and the recipient verifies the signature using the sender’s public key.

### Certificates

Certificates are digital documents used to associate public keys with verified identities. Certificate Authorities (CAs) are responsible for signing and validating certificates.

### Questions

#### What is required to sign for non-repudiation?

Answer: `private key`

#### What is used to sign for confidentiality?

Answer: `public key`

---

# PGP and GPG

### Overview

PGP (Pretty Good Privacy) and GPG (GNU Privacy Guard) are tools used for secure communication, encryption, and digital signatures.

### Features

GPG allows users to generate keys, encrypt data, decrypt data, and verify signatures using public key cryptography.

### Practical Example

A sender encrypts a message using the recipient’s public key, and the recipient decrypts the message using their private key.

### Question

#### User Y encrypts the message using User X's public key. What user can read the message?

Answer: `User X`
