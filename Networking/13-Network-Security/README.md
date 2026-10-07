Network Security

Network security is the practice of protecting networks, devices, services, and data from unauthorized access, misuse, disruption, and attacks.

Network security combines technologies, configurations, policies, and security controls.

---

1. Security Goals

Three important goals of information security are:

· Confidentiality
· Integrity
· Availability

These are commonly known as the CIA Triad.

Confidentiality

Confidentiality means preventing unauthorized people from accessing information.

```text
Authorized User ─────> Data
Unauthorized User ──X─> Data
```

Integrity

Integrity means protecting data from unauthorized modification.

```text
Original Data
     |
     v
Protected Data
     |
     v
No Unauthorized Changes
```

Availability

Availability means keeping systems and services accessible when they are needed.

```text
User ─────> Network ─────> Service
                 |
              Available
```

---

2. Authentication

Authentication verifies the identity of a user or device.

Examples include:

· Username and password
· Multi-factor authentication
· Digital certificates

The basic idea is:

```text
User
 |
 | Credentials
 v
Authentication
 |
 +----> Valid
 |
 +----> Invalid
```

Authentication answers:

«Who are you?»

---

3. Authorization

Authorization determines what an authenticated user or device is allowed to access.

```text
Authentication
      |
      v
Authorization
      |
      +----> Allowed
      |
      +----> Denied
```

Authentication identifies the user.

Authorization determines what the user can do.

---

4. Accounting

Accounting records and tracks activities performed by users or systems.

Examples include:

· Login records
· Access records
· System activity
· Network activity

Authentication, authorization, and accounting are often considered together as AAA:

```text
Authentication
       |
       v
Authorization
       |
       v
Accounting
```

---

5. Firewall

A firewall controls network traffic according to defined rules.

```text
Internet
   |
Firewall
   |
Internal Network
```

A firewall can allow or block traffic based on factors such as:

· Source
· Destination
· Protocol
· Port
· Direction

Example:

```text
Internet ───> Firewall ───> Server
                 |
             Security Rule
```

---

6. Firewall Rules

A firewall can contain rules such as:

```text
Allow TCP 443
Block TCP 23
Allow SSH from trusted network
Block unauthorized traffic
```

The exact rules depend on the network architecture and security requirements.

---

7. DMZ Security

A DMZ can be used to isolate public-facing services from an internal network.

```text
                 Internet
                    |
                 Firewall
                    |
                   DMZ
                    |
                 Firewall
                    |
              Internal LAN
```

If a public-facing service is compromised, segmentation can help reduce direct access to internal systems.

---

8. Encryption

Encryption converts readable data into a protected form.

```text
Plaintext
    |
    v
Encryption
    |
    v
Ciphertext
```

The ciphertext can be converted back into readable data through decryption when the appropriate key is available.

```text
Ciphertext
    |
    v
Decryption
    |
    v
Plaintext
```

---

9. Symmetric Encryption

Symmetric encryption uses the same secret key for encryption and decryption.

```text
              Same Secret Key
               /          \
              v            v
Plaintext -> Encryption -> Ciphertext
Ciphertext -> Decryption -> Plaintext
```

Advantages

· Fast
· Efficient for large amounts of data

Challenge

The secret key must be securely shared between the communicating parties.

---

10. Asymmetric Encryption

Asymmetric encryption uses a pair of keys:

· Public key
· Private key

```text
Public Key
    |
    v
Encryption
    |
    v
Ciphertext
    |
    v
Private Key
    |
    v
Decryption
```

The public key can be shared, while the private key should be protected.

---

11. Public and Private Keys

A public key can be distributed to other parties.

A private key should remain under the control of its owner.

```text
Public Key  ──> Can be shared
Private Key ──> Must be protected
```

Asymmetric cryptography can be used for secure communication and digital signatures.

---

12. Hashing

Hashing converts input data into a fixed-length output called a hash.

```text
Input Data
    |
    v
 Hash Function
    |
    v
Hash Value
```

Example:

```text
Data
 |
 v
SHA-256
 |
 v
Hash
```

Hashing is different from encryption because a cryptographic hash is designed as a one-way transformation.

