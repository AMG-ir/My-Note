# 14 - Cryptography

Cryptography is the practice of protecting information by transforming data so that it can be securely stored or transmitted. It is widely used in network security to protect confidentiality, integrity, authentication, and trust between systems.

## Overview

The main concepts covered in this section:

- Encryption
- Decryption
- Symmetric encryption
- Asymmetric encryption
- Public keys
- Private keys
- Hashing
- Digital signatures

## Contents

- [Encryption](#encryption)
- [Symmetric Encryption](#symmetric-encryption)
- [Asymmetric Encryption](#asymmetric-encryption)
- [Public and Private Keys](#public-and-private-keys)
- [Hashing](#hashing)
- [Hashing vs Encryption](#hashing-vs-encryption)
- [Digital Signatures](#digital-signatures)
- [Cryptography and Security Goals](#cryptography-and-security-goals)
- [Symmetric vs Asymmetric Cryptography](#symmetric-vs-asymmetric-cryptography)
- [Practical Uses of Cryptography](#practical-uses-of-cryptography)
- [Key Security Principles](#key-security-principles)
- [Cryptography Concepts Comparison](#cryptography-concepts-comparison)
- [Key Takeaways](#key-takeaways)
- [Practice](#practice)

---

## Encryption

Encryption transforms readable data, known as plaintext, into an unreadable form called ciphertext.

```text
Plaintext
    |
    v
Encryption
    |
    v
Ciphertext
```

The ciphertext can be converted back into plaintext through decryption when the required key is available.

```text
Ciphertext
    |
    v
Decryption
    |
    v
Plaintext
```

| Term       | Description |
|------------|-------------|
| Plaintext  | Original readable data |
| Ciphertext | Encrypted data |
| Encryption | Converting plaintext into ciphertext |
| Decryption | Converting ciphertext back into plaintext |
| Key        | Value used by a cryptographic algorithm |

---

## Symmetric Encryption

Symmetric encryption uses the same secret key for encryption and decryption. Both sides must have access to the same secret key.

```text
              Secret Key
                  |
                  v
Plaintext --> Encryption --> Ciphertext
                               |
                               v
                          Decryption
                               |
                               v
                           Plaintext
```

**Characteristics**

- Uses one shared secret key
- The same key is used for encryption and decryption
- Generally efficient for protecting large amounts of data
- The secret key must be protected

Basic example:

```text
Sender
  |
  | Plaintext
  v
[Encryption]
  |
  | Shared Secret Key
  v
Ciphertext
  |
  v
Receiver
  |
  | Shared Secret Key
  v
[Decryption]
  |
  v
Plaintext
```

---

## Asymmetric Encryption

Asymmetric encryption uses a pair of related keys: a public key and a private key. The public key can be shared, while the private key must be kept secret.

```text
Public Key  --> Can be shared
Private Key --> Must remain secret
```

Basic concept:

```text
Sender
  |
  | Plaintext
  v
Encryption
  |
  | Receiver's Public Key
  v
Ciphertext
  |
  v
Receiver
  |
  | Receiver's Private Key
  v
Decryption
  |
  v
Plaintext
```

**Characteristics**

- Uses two related keys
- Public key can be distributed
- Private key must be protected
- Useful for secure communication and identity-related functions
- Generally more computationally expensive than symmetric encryption

---

## Public and Private Keys

A public/private key pair is used in asymmetric cryptography.

- **Public key:** can be distributed to other systems and used for operations designed to be performed with the public key.
- **Private key:** must remain secret. Anyone who has access to a private key may be able to perform operations associated with that key.

| Key         | Visibility         | Purpose |
|-------------|--------------------|---------|
| Public Key  | Can be shared      | Public-side cryptographic operations |
| Private Key | Must remain secret | Private-side cryptographic operations |

---

## Hashing

Hashing converts input data into a fixed-size value called a hash or digest.

```text
Input Data
    |
    v
Hash Function
    |
    v
Hash Value
```

Hashing is different from encryption because a cryptographic hash is designed as a one-way function. A hash is commonly used to verify whether data has changed. If the input changes, the resulting hash should also change.

---

## Hashing vs Encryption

| Feature                 | Hashing           | Encryption |
|-------------------------|-------------------|------------|
| Main purpose            | Data integrity    | Data confidentiality |
| Output                  | Hash/digest       | Ciphertext |
| Designed to be reversed | No                | Yes, with the required key |
| Uses keys               | Not necessarily   | Yes |
| Original data recovery  | Not the purpose   | Possible through decryption |

---

## Digital Signatures

A digital signature is a cryptographic mechanism used to provide authenticity and integrity. It can help a recipient verify:

- Who signed the data
- Whether the data was modified
- Whether the signature matches the associated data

Digital signatures use asymmetric cryptography and hashing.

```text
Data
  |
  v
Hash
  |
  v
Signature Process
  |
  v
Digital Signature
```

The recipient can use the appropriate public key and the received data to verify the signature.

---

## Cryptography and Security Goals

Cryptographic mechanisms can support several security goals.

| Goal             | Description | Supporting Mechanisms |
|------------------|-------------|-----------------------|
| Confidentiality  | Protecting information from unauthorized access | Encryption |
| Integrity        | Ensuring data has not been modified without authorization | Hashing, digital signatures |
| Authentication   | Verifying the identity of a user, system, or sender | Asymmetric cryptography, digital signatures |
| Non-Repudiation  | Providing evidence that an entity performed an action, such as signing data | Digital signatures |

---

## Symmetric vs Asymmetric Cryptography

| Feature               | Symmetric        | Asymmetric |
|-----------------------|------------------|------------|
| Number of keys        | One shared key   | Public/private key pair |
| Key distribution      | More difficult   | Public key can be shared |
| Performance           | Generally faster | Generally slower |
| Large amounts of data | Well suited      | Less efficient |
| Main concept          | Shared secret    | Key pair |

---

## Practical Uses of Cryptography

Cryptography is used in many areas of networking and information security. Examples include:

- Protecting network communications
- Protecting stored information
- Verifying data integrity
- Authentication
- Secure exchange of information
- Digital signatures
- Secure web communication

---

## Key Security Principles

Cryptographic security depends not only on the algorithm but also on protecting the keys. Important principles include:

- Keep private keys secret.
- Protect shared secret keys.
- Do not expose sensitive keys unnecessarily.
- Use appropriate cryptographic mechanisms for the required security goal.
- Verify cryptographic information before trusting it.

---

## Cryptography Concepts Comparison

| Concept              | Main Purpose |
|----------------------|--------------|
| Symmetric Encryption | Confidentiality using a shared secret |
| Asymmetric Encryption| Cryptography using a public/private key pair |
| Public Key           | Public part of an asymmetric key pair |
| Private Key          | Secret part of an asymmetric key pair |
| Hashing              | Integrity verification |
| Digital Signature    | Authenticity and integrity verification |
| Encryption           | Protecting data confidentiality |

---

## Key Takeaways

- Cryptography is an important part of network security.
- Encryption protects data confidentiality.
- Symmetric encryption uses a shared secret key.
- Asymmetric encryption uses public and private keys.
- Public keys can be shared, while private keys must remain secret.
- Hashing is mainly used for integrity-related purposes.
- Hashing and encryption are different concepts.
- Digital signatures can provide authenticity and integrity.
- Cryptographic keys must be properly protected.

---

## Practice

- Explain the difference between encryption and hashing.
- Explain symmetric encryption.
- Explain asymmetric encryption.
- What is the difference between a public key and a private key?
- Why should a private key remain secret?
- Explain the purpose of a digital signature.
- Compare symmetric and asymmetric cryptography.
- Explain how cryptography can provide confidentiality and integrity.

---

Part of My-Note. Personal technical knowledge base, continuously updated.
