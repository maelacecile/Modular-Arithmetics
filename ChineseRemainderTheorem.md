# Chinese Remainder Theorem Solution

## Overview
This document presents a solution to a modular arithmetic problem using the Chinese Remainder Theorem (CRT). CRT allows us to solve systems of congruences by finding a unique solution modulo the product of the moduli. This technique is widely used in number theory and cryptography.

## Problem Statement
We are given two parts in this exercise:

1. **Part (a):** Find \( x \) such that:
   - \( x \equiv 211 \ (\text{mod} \ 2438) \)
   - \( x \equiv 3304 \ (\text{mod} \ 4247) \)

   The solution \( x \) should be between 0 and \( 2438 \times 4247 \).

2. **Part (b):** Find \( x \) such that:
   - \( x \equiv 211 \ (\text{mod} \ 2438) \)
   - \( x \equiv 3304 \ (\text{mod} \ 4247) \)
   - \( x \equiv 6614 \ (\text{mod} \ 7123) \)

   The solution \( x \) should be between 0 and \( 2438 \times 4247 \times 7123 \).

### Goal
Determine the unique value of \( x \) that satisfies each set of congruences.

## Solution Steps

### Step 1: Calculate Using CRT Formula
To solve using the Chinese Remainder Theorem, we’ll break down each part using Python. We’ll multiply each modulus to create the complete modulus and solve for \( x \) using modular inverses.

### Step 2: Python Code
Here’s the code that demonstrates solving each part:

```python
from sympy import mod_inverse

def crt(a, n):
    """Solve x for x ≡ a[i] (mod n[i]) for each i, using Chinese Remainder Theorem."""
    N = 1
    for ni in n:
        N *= ni  # Product of all moduli

    x = 0
    for ai, ni in zip(a, n):
        Ni = N // ni
        Mi = mod_inverse(Ni, ni)
        x += ai * Ni * Mi

    return x % N

# Part (a) values
a_part_a = [211, 3304]
n_part_a = [2438, 4247]
x_part_a = crt(a_part_a, n_part_a)
print("Solution for Part (a), x:", x_part_a)

# Part (b) values
a_part_b = [211, 3304, 6614]
n_part_b = [2438, 4247, 7123]
x_part_b = crt(a_part_b, n_part_b)
print("Solution for Part (b), x:", x_part_b)
