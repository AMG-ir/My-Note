# 13 - Network Security

Network security is the practice of protecting networks, devices, services, and data from unauthorized access, misuse, disruption, and attacks. It combines technologies, configurations, policies, and security controls.

## Contents

- [Security Goals](#security-goals)
- [Authentication, Authorization, and Accounting](#authentication-authorization-and-accounting)
- [Firewall](#firewall)
- [DMZ Security](#dmz-security)
- [Encryption](#encryption)
- [Hashing](#hashing)
- [Network Attacks](#network-attacks)
- [Defense in Depth](#defense-in-depth)
- [Basic Network Security Practices](#basic-network-security-practices)
- [Security Concepts Comparison](#security-concepts-comparison)
- [Key Takeaways](#key-takeaways)
- [Practice](#practice)

---

## Security Goals

Three important goals of information security are confidentiality, integrity, and availability. These are commonly known as the CIA Triad.

### Confidentiality

Preventing unauthorized people from accessing information.

```text
Authorized User ------> Data
Unauthorized User --X-> Data
```

### Integrity

Protecting data from unauthorized modification.

```text
Original Data
     |
     v
Protected Data
     |
     v
No Unauthorized Changes
```

### Availability

Keeping systems and services accessible when they are needed.

```text
User -----> Network -----> Service
                 |
             Available
```

---

## Authentication, Authorization, and Accounting

### Authentication

Authentication verifies the identity of a user or device. Examples include:

- Username and password
- Multi-factor authentication
- Digital certificates

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

Authentication answers: who are you?

### Authorization

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

Authentication identifies the user. Authorization determines what the user can do.

### Accounting

Accounting records and tracks activities performed by users or systems. Examples include:

- Login records
- Access records
- System activity
- Network activity

Authentication, authorization, and accounting are often considered together as AAA.

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

## Firewall

A firewall controls network traffic according to defined rules.

```text
Internet
   |
Firewall
   |
Internal Network
```

A firewall can allow or block traffic based on factors such as:

- Source
- Destination
- Protocol
- Port
- Direction

### Firewall Rules

A firewall can contain rules such as:

```text
Allow TCP 443
Block TCP 23
Allow SSH from trusted network
Block unauthorized traffic
```

The exact rules depend on the network architecture and security requirements.

---

## DMZ Security

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

## Encryption

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

### Symmetric Encryption

Symmetric encryption uses the same secret key for encryption and decryption.

```text
              Same Secret Key
               /          \
              v            v
Plaintext -> Encryption -> Ciphertext
Ciphertext -> Decryption -> Plaintext
```

- Advantages: fast, efficient for large amounts of data.
- Challenge: the secret key must be securely shared between the communicating parties.

### Asymmetric Encryption

Asymmetric encryption uses a pair of keys: a public key and a private key.

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

### Public and Private Keys

```text
Public Key  --> Can be shared
Private Key --> Must be protected
```

Asymmetric cryptography can be used for secure communication and digital signatures.

---

## Hashing

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

Hashing is different from encryption because a cryptographic hash is designed as a one-way transformation. Hashing can be used for:

- Integrity verification
- Password protection
- File verification

### Hashing vs Encryption

| Feature       | Hashing                    | Encryption |
|---------------|----------------------------|------------|
| Main Purpose  | Integrity / verification   | Confidentiality |
| Reversible    | Designed to be one-way     | Yes, with the appropriate key |
| Uses Keys     | Normally no                | Yes |
| Output        | Hash value                 | Ciphertext |

---

## Network Attacks

Networks can be targeted by different types of attacks. Examples include:

- Denial-of-Service attacks
- Distributed Denial-of-Service attacks
- Man-in-the-Middle attacks
- Sniffing
- Spoofing
- Password attacks
- Malware-based attacks

The appropriate defense depends on the attack and network architecture.

### Denial of Service

A Denial-of-Service (DoS) attack attempts to make a service or system unavailable.

```text
Attack Traffic
      |
      v
   Server
      |
      X
Service Unavailable
```

A Distributed Denial-of-Service (DDoS) attack uses multiple sources to generate attack traffic.

```text
Attacker 1 --+
Attacker 2 --+--> Target
Attacker 3 --+
Attacker 4 --+
```

### Man-in-the-Middle

A Man-in-the-Middle (MitM) attack occurs when an attacker positions themselves between communicating parties and attempts to intercept or manipulate communication.

```text
User -----> Attacker -----> Server
```

Encryption and authentication can help protect communications against MitM attacks.

### Sniffing

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

### Spoofing

Spoofing involves pretending to be another device, user, or network identity. Examples include:

- IP spoofing
- MAC spoofing
- Email spoofing

The attacker attempts to make traffic appear to originate from a trusted source.

---

## Defense in Depth

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

## Basic Network Security Practices

- Use strong authentication.
- Protect private keys and credentials.
- Apply appropriate firewall rules.
- Segment sensitive networks.
- Encrypt sensitive communications.
- Monitor network activity.
- Keep systems and services appropriately maintained.
- Limit unnecessary network access.
- Use secure protocols where possible.

---

## Security Concepts Comparison

| Concept              | Main Purpose |
|----------------------|--------------|
| Authentication       | Verify identity |
| Authorization        | Control access |
| Accounting           | Record activity |
| Firewall             | Filter network traffic |
| Encryption           | Protect confidentiality |
| Hashing              | Verify data / protect stored credentials |
| Network Segmentation | Isolate network areas |
| DMZ                  | Isolate public-facing services |

---

## Key Takeaways

- Network security protects systems, networks, services, and data.
- The CIA Triad consists of confidentiality, integrity, and availability.
- Authentication verifies identity.
- Authorization determines access permissions.
- Accounting records activity.
- Firewalls control network traffic according to security rules.
- DMZs can isolate public-facing services.
- Symmetric encryption uses one shared secret key.
- Asymmetric encryption uses public and private keys.
- Hashing is primarily used for integrity and verification.
- DoS attacks attempt to make services unavailable.
- DDoS attacks use multiple sources.
- MitM attacks target communication between parties.
- Sniffing involves capturing network traffic.
- Spoofing involves falsifying an identity or source.
- Defense in depth uses multiple security controls.

---

## Practice

- What are the three components of the CIA Triad?
- What is the difference between authentication and authorization?
- What does AAA stand for?
- What is the purpose of a firewall?
- What is the purpose of a DMZ?
- Explain the difference between symmetric and asymmetric encryption.
- What is the difference between a public key and a private key?
- What is hashing used for?
- Explain the difference between hashing and encryption.
- What is a DoS attack?
- What is the difference between DoS and DDoS?
- What is a Man-in-the-Middle attack?
- What is network sniffing?
- What is spoofing?
- Explain the idea of defense in depth.

---

Part of My-Note. Personal technical knowledge base, continuously updated.
