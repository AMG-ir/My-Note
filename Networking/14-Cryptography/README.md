Cryptography

Cryptography is the practice of protecting information by transforming data so that it can be securely stored or transmitted.

Cryptography is widely used in network security to protect confidentiality, integrity, authentication, and trust between systems.

1. Cryptography Overview

Cryptography provides mechanisms for protecting data against unauthorized access and modification.

The main concepts covered in this section are:

· Encryption
· Decryption
· Symmetric encryption
· Asymmetric encryption
· Public keys
· Private keys
· Hashing
· Digital signatures

---

2. Encryption

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

Basic Concepts

Term Description
Plaintext Original readable data
Ciphertext Encrypted data
Encryption Converting plaintext into ciphertext
Decryption Converting ciphertext back into plaintext
Key Value used by a cryptographic algorithm

---

3. Symmetric Encryption

Symmetric encryption uses the same secret key for encryption and decryption.

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

Both sides must have access to the same secret key.

Characteristics

· Uses one shared secret key
· The same key is used for encryption and decryption
· Generally efficient for protecting large amounts of data
· The secret key must be protected

Basic Example

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

4. Asymmetric Encryption

Asymmetric encryption uses a pair of related keys:

· Public key
· Private key

The public key can be shared, while the private key must be kept secret.

```text
Public Key  --> Can be shared
Private Key --> Must remain secret
```

Basic Concept

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

Characteristics

· Uses two related keys
· Public key can be distributed
· Private key must be protected
· Useful for secure communication and identity-related functions
· Generally more computationally expensive than symmetric encryption

---

5. Public and Private Keys

A public/private key pair is used in asymmetric cryptography.

Public Key

The public key can be distributed to other systems.

It can be used for operations that are designed to be performed with the public key.

Private Key

The private key must remain secret.

Anyone who has access to a private key may be able to perform operations associated with that key.

Comparison

Key Visibility Purpose
Public Key Can be shared Public-side cryptographic operations
Private Key Must remain secret Private-side cryptographic operations

---

6. Hashing

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

Hashing is different from encryption because a cryptographic hash is designed as a one-way function.

A hash is commonly used to verify whether data has changed.

Example

```text
Data
  |
  v
Hash Function
  |
  v
Hash Value
```

If the input changes, the resulting hash should also change.

---

7. Hashing vs Encryption

Hashing and encryption serve different purposes.

Feature Hashing Encryption
Main purpose Data integrity Data confidentiality
Output Hash/digest Ciphertext
Designed to be reversed No Yes, with the required key
Uses keys Not necessarily Yes
Original data recovery Not the purpose Possible through decryption

---

8. Digital Signatures

A digital signature is a cryptographic mechanism used to provide authenticity and integrity.

It can help a recipient verify:

· Who signed the data
· Whether the data was modified
· Whether the signature matches the associated data

Digital signatures use asymmetric cryptography and hashing.

Basic Concept

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

9. Cryptography and Security Goals

Cryptographic mechanisms can support several security goals.

Confidentiality

Protecting information from unauthorized access.

Encryption is commonly used to provide confidentiality.

Integrity

Ensuring that data has not been modified without authorization.

Hashing and digital signatures can help provide integrity verification.

Authentication

Verifying the identity of a user, system, or sender.

Asymmetric cryptography and digital signatures can be used as part of authentication systems.

Non-Repudiation

Providing evidence that a particular entity performed an action, such as signing data.

Digital signatures can support non-repudiation.

---

10. Symmetric vs Asymmetric Cryptography

Feature Symmetric Asymmetric
Number of keys One shared key Public/private key pair
Key distribution More difficult Public key can be shared
Performance Generally faster Generally slower
Large amounts of data Well suited Less efficient
Main concept Shared secret Key pair

---

11. Practical Uses of Cryptography

Cryptography is used in many areas of networking and information security.

Examples include:

· Protecting network communications
· Protecting stored information
· Verifying data integrity
· Authentication
· Secure exchange of information
· Digital signatures
· Secure web communication

---

12. Key Security Principles

Cryptographic security depends not only on the algorithm but also on protecting the keys.

Important principles include:

· Keep private keys secret
· Protect shared secret keys
· Do not expose sensitive keys unnecessarily
· Use appropriate cryptographic mechanisms for the required security goal
· Verify cryptographic information before trusting it

---

13. Cryptography Concepts Comparison

Concept Main Purpose
Symmetric Encryption Confidentiality using a shared secret
Asymmetric Encryption Cryptography using a public/private key pair
Public Key Public part of an asymmetric key pair
Private Key Secret part of an asymmetric key pair
Hashing Integrity verification
Digital Signature Authenticity and integrity verification
Encryption Protecting data confidentiality

---

Key Takeaways

· Cryptography is an important part of network security.
· Encryption protects data confidentiality.
· Symmetric encryption uses a shared secret key.
· Asymmetric encryption uses public and private keys.
· Public keys can be shared, while private keys must remain secret.
· Hashing is mainly used for integrity-related purposes.
· Hashing and encryption are different concepts.
· Digital signatures can provide authenticity and integrity.
· Cryptographic keys must be properly protected.

---

Practice

1. Explain the difference between encryption and hashing.
2. Explain symmetric encryption.
3. Explain asymmetric encryption.
4. What is the difference between a public key and a private key?
5. Why should a private key remain secret?
6. Explain the purpose of a digital signature.
7. Compare symmetric and asymmetric cryptography.
8. Explain how cryptography can provide confidentiality and integrity.
