# Importance of Cryptography

### Overview

Cryptography is used to ensure secure communication in the presence of adversaries. It protects the confidentiality, integrity, and authenticity of transmitted data so attackers cannot easily read or modify sensitive information during transmission.

### Real-World Applications

Cryptography is used daily in many modern technologies and services. Examples include encrypted logins, secure SSH sessions, online banking, encrypted messaging, and file verification through hashing. Many industries also rely on cryptography to comply with security standards and regulations such as PCI DSS, HIPAA, GDPR, and DPA.


# Plaintext and Ciphertext

### Plaintext

Plaintext refers to the original readable data before encryption is applied. This could include text, files, passwords, or messages that can be understood directly by humans without any tools.

### Ciphertext

Ciphertext is the encrypted form of plaintext produced after encryption and as such ciphertext appears unreadable unless it is decrypted using the correct key.

### Encryption and Decryption

Encryption is the process of converting plaintext into ciphertext using an encryption algorithm and key. Decryption reverses this process by converting ciphertext back into readable plaintext using the corresponding key.

### Questions

#### What do you call the encrypted plaintext?

Answer: `ciphertext`

#### What do you call the process that restores the plaintext?

Answer: `decryption`

---

# Historical Ciphers

### Caesar Cipher

The Caesar Cipher is one of the earliest known encryption techniques. It works by shifting each letter in the plaintext by a fixed number of positions in the alphabet. For example, a shift of 3 changes A to D, B to E, and so on. A shift of 26 will be the orignal letters in the english alphabet

### Weaknesses

Although simple, the Caesar Cipher is considered insecure by modern standards because all possible shifts can easily be tested through brute force as there are only 25 possible shifts.

### Question

#### Knowing that `XIPXIRGCTI` was encrypted using Caesar Cipher, what is the original plaintext?

Answer: `LICANENCRYPT`

---

# Types of Encryption

### Symmetric Encryption

Symmetric encryption uses the same shared key for both encryption and decryption. Commonly used for encrypting large amounts of data due to how fast it is.

### Asymmetric Encryption

Asymmetric encryption uses two separate keys: a public key for encryption and a private key for decryption. This allows secure communication without sharing the private key publicly.

### Questions

#### What is the acronym for the algorithm?

Answer: `AES`

#### What would 2048 refer to as an asymmetric algorithm?

Answer: `bits`

---

# Basic Math

### XOR Operation

XOR is a logical operation commonly used in cryptography. It compares two bits and outputs `1` when the bits are different and `0` when they are the same.

#### Example

```text
1000 XOR 1111 -> 0111
```

---

### Modulo Operation

Modulo calculates the remainder after division and is commonly used in encryption algorithms and programming operations.

#### Examples

```text
10 % 5  -> 0
11 % 10 -> 1
10 % 11 -> 10
```

The remainder refers to the value left over after division when a number cannot be divided evenly.

---

### Questions

#### What is `1001 XOR 1010`?

Answer: `0011`

#### What is `1111 XOR 0000`?

Answer: `1111`

#### What is `5 MOD 3`?

Answer: `2`
