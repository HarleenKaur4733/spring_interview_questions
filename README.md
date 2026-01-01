# 📌 Java & Spring Interview Questions

---

## 1. What is Reflection in Java? Why is it runtime? How does DI use it?

**Reflection in Java** is a **runtime mechanism** that allows inspection and modification of classes, methods, and fields dynamically — even without knowing them at compile time.

Frameworks like Spring use reflection for **Dependency Injection**, reading annotations, creating objects, and invoking methods dynamically (without `new` keyword), making the application loosely coupled and configurable.

---

## 2. Difference between form-bases auth and basic auth?
**Form Authentication:**
User logs in using an HTML login form and server creates a session. Good for web apps.


**Basic Authentication:**
Username and password are sent in every request via headers (key:value). Suitable for APIs but less secure.

---

## 3. Flow of JWT Tokkens?
1. Client log in with username and password
2. **Authentication Server** generate token and return to client
3. Client request to access user resources and send tokken in Authorization Header.
4. **Resource Server** then ivokes endpoints of **Authentication Server** to validate various part of tokken.
5. Autheticate User and send response to client

 ---


 ### 🔐 How JWT Signature is Created (Simple Steps)

1. Convert Header to Base64
2. Convert Payload to Base64
3. Concatenate → `headerBase64 + "." + payloadBase64`
4. Use secret key + algorithm to generate signature:

 ---

 ## 🔐 JWT Signing Methods Summary

JWTs are digitally signed so the server can verify their authenticity and detect tampering.

There are **two ways to sign a JWT**:

---

### 1. **HMAC (Symmetric Signing)**  
🔑 Uses **one shared secret key**.

- Same key is used to **sign** the token and **verify** it.
- Simple, fast, recommended for **single-server apps**.
- Anyone with the key can both create and validate tokens.

**Analogy:**  
One house key → lock & unlock the same door.

---

### 2. **RSA (Asymmetric Signing)**  
🔑 Uses **two keys — Private + Public**.

- **Private key** → Sign token  
- **Public key** → Verify token  
- Recommended for **microservices / distributed systems**.
- Public key can be shared safely for validation.

**Analogy:**  
You sign a document with your unique signature (private key).  
Anyone can verify it, but only you can sign (public key verification).

---

### Quick Comparison

| Feature | HMAC (Symmetric) | RSA (Asymmetric) |
|---|---|---|
| Keys Used | 1 secret key | Public + Private key |
| Sign + Verify | Same key | Private signs, Public verifies |
| Speed | Faster | Slightly slower |
| Best For | Single server | Distributed systems |
| Security Level | Good | Higher |

---

### Why signing matters?

- Ensures JWT is **authentic**
- Prevents **tampering**
- No need to store session → JWT is **stateless**
- Makes token trusted for future requests

---

**In one line:**  
> HMAC = one key for both signing & verifying.  
> RSA = two keys (private signs, public verifies).
