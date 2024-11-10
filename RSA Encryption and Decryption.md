# RSA Encryption and Decryption Solution

## Overview
This document provides a solution to an RSA encryption and decryption problem. RSA is a public-key cryptographic system that enables secure communication by using a pair of keys: a public key for encryption and a private key for decryption. This exercise involves setting up RSA keys, encrypting a message, and verifying the decryption.

## Problem Statement
We are given two tasks:

1. **Task 1:** Set up an RSA system for Alice using the primes:
   - \( p = 556069583727568975173209 \)
   - \( q = 8719786159636386081846139 \)

   Calculate:
   - \( n = p \times q \)
   - \( \phi(n) = (p - 1)(q - 1) \)
   - Public key \( (e, n) \) with \( e = 65537 \)
   - Private key \( (d, n) \), where \( d \) is the modular inverse of \( e \mod \phi(n) \)

2. **Task 2:** Use Alice’s public key to encrypt the message \( m = 122333221 \) and verify that decryption with her private key returns the original message.

### Goal
Demonstrate the RSA encryption and decryption process by calculating \( n \), \( \phi(n) \), and the keys, then using them to encrypt and decrypt the message.

## Solution Steps

### Step 1: Calculate \( n \) and \( \phi(n) \)
   - Compute \( n = p \times q \)
   - Compute \( \phi(n) = (p - 1) \times (q - 1) \)

### Step 2: Generate Public and Private Keys
   - Set \( e = 65537 \), a commonly used public exponent.
   - Calculate \( d \) as the modular inverse of \( e \) with respect to \( \phi(n) \) using the Extended Euclidean Algorithm.

### Step 3: Encrypt and Decrypt the Message
   - **Encryption**: Calculate \( c = m^e \mod n \)
   - **Decryption**: Calculate \( m = c^d \mod n \) to retrieve the original message.

### Python Code
The following code demonstrates each step in Python.

```python
from sympy import mod_inverse

# Given values
p = 556069583727568975173209
q = 8719786159636386081846139
e = 65537
m = 122333221

# Step 1: Calculate n and phi(n)
n = p * q
phi_n = (p - 1) * (q - 1)

# Step 2: Find d, the modular inverse of e mod phi(n)
d = mod_inverse(e, phi_n)

# Step 3: Encrypt the message
c = pow(m, e, n)
print("Encrypted message, c:", c)

# Step 4: Decrypt the message
decrypted_m = pow(c, d, n)
print("Decrypted message, m:", decrypted_m)
```

### Output
```python
# Output for RSA Encryption and Decryption

# Values Calculated:
n = 4848807859982422520055363619087557256788012890051
phi(n) = 4848807859982422520055354343231813892832955870704
Private Key (d) = 4019352973151122050513865145649198491570306248865

# Encrypted Message (c)
c = 220922577707289073220281121173254002900191972769

# Decrypted Message (m)
m = 122333221
