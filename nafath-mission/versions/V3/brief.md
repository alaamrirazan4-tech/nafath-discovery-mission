Version: NAFATH-V3

Your track: AI

## Overview

Bringing a public-service AI chat assistant into a government mobile app means we have to carefully tie together six core technical areas so everything runs smoothly, securely, and legally. Software engineering handles the structured release cycles and keeps API integrations stable. On the AI side, Retrieval-Augmented Generation (RAG) pulls factual answers straight from verified policy documents to cut down on mistakes. Mobile development and networking work together to secure data in transit across modern networks, while cybersecurity protects the model from prompt manipulation attempts. Finally, data management puts strict privacy safeguards in place for user logs. Altogether, these pieces form a dependable and trusted digital service for the public.

## Software

Under Semantic Versioning 2.0.0, the public API has to increment its MAJOR version whenever we introduce breaking changes that alter request structures or drop existing endpoints, which forces clients to update. The MINOR version goes up when we add backwards-compatible features or new optional parameters. We only bump the PATCH version for backwards-compatible bug fixes or minor code adjustments that leave the public API contract completely intact.

Resource: Semantic Versioning 2.0.0 Specification - https://semver.org/spec/v2.0.0.html

## AI

Retrieval-Augmented Generation (RAG) is an architecture that links a large language model with an external, authoritative knowledge base. Instead of relying purely on internal training memory, the system takes a user query, converts it into embeddings, pulls matching chunks from official databases, and feeds that verified context right into the prompt. This anchors the model in real documents, which heavily reduces hallucinations and incorrect statements.

Resource: Retrieval-Augmented Generation for Knowledge-Intensive NLP Tasks - https://arxiv.org/abs/2005.11401

## Mobile

iOS App Transport Security (ATS) enforces secure connections by requiring apps to use HTTPS with TLS 1.2 or higher, strong ciphers, and valid certificates for all network calls. If the mobile app tries calling a plain HTTP endpoint, ATS blocks the connection instantly at the OS level to stop unencrypted data from leaking out over public networks.

Resource: Apple Developer Documentation - Preventing Unsecure Network Connections - https://developer.apple.com/documentation/security/preventing_unsecure_network_connections

## Networking

IPv6 uses 128-bit hexadecimal addresses, creating a virtually endless pool of unique identifiers to support the explosion of connected mobile devices and IoT gear. IPv4, by contrast, relies on 32-bit addresses and maxes out at around 4.3 billion, leading to severe shortages and clumsy NAT workarounds. IPv6 brings back direct end-to-end connectivity, simplifies routing, and guarantees long-term scalability.

Resource: RFC 8200 - Internet Protocol, Version 6 (IPv6) Specification - https://www.rfc-editor.org/rfc/rfc8200

## Cybersecurity

Prompt injection happens when malicious inputs trick an LLM into running unauthorized commands. Direct injection is when a user manually types bad instructions into the chat box, whereas indirect injection occurs when the assistant pulls untrusted external content—like a poisoned RAG document—that carries hidden adversarial instructions. To mitigate this, we separate user inputs from system prompts using strict delimiters and use input/output guardrails.

Resource: NIST SP 800-218 - Secure Software Development Framework (SSDF) - https://csrc.nist.gov/pubs/sp/800/218/final

## Data

Anonymization completely strips out all identifying pieces from chat logs so that no one can ever trace the data back to an individual. Pseudonymization swaps out direct identifiers with artificial keys while keeping the mapping table locked down separately. Because true anonymized data is irreversibly unidentifiable, it steps completely outside the reach of data protection regulations like GDPR.

Resource: GDPR Article 4 - Definitions - https://gdpr-info.eu/art-4-gdpr/

## Misconception in My Track

A widespread misconception about RAG is that pulling verified documents entirely eliminates wrong answers or hallucinations. In reality, while RAG provides a strong factual anchor, the LLM can still misinterpret what it reads or summarize it awkwardly during generation. Section 4.2 of the seminal RAG paper highlights that although these models are much more accurate than pure parametric models, they are still generative systems that can slip up with subtle errors if generation decoding isn't strictly constrained.

## Open Question

I would verify whether our backend can maintain sub-second response times when scaling the vector store to handle millions of archived government policy documents.
