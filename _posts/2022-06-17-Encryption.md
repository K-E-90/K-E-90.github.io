---
title: Data Encryption Tool
date: 2022-06-17 12:00:00 +0200
categories: [Encryption]
tags: [Encryption,Python]
---

<!-- # An encryption tool for data protection. -->
## Problem Statement

Recently, I required to use a USB flash drive that contained sensitive data. Therefor, it was beneficial to ensure that the stick was encrypted so that no one could read it in case it was lost.

Searching for suitable tools for this task, I found BitLocker. However this tool works only on windows and third-party software is required on other operating systems to acces the encrypted files. Other crossplatform tools also exist, but these require you to install their software on every computer.

What I wanted was a tool for data encryption that is cross platform and requires no installation. Since I didn't find a suitable product, I decided to create my own. 

## Approach

I chose to develop this in Python as I find it easy to prototype and due to the large collection of libraries available. Cryptography is a complex topic, so using cryptographic algorithms provided by the [crytography](https://pypi.org/project/cryptography/) library saves a lot of time.


The program uses this library to generate a key by hashing the password with a randomly generated salt. This key will be saved on your computer locally for recovery in case you forget your password.

The salt is saved on the USB stick with the encrypted files and the executables to encrypt and decrypt the folder.



```python
import cryptography
import EncryptoLib as EL


def main():
    [succes, salt] = EL.get_salt()
    if not succes: #No salt found for encryption
        return
    password = input("Enter password: ")
    [succes, key] = EL.get_key(salt,password)
    if not succes: #Incorrect password provided
        return
    files = EL.get_decrypted_files()
    EL.encrypt_files(files,key)

if __name__ == "__main__":
    main()
    
```

## Result



