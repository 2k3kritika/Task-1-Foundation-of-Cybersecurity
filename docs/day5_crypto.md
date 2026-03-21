# 🔐 Cryptography Fundamentals for Cybersecurity

[Back to main README](/README.md)

This repository covers core cryptographic concepts including encryption types, hashing, digital certificates, SSL/TLS, and practical usage of OpenSSL.

---

# 🔑 1. Symmetric vs Asymmetric Encryption

Encryption is the process of converting plaintext into unreadable data (ciphertext) to protect information.

---

## 🔹 Symmetric Encryption

Uses the **same key** for encryption and decryption.

### 📌 Key Features:

* Fast and efficient
* Suitable for large data
* Key must be shared securely

### 📊 Example:

```bash id="sym1"
Plaintext → [Key] → Ciphertext → [Same Key] → Plaintext
```

### 🔧 Common Algorithms:

* AES (Advanced Encryption Standard)
* DES (outdated)

---

## 🔹 Asymmetric Encryption

Uses **two keys**:

* Public Key (shared)
* Private Key (secret)

### 📌 Key Features:

* More secure key exchange
* Slower than symmetric encryption

### 📊 Example:

```bash id="asym1"
Encrypt with Public Key → Decrypt with Private Key
```

### 🔧 Common Algorithms:

* RSA
* ECC (Elliptic Curve Cryptography)

---

## ⚖️ Key Difference

| Feature   | Symmetric       | Asymmetric   |
| --------- | --------------- | ------------ |
| Keys Used | One             | Two          |
| Speed     | Fast            | Slower       |
| Security  | Moderate        | High         |
| Use Case  | Data encryption | Key exchange |

---

# 🔍 2. Hashing (MD5, SHA256)

Hashing converts data into a **fixed-length string**.

---

## 🔹 Properties of Hash Functions

* One-way (cannot reverse)
* Fixed output length
* Same input → same hash
* Small change → completely different hash

---

## 🔹 MD5 (Message Digest 5)

* Produces 128-bit hash
* **Not secure** (vulnerable to collisions)

Example:

```bash id="md5"
echo -n "hello" | md5sum
```

---

## 🔹 SHA256

* Produces 256-bit hash
* Much more secure than MD5

Example:

```bash id="sha256"
echo -n "hello" | sha256sum
```

---

## 📌 Use Cases:

* Password storage (with salting)
* File integrity verification
* Digital signatures

---

# 📜 3. Digital Certificates & SSL/TLS

---

## 🔹 Digital Certificates

Used to verify identity of a website or entity.

### Contains:

* Public key
* Domain name
* Certificate Authority (CA)
* Expiry date

---

## 🔹 SSL/TLS (Secure Communication)

Protocols used to secure data over the internet.

---

## 🔄 TLS Handshake (Simplified)

1. Client sends request to server
2. Server sends certificate (public key)
3. Client verifies certificate
4. Client generates session key
5. Secure communication begins

---

## 🔐 Why TLS Uses Both Encryption Types

* Asymmetric → Secure key exchange
* Symmetric → Fast data encryption

---

# 🧪 4. Hands-on: OpenSSL Practice

OpenSSL is a powerful tool for encryption, decryption, and certificate management.

---

## 🔹 Encrypt a File (Symmetric)

```bash id="enc1"
openssl enc -aes-256-cbc -salt -in message.txt -out message.enc
```

---

## 🔹 Decrypt a File

```bash id="dec1"
openssl enc -aes-256-cbc -d -in message.enc -out decrypted.txt
```

---

## 🔹 Generate RSA Key Pair

```bash id="rsa1"
openssl genpkey -algorithm RSA -out private.pem
openssl rsa -pubout -in private.pem -out public.pem
```

---

## 🔹 Encrypt with Public Key

```bash id="enc2"
openssl rsautl -encrypt -inkey public.pem -pubin -in message.txt -out encrypted.txt
```

---

## 🔹 Decrypt with Private Key

```bash id="dec2"
openssl rsautl -decrypt -inkey private.pem -in encrypted.txt -out decrypted.txt
```

---

## 🔹 Generate a Self-Signed Certificate

```bash id="cert1"
openssl req -x509 -newkey rsa:2048 -keyout key.pem -out cert.pem -days 365
```

---

# 🎯 Learning Outcome

After completing this, you should:

* Understand encryption types and their use cases
* Differentiate hashing vs encryption
* Know how SSL/TLS secures communication
* Perform basic encryption/decryption using OpenSSL

---

# ⚠️ Notes

* MD5 is insecure — avoid using it in real applications
* Never share private keys
* Always verify certificates in real-world scenarios
* Cryptography is only as strong as its implementation

---
