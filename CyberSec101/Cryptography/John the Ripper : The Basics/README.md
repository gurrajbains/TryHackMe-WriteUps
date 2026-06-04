# Basics Terms 

## What are Hashes? 

   A hash is essentially a way of take a piece of data of any length and then converting it into another fixed-length form. This masks the original value of the input and since hases are one way, you can't recover an input from and output.

## Johns Purpose

  While we state that you can't recover an output from an input this isn't neccesarrily true as you can simply compare two different hashes until you get the correct hash. This is a brute force method which John The Ripper is a tool for attaking various hash types.

  ### Questions

 What is the most popular extended version of John the Ripper?

# John the Ripper Basics

### Overview

John the Ripper is a password-cracking tool used to perform dictionary attacks, brute-force attacks, and hash-cracking attacks against many different hash formats. The most popular version is Jumbo John, which extends the original tool with support for additional hash types and cracking features.

### Setting Up John

John the Ripper is included in many security-focused Linux distributions. The room uses the popular rockyou.txt wordlist, which contains millions of passwords obtained from the RockYou data breach.

#### Question

What website's breach was the rockyou.txt wordlist created from?

Answer: rockyou.com

---

# Basic Hash Cracking

### Basic Syntax

John the Ripper uses the following command structure:


john [options] [file]

Common options include:

--wordlist
--format

Before attempting to crack a hash, it is important to identify the hash type either through context or by using hash identification tools.

#### Questions

What type of hash is hash1.txt?

Answer: md5

What is the cracked value of hash1.txt?

Answer: biscuit

What type of hash is hash2.txt?

Answer: sha1

What is the cracked value of hash2.txt?

Answer: kangeroo

What type of hash is hash3.txt?

Answer: sha256

What is the cracked value of hash3.txt?

Answer: microphone

What type of hash is hash4.txt?

Answer: whirlpool

What is the cracked value of hash4.txt?

Answer: colossal

---

# Cracking Windows Authentication Hashes

### NTLM

Windows systems store password hashes using NTLM. These hashes are commonly extracted from the Security Accounts Manager (SAM) database and can be cracked using John the Ripper once the correct hash format is specified.

#### Question

What is the cracked value of the NTLM hash?

Answer: mushroom

---

# Single Crack Mode

### Overview

Single Crack Mode generates password candidates using information known about the target user, such as usernames and related account details. This method is effective when users create passwords based on personal information.

#### Question

What is Jack's password?

Answer: Joker

---

# Custom Rules

### Overview

Custom rules allow John the Ripper to modify words from a wordlist according to predefined patterns. These transformations can simulate common password creation habits such as adding numbers, symbols, or capital letters.

#### Questions

What do custom rules allow us to exploit?

Answer: Password complexity predictability

What rule would append a capital letter to the end of a word?

Answer: Az"[A-Z]"

What would you use to call a custom rule called TryHackMe?


--rule=TryHackMe

---

# Cracking Password-Protected ZIP Files

### zip2john

The zip2john utility extracts password hashes from ZIP archives and converts them into a format that John the Ripper can understand.


zip2john secure.zip > zip.hash


#### Questions

What is the password for the secure ZIP file?

Answer: pass123

What is the flag inside the ZIP file?

Answer: THM{w3ll_d0n3_h4sh_rul3}

---

# Cracking Password-Protected RAR Archives

### rar2john

The rar2john utility extracts password hashes from RAR archives and converts them into a format suitable for John the Ripper.


rar2john archive.rar > rar.hash

#### Questions

What is the password for the secure RAR file?

Answer: password

What is the flag inside the RAR file?

Answer: THM{r4r_4rch1ve_h4sh_t1m3}

---

# Cracking SSH Keys with John

### ssh2john

The ssh2john.py script converts encrypted SSH private keys into a format that John the Ripper can crack.


python ssh2john.py id_rsa ==> id_rsa.hash
 

After converting the key, the resulting hash can be attacked using a wordlist.

#### Question

What is the SSH private key password?

Answer: mango
