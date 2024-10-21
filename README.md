# Ex 9-RSA-Encryption-Algorithm
# AIM:
To Implement RSA Encryption Algorithm in C Program.
# ALOGORITHM:
1.Select 2 prime numbers p and q.
2.Calculate n and pi(n).
3.Choose small number e.
4.Calculate d.
5.Perform encryption and decryption and get the outputs correspondingly.

# PROGRAM:
```
#include <stdio.h>
#include <math.h>

// Function to compute greatest common divisor (GCD)
int gcd(int a, int b) {
    int temp;
    while (b != 0) {
        temp = a % b;
        a = b;
        b = temp;
    }
    return a;
}

// Function to compute modular exponentiation
long long mod_pow(long long base, long long exp, long long mod) {
    long long result = 1;
    while (exp > 0) {
        if (exp % 2 == 1)
            result = (result * base) % mod;
        base = (base * base) % mod;
        exp = exp / 2;
    }
    return result;
}

int main() {
    // Two prime numbers (for simplicity, small primes are used)
    int p = 61, q = 53;
    int n = p * q;           // n = p * q
    int phi = (p - 1) * (q - 1);  // Euler's Totient function phi(n)

    // Public key (e) must be such that 1 < e < phi and gcd(e, phi) = 1
    int e = 17;   // A common choice for e
    int d, k = 1; // d is the private key

    // Compute d such that (d * e) % phi = 1
    while ((1 + (k * phi)) % e != 0) {
        k++;
    }
    d = (1 + (k * phi)) / e;

    // Message to be encrypted
    long long message;
    printf("Enter the message to encrypt (as integer): ");
    scanf("%lld", &message);

    // Encrypt the message
    long long encrypted_message = mod_pow(message, e, n);
    printf("Encrypted message: %lld\n", encrypted_message);

    // Decrypt the message
    long long decrypted_message = mod_pow(encrypted_message, d, n);
    printf("Decrypted message: %lld\n", decrypted_message);

    return 0;
}
```
# OUTPUT:
![Screenshot 2024-10-21 102433](https://github.com/user-attachments/assets/b30a3e83-060b-4642-a15a-039ffa52d22d)

# RESULT:
Hence, the simulation of RSA algorithm is successfully done.
  
  
