# de-encrypt
# AES Encryption and Decryption with Node.js `crypto` Module

This repository demonstrates the use of Node.js's built-in `crypto` module for encrypting and decrypting messages using the AES-256-CBC algorithm.

## Table of Contents

- [Overview](#overview)
- [Requirements](#requirements)
- [Usage](#usage)
- [Code Explanation](#code-explanation)
- [License](#license)

---

## Overview

This script showcases the following:
- Hashing a password using the `createHash` method.
- Generating random bytes for cryptographic purposes.
- Encrypting and decrypting messages using AES-256-CBC with `createCipheriv` and `createDecipheriv`.

---

## Requirements

- Node.js installed on your system (v12 or higher).

---

## Usage

1. Clone the repository:
   ```bash
   git clone https://github.com/your-username/aes-crypto-example.git
   cd aes-crypto-example
2. Run the script:

```bash
  node index.js
```
3. The output will show:

Encrypted message (in hexadecimal format).
Decrypted message (the original plaintext).

## **Code Explanation**
**Hashing Example (Commented Out)**
javascript
```Javascript
const hash = crypto.createHash('sha256');
hash.update('password123');
console.log(hash.digest('hex'));
```
This code hashes the string `password123` using SHA-256 and outputs the hash in hexadecimal format.

**Generate Random Bytes**
```Javascript
Copy code
crypto.randomBytes(16, (err, buf) => {
  if (err) throw err;
  console.log(buf.toString('hex'));
});
```
This generates a random 16-byte string, often used for cryptographic purposes such as initialization vectors (IVs).

## **Encryption and Decryption with AES-256-CBC**
``` Javascript
const algorithm = 'aes-256-cbc';
const key = crypto.randomBytes(32);
const iv = crypto.randomBytes(16);

const cipher = crypto.createCipheriv(algorithm, key, iv);
let encrypted = cipher.update('hello, this is a secret message', 'utf8', 'hex');
encrypted += cipher.final('hex');
console.log(encrypted);

const decipher = crypto.createDecipheriv(algorithm, key, iv);
let decrypted = decipher.update(encrypted, 'hex', 'utf8');
decrypted += decipher.final('utf8');
console.log(decrypted);
```
Encryption: The createCipheriv method uses the AES-256-CBC algorithm, a random 32-byte key, and a 16-byte IV to encrypt a message.
Decryption: The createDecipheriv method decrypts the encrypted message using the same key and IV.


**License**
This project is licensed under the MIT License. See the LICENSE file for details.
```
de-encrypt/blob/core/LICENSE
```
