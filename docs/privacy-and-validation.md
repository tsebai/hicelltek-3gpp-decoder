# Privacy and validation

## Processing model

Submitted hexadecimal frames are processed in memory and are not retained by the online decoder. The public workflow is designed for isolated protocol data units, not for uploading private capture archives.

Users remain responsible for removing subscriber identifiers, security material and other sensitive information before sharing a decoded result outside their authorized environment.

This repository intentionally contains no:

- Customer or production payloads
- Private validation corpus
- API keys, credentials or secrets
- Server or deployment configuration
- Proprietary source code or binaries

## Bounded validation result

The published bounded validation scope contains 63,375 cases:

| Expected outcome | Cases |
| --- | ---: |
| Successful decode | 36,904 |
| Safe rejection | 26,471 |
| Total | 63,375 |

Within this bounded scope, the recorded result is zero oracle failures and zero transport failures.

## What the result establishes

The result establishes the expected behaviour on the cited bounded corpus: valid in-scope inputs decode as expected, while designated malformed or unsupported inputs are rejected safely.

## What the result does not establish

It is not a claim that every possible RRC or NAS bit sequence will decode. Results outside the corpus still depend on:

- Correct radio technology and logical-channel metadata
- The appropriate release grammar
- Whether the message is ciphered
- Optional or vendor-specific extensions
- Truncation, padding and capture framing

A decoder output should be treated as one item of technical evidence. Root-cause analysis normally requires correlation with the surrounding procedure and network context.

## Proprietary-engine notice

The decoding engine is proprietary. This repository contains public documentation and examples only. No licence to the engine, its source code, generated ASN.1 artefacts or binaries is granted by this repository.