Hashing can be used for:

· Integrity verification
· Password protection
· File verification

---

13. Hashing vs Encryption

Feature Hashing Encryption
Main Purpose Integrity / verification Confidentiality
Reversible Designed to be one-way Yes, with the appropriate key
Uses Keys Normally no Yes
Output Hash value Ciphertext

---

14. Network Attacks

Networks can be targeted by different types of attacks.

Examples include:

· Denial-of-Service attacks
· Distributed Denial-of-Service attacks
· Man-in-the-Middle attacks
· Sniffing
· Spoofing
· Password attacks
· Malware-based attacks

The appropriate defense depends on the attack and network architecture.

---

15. Denial of Service

A Denial-of-Service (DoS) attack attempts to make a service or system unavailable.

```text
Attack Traffic
      |
      v
   Server
      |
      X
   Service
Unavailable
```

A Distributed Denial-of-Service (DDoS) attack uses multiple sources to generate attack traffic.

```text
Attacker 1 ──┐
Attacker 2 ──┼──> Target
Attacker 3 ──┤
Attacker 4 ──┘
```

---

16. Man-in-the-Middle

A Man-in-the-Middle (MitM) attack occurs when an attacker positions themselves between communicating parties and attempts to intercept or manipulate communication.

```text
User ─────> Attacker ─────> Server
```

Encryption and authentication can help protect communications against MitM attacks.

---

17. Sniffing

Sniffing refers to capturing and analyzing network traffic.

```text
Network Traffic
      |
      v
Traffic Capture
      |
      v
Traffic Analysis
```

Unencrypted traffic is especially vulnerable to being read if an attacker can capture it.

---

18. Spoofing

Spoofing involves pretending to be another device, user, or network identity.

Examples include:

· IP spoofing
· MAC spoofing
· Email spoofing

The attacker attempts to make traffic appear to originate from a trusted source.

---

19. Defense in Depth

Defense in depth means using multiple security controls instead of relying on a single security mechanism.

```text
Internet
   |
Firewall
   |
Network Segmentation
   |
Authentication
   |
Access Control
   |
Protected Systems
```

If one security control fails, other controls can still provide protection.

---

20. Basic Network Security Practices

Important security practices include:

· Use strong authentication.
· Protect private keys and credentials.
· Apply appropriate firewall rules.
· Segment sensitive networks.
· Encrypt sensitive communications.
· Monitor network activity.
· Keep systems and services appropriately maintained.
· Limit unnecessary network access.
· Use secure protocols where possible.

---

Security Concepts Comparison

Concept Main Purpose
Authentication Verify identity
Authorization Control access
Accounting Record activity
Firewall Filter network traffic
Encryption Protect confidentiality
Hashing Verify data / protect stored credentials
Network Segmentation Isolate network areas
DMZ Isolate public-facing services

---

Key Takeaways

· Network security protects systems, networks, services, and data.
· The CIA Triad consists of confidentiality, integrity, and availability.
· Authentication verifies identity.
· Authorization determines access permissions.
· Accounting records activity.
· Firewalls control network traffic according to security rules.
· DMZs can isolate public-facing services.
· Symmetric encryption uses one shared secret key.
· Asymmetric encryption uses public and private keys.
· Hashing is primarily used for integrity and verification.
· DoS attacks attempt to make services unavailable.
· DDoS attacks use multiple sources.
· MitM attacks target communication between parties.
· Sniffing involves capturing network traffic.
· Spoofing involves falsifying an identity or source.
· Defense in depth uses multiple security controls.

---

Practice

1. What are the three components of the CIA Triad?
2. What is the difference between authentication and authorization?
3. What does AAA stand for?
4. What is the purpose of a firewall?
5. What is the purpose of a DMZ?
6. Explain the difference between symmetric and asymmetric encryption.
7. What is the difference between a public key and a private key?
8. What is hashing used for?
9. Explain the difference between hashing and encryption.
10. What is a DoS attack?
11. What is the difference between DoS and DDoS?
12. What is a Man-in-the-Middle attack?
13. What is network sniffing?
14. What is spoofing?
15. Explain the idea of defense in depth.
