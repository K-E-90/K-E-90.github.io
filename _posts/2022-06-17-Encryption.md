---
title: Data Encryption Tool
date: 2022-06-17 12:00:00 +0200
categories: [Encryption]
tags: [Encryption,Python]
---

<!-- # An encryption tool for data protection. -->
# Problem Statement

Recently, I required to use a USB flash drive that contained sensitive data. Therefor, it was beneficial to ensure that the stick was encrypted so that no one could read it in case it was lost.

Searching for suitable tools for this task, I found BitLocker. However these tools work only on windows and third-party software is required on other operating systems to acces the encrypted files. Other crossplatform tools also exist, but these require to install their software on the computer.

What I wanted was a tool for data encryption that is cross platform and requires no installation. Since I didn't find a suitable product, I decided to create my own. 

# Approach

I chose to develop this in Python as I find it easy to prototype and due to the large collection of libraries available. I used cryptographic algorithms that were provided by the [crytography](https://pypi.org/project/cryptography/) library.



```python
import cryptography
print('Hello World!')

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

