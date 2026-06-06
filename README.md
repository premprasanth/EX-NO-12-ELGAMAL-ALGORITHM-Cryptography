# EX-NO-12-ELGAMAL-ALGORITHM
## NAME: J.PREM PRASANTH

## REGISTER NUMBER:2305001028

## AIM:
To Implement ELGAMAL ALGORITHM

## ALGORITHM:

1. ElGamal Algorithm is a public-key cryptosystem based on the Diffie-Hellman key exchange and relies on the difficulty of solving the discrete logarithm problem.

2. Initialization:
   - Select a large prime \( p \) and a primitive root \( g \) modulo \( p \) (these are public values).
   - The receiver chooses a private key \( x \) (a random integer), and computes the corresponding public key \( y = g^x \mod p \).

3. Key Generation:
   - The public key is \( (p, g, y) \), and the private key is \( x \).

4. Encryption:
   - The sender picks a random integer \( k \), computes \( c_1 = g^k \mod p \), and \( c_2 = m \times y^k \mod p \), where \( m \) is the message.
   - The ciphertext is the pair \( (c_1, c_2) \).

5. Decryption:
   - The receiver computes \( s = c_1^x \mod p \), and then calculates the plaintext message \( m = c_2 \times s^{-1} \mod p \), where \( s^{-1} \) is the modular inverse of \( s \).

6. Security: The security of the ElGamal algorithm relies on the difficulty of solving the discrete logarithm problem in a large prime field, making it secure for encryption.

## Program:
```
import random

def modinv(a, p):
    return pow(a, -1, p)

def keygen(p, g):
    x = random.randint(2, p - 2)
    y = pow(g, x, p)
    return x, y

def encrypt(p, g, y, m):
    k = random.randint(2, p - 2)
    c1 = pow(g, k, p)
    c2 = (m * pow(y, k, p)) % p
    return c1, c2

def decrypt(p, x, c1, c2):
    s = pow(c1, x, p)
    m = (c2 * modinv(s, p)) % p
    return m


# Example
p = 467  # prime modulus
g = 2    # generator

# Key generation
x, y = keygen(p, g)
print("Private Key:", x)
print("Public Key:", y)

# Encryption
message = 123
c1, c2 = encrypt(p, g, y, message)
print("\nCiphertext: (", c1, ",", c2, ")")

# Decryption
decrypted = decrypt(p, x, c1, c2)
print("Decrypted Message:", decrypted)
```

## Output:
<img width="728" height="359" alt="image" src="https://github.com/user-attachments/assets/f8a456ba-e514-4166-bbd6-95c8ecf06d09" />




## Result:
The program is executed successfully.
