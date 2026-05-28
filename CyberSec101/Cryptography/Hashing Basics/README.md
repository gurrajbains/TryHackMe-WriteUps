# Introduction

A hash value is a fixed-size string of characters that is computed by a hash function. A hash function takes an input and produces an output of a fixed length.

## Hash Functions

Encryption is not the same as hashing because there is no key involved, and it is designed to be practically impossible to recover the original input from the output.

For a good hash function, the output is very difficult to predict. Even a single-character change in the input can produce a drastically different hash value.

##Examples of Hashes

Common hash functions include MD5, SHA-1, SHA-256, and SHA-512. Hash values are often represented using hexadecimal or Base64 encoding.

## Importance

Hashing is important in cybersecurity because it helps protect data integrity and ensures password confidentiality. For example, a server typically does not store your actual password. Instead, it stores a hash of the password. When you log in, the password you enter is hashed and compared to the stored hash. If the hashes match, access is granted; otherwise, the login attempt is rejected.

## Hash Collisions

A hash collision occurs when two different inputs produce the same hash output. Hash functions are designed to minimize the likelihood of collisions, but they cannot eliminate them entirely.

## Why Collisions Happen

Hash collisions are unavoidable because hash functions have a limited number of possible outputs, while the number of possible inputs is practically unlimited. As a result, different inputs must eventually produce the same hash value.
### Example

If a hash function produces a 4-bit hash value, only 16 different hash outputs are possible.

2^4 = 16

Since infinitely many inputs exist but only 16 outputs are available, some inputs must eventually produce the same hash value thus leading the collision.

### Insecure Hash Algorithms

MD5 and SHA1 are now considered insecure because researchers have successfully created intentional hash collisions against them. Due to these vulnerabilities, they should not be trusted for password hashing or data integrity verification.

## Questions 

What is the SHA256 hash of the passport.jpg file in ~/Hashing-Basics/Task-2?

77148c6f605a8df855f2b764bcc3be749d7db814f5f79134d2aa539a64b61f02

What is the output size in bytes of the MD5 hash function?

16

If you have an 8-bit hash output, how many possible hash values are there?

256 -- Each bit has 2 different choices 0 and 1 and there are 8 thus 2^8
# Password Storage and Hashing

### Overview

Hashing is commonly used in cyber security for password storage and data integrity verification. When used for authentication, systems do not need to store the original password and as mentioned they store a hash of the password and compare hashes during login attempts.

### Plaintext Password Storage

Storing passwords in plaintext is extremely insecure because anyone who gains access to the database can immediately view all user passwords. One major example was the RockYou data breach, where millions of plaintext passwords were leaked.

### Insecure Encryption

Some companies attempted to store passwords using outdated encryption algorithms instead of secure hashing. In the Adobe data breach, attackers were able to recover many passwords because the encryption method was weak and password hints were stored in plaintext.

### Insecure Hashing Algorithms

Using weak hashing algorithms such as SHA-1 is also insecure. LinkedIn suffered a major data breach because SHA-1 was used without password salting, making passwords easier to crack.

### Password Salting

Password salting involves adding a random value to a password before hashing it. This helps protect against attacks such as rainbow table lookups and prevents identical passwords from producing identical hashes.

### Question

#### What is the 20th password in `rockyou.txt`?

Answer: qwerty

# Using Hashing to Store Passwords

### Why Hash Passwords?

Instead of storing passwords directly, systems store the hash value of the password using a secure hashing algorithm. This improves security because if the database is leaked, attackers must crack the hashes before discovering the original passwords.

### Rainbow Tables

A rainbow table is a precomputed lookup table that maps hashes to plaintext passwords. Attackers can use rainbow tables to quickly identify passwords associated with unsalted hashes.

#### Example Rainbow Table

