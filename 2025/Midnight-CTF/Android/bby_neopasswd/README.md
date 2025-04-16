# bby_neopasswd

## Context

In this challenge, we are provided with an Android APK file. The goal is to reverse-engineer the application to retrieve the flag.


## Objective

Analyze the APK file and extract the flag hidden within its code.

---

# Solve

### Step 1: Decompile the APK
Using **JADX**, we decompiled the APK to analyze its source code. In the decompiled files, we found a suspicious class named `NotificationsFragment.java`.

### Step 2: Analyze the Code
In the `NotificationsFragment.java` file, we discovered the following method:

```java
private byte[] encryptNotification(byte[] toEncrypt) {
    byte[] encrypted = new byte[toEncrypt.length];
    for (int i = 0; i < encrypted.length; i++) {
        encrypted[i] = (byte) (toEncrypt[i] ^ 66);
    }
    return encrypted;
}
```

This method performs a simple XOR operation with the key `66` to encrypt or decrypt data. Additionally, we found a byte array `bArr` that appears to be the encrypted flag:

```java
byte[] bArr = {15, 1, 22, 4, 57, 115, 54, 119, 29, 17, 55, 18, 113, 48, 29, 113, 35, 49, 59, 29, 54, 114, 29, 4, 115, 44, 38, 29, 17, 113, 33, 48, 39, 54, 119, 63};
```

### Step 3: Write a Python Script to Decrypt
To decrypt the flag, we wrote a Python script that applies the XOR operation with the key `66` to each byte in the array:

```python
bArr = [
    15, 1, 22, 4, 57, 115, 54, 119, 29, 17, 55, 18,
    113, 48, 29, 113, 35, 49, 59, 29, 54, 114, 29, 4,
    115, 44, 38, 29, 17, 113, 33, 48, 39, 54, 119, 63
]

key = 66

decrypted = ''.join(chr(b ^ key) for b in bArr)

print("Decrypted Text:\n", decrypted)
```

## Flag

```
MCTF{1t5_SuP3r_3asy_t0_F1nd_S3cret5}
```

---
