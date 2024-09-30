# Solving with Chinese Remainder Theorem (CRT)

I solved the problem using the Chinese Remainder Theorem (CRT) to combine the three ciphertexts under different moduli. After combining, I computed the integer cube root (since `e = 3`) to reveal the original message.

## Code Snippet

Below is the essential Python snippet that demonstrates the solution:

```python
from sympy.ntheory.modular import solve_congruence

congruences = [(ct1, n1), (ct2, n2), (ct3, n3)]
c, _ = solve_congruence(*congruences)

# Finding the plaintext by computing the cube root of c
p = int(round(c ** (1/3)))

Decrypted Plaintext
The resulting decrypted plaintext is:
42800643192345849658832356723113079698799922547523584
This concludes the successful decryption process.
Decipher: b'recr{H4s4d_is_t0_g00d}'