| Hash | Password |
|---|---|
| 02c75fb22c75b23dc963c7eb91a062cc | zxcvbnm |
| e10adc3949ba59abbe56e057f20f883e | 123456 |
| e99a18c428cb38d5f260853678922e03 | abc123 |
| 4c5923b6a6fac7b7355f53bfe2b8f8c1 | inS3CyourP4$$ |

### Password Salting

To defend against rainbow table attacks, systems add a unique random value called a salt to each password before hashing it. This ensures that even if two users share the same password, their stored hashes will still be different.

### Secure Password Storage

Modern password storage should use secure hashing algorithms such as:

- Argon2
- Bcrypt
- Scrypt
- PBKDF2

These algorithms are designed specifically for password hashing and include protections such as salting and computational cost adjustments.

### Why Not Encrypt Passwords?

Passwords used for authentication should generally not be encrypted because encryption requires storing a decryption key. If the key is compromised, attackers could decrypt every stored password. Hashing avoids this problem because hashes are designed to be one-way functions rather than two way.

### Questions

#### What password matches the hash `4c5923b6a6fac7b7355f53bfe2b8f8c1`?

Answer: inS3CyourP4$$

#### What is the plaintext for the hash `5b31f93c09ad1d065c0491b764d04933`?

Answer: tryhackme

#### Should passwords be encrypted in password-verification systems?

Answer: Nay

# Hash Identification

### Overview

From an offensive security perspective, it is important to identify the type of hash before attempting to crack it. While automated tools can help identify hashes, they are not always reliable and should be used alongside contextual information.

### Hash Recognition

Tools such as HashID can assist in identifying hash formats, but some hashes share similar lengths and structures. For example, MD5 and NTLM hashes can appear very similar, making context an important factor when determining the correct hash type.

### Linux Password Hashes

On Linux systems, password hashes are stored in /etc/shadow, which is normally only accessible by the root user. Password entries contain information such as the hashing algorithm, options, salt, and hash value.

### Example

$y$j9T$76UzfgEM5PnymhQ7TlJey1$/OOSg64dhfF.TigVPdzqiFang6uZA4QA1pzzegKdVm4

Breaking it down:

- $y$ indicates yescrypt
- j9T contains algorithm parameters
- 76UzfgEM5PnymhQ7TlJey1 is the salt
- The final section is the hash value

### Windows Password Hashes

Windows systems store password hashes in the Security Accounts Manager (SAM) database while Modern Windows systems primarily use NTLM hashes.

### Questions

#### What is the hash size in yescrypt?

Answer: 256

#### What is the Hash-Mode listed for Cisco-ASA MD5?

Answer: 2410

#### What hashing algorithm is used in Cisco-IOS if it starts with `$9$`?

Answer: scrypt

# Cracking Password Hashes

### Overview

To recover the original password a attacker must perform password cracking by hashing many candidate passwords and comparing the results against the target hash. 

### Password Cracking Tools

Two of the most common password cracking tools are:

- Hashcat
- John the Ripper

These tools automate the process of testing large numbers of possible passwords against a target hash.

### GPU Acceleration

Modern GPUs contain thousands of cores and can perform the mathematical operations required for hashing much faster than traditional CPUs. 
Some algorithms such as Bcrypt are intentionally designed to resist GPU acceleration and remain expensive to compute thus slowing down the process to crack the hash.


### Cracked Hashes

#### Hash 1

$2a$06$7yoU3Ng8dHTXphAg913cyO6Bjs3K5lBnwq5FJyA6d01pMSrddr1ZG

Answer: 85208520

#### Hash 2

9eb7ee7f551d2f0ac684981bd1f1e2fa4a37590199636753efe614d4db30e8e1

Answer: halloween

#### Hash 3

$6$GQXVvW4EuM$ehD6jWiMsfNorxy5SINsgdlxmAEl3.yif0/c3NqzGLa0P.S7KRDYjycw5bnYkF5ZtB8wQy8KnskuWQS3Yr1wQ0

Answer: spaceman

#### Hash 4

b6b0d451bbf6fed658659a9e7e5598fe

Answer: funforyou

