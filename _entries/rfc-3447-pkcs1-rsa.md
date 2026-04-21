---
layout: entry
title: "PKCS #1: RSA Cryptography Specifications Version 2.1"
author: "Jakob Jonsson, Burt Kaliski"
year: 2003
format: paper
topic: security
source: https://www.rfc-editor.org/rfc/rfc3447
---

## Why I read this

Read it to understand the basics of modern cryptography — RSA is the canonical public-key algorithm, and this RFC is where its encryption, signature, and padding schemes are actually specified.

## Key ideas

- RSA lets two parties communicate securely over an insecure channel, with no shared secret established beforehand.
- Security rests on the computational hardness of inverting specific mathematical operations — concretely, factoring very large integers.
- Two main uses, mirror images of each other: **encryption/decryption** (for confidentiality) and **digital signatures/verification** (for authenticity and integrity).
- Minimal flows:
  ```
  Encryption:  sender → K+_receiver(m)       → channel → K-_receiver(·) = m
  Signature:   sender → (m, K-_sender(m))    → channel → K+_sender(sig) == m
  ```
  Encryption uses the *receiver's* keypair; signing uses the *sender's*. Anyone can encrypt or verify (public key); only the owner can decrypt or sign (private key).
- Combined, encryption and signatures give you three properties:
  - **Confidentiality** — nobody else can read the message.
  - **Authentication** — the receiver knows who sent it.
  - **Integrity** — the message wasn't altered in transit.

## Personal takeaways

Had to do a [presentation](https://docs.google.com/presentation/d/1un3coP-t7x1zLXI-QUvZJy18Tm7AEIuRE9k7Z1VIsUk/edit?usp=sharing) on the topic at university. Reading the RFC is what made the handshake chapter from [*Distributed Systems: Concepts and Design*]({{ '/entries/coulouris-distributed-systems/' | relative_url }}) finally click.
