# HMAC Authentication and Verification

## Group
Group D

## Experiment ID
EXP04

## Navigation Title
HMAC Authentication and Verification

## Short Description
Generate and verify HMAC values using a secret key and analyze the effect of modifying the message or key in a virtual cryptography laboratory.

## Folder
/experiments/hmac/

## Entry File
index.html

## Expected Navigation Link
/experiments/hmac/

## Required Libraries
None

## Input
Plaintext message string, secret cryptographic key string, received HMAC digest for verification, and tampered message/key variants for avalanche analysis.

## Output
Cryptographic HMAC-SHA-256 digest in 64-character hexadecimal format, authenticity verification verdict (Match / Tampered), Hamming distance bit difference, and avalanche percentage.

## Theory Summary
HMAC (Hash-based Message Authentication Code) is a keyed-hash authentication mechanism formally specified in RFC 2104 and NIST FIPS PUB 198-1. It provides data integrity and authenticity by combining a shared secret key with an iterated cryptographic hash function such as SHA-256. Unlike naive concatenation H(Key || Message), which is vulnerable to length-extension attacks in Merkle-Damgard hash designs, HMAC uses a nested two-pass construction: HMAC(K, m) = H((K' XOR opad) || H((K' XOR ipad) || m)). In this formula, K' is the secret key padded or hashed to the hash block size B (64 bytes for SHA-256), ipad is the inner padding byte 0x36 repeated B times, and opad is the outer padding byte 0x5C repeated B times. Changing a single bit in the message or key flips approximately 50% of the output bits due to the avalanche effect. HMAC is strictly a one-way message authentication code and cannot be decrypted.
