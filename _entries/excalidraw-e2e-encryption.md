---
layout: entry
title: "End-to-End Encryption in the Browser"
author: "Excalidraw"
year: 2020
format: blog
topic: security
source: https://blog.excalidraw.com/end-to-end-encryption/
---

## Why I read this

A look at Excalidraw's architecture. Worth reading if you're curious how a client-side-heavy app handles end-to-end encryption without a trusted backend.

## Key ideas

- Client-side-only E2EE: data is encrypted in the browser before it touches the server, so the server stores opaque blobs and has no ability to read user content.
- The decryption key lives in the URL fragment (the part after `#`), which browsers do not send to the server — so sharing a link shares the key with collaborators but never with Excalidraw's backend.
- A symmetric scheme (AES-GCM) encrypts the scene; the key is encoded as a JWK and placed in the URL fragment directly.

## Personal takeaways

Inspired me to build [tinycodeshare.app](https://www.tinycodeshare.app/), applying the same URL-fragment E2EE pattern to code sharing.
