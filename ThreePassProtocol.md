# Three-Pass Protocol Solution

## Overview
This file documents the solution to a problem involving Shamir's Three-Pass Protocol, a public-key message exchange system. In this protocol, Alice and Bob use modular arithmetic to securely exchange a message without needing a shared secret key. The protocol relies on Fermat’s Little Theorem and modular inverses.

## Problem Statement
Alice and Bob want to exchange a message securely. Using Shamir's Three-Pass Protocol, they send the following sequence of messages:
- **A->B:** 28815377349986238948
- **B->A:** 32022638409929718780
- **A->B:** 14438564975518228697

Parameters given:
- **Prime \( p \)** = 91246234312872996521
- **Modular product \( (a.b) \) mod (p-1)** = 52989123124449843069

### Goal
Determine the original message \( m \) that Alice sent to Bob, using modular inverses and the known values.

## Solution Steps

### Step 1: Setup Algebraic Expressions
   - Let \( m \) represent Alice’s original message.
   - Alice first sends \( m^a \mod p \) to Bob.
   - Bob then responds with \( (m^a)^b \mod p = m^{ab} \mod p \).
   - Finally, Alice responds by sending \( (m^{ab})^{a^{-1}} \mod p = m^b \mod p \) back to Bob.

### Step 2: Use Modular Inverses
   - Since we know the product \( a.b \mod (p-1) \), we can calculate the modular inverse of \( a \) and \( b \) to find \( m \) by working backward.
   - Compute the modular inverse of \( a \) with respect to \( p-1 \), then apply it to retrieve \( m \).

### Step 3: Python Code
The code below demonstrates how to find \( m \) given the values from the problem.

```python
from sympy import mod_inverse

# Given values
p = 91246234312872996521
ab_mod = 52989123124449843069
msg_part3 = 14438564975518228697  # Alice's final response to Bob

# Calculate the inverse of (a * b) mod (p-1)
inverse_ab = mod_inverse(ab_mod, p-1)

# Determine the original message 'm'
m = pow(msg_part3, inverse_ab, p)
print("The original message, m:", m)
