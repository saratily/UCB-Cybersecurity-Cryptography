# UCB-Cybersecurity-Cryptography

## Key Cryptographic Terms

| Term | Definition |
|--|--|
| Plaintext | Information in human-readable form. |
| Ciphertext | Plaintext message that has been encrypted into an unreadable form. |
| Encryption | The process of converting plaintext to ciphertext.| 
| Decryption | The process of converting ciphertext to plaintext. |
| Cipher | A method of performing encryption or decryption. |
| Key | A parameter specifying how plaintext is converted to ciphertext and vice versa. |
| Caesar cipher | A type of cipher that shifts the letters in the alphabet by a fixed number. |
| Enigma cipher | A type of cipher used by Germany in World War II to encrypt messages. |

## Encoding

Binary to Text Conversion
browserling.com/tools/binary-to-text
Character Encoding for Numbers
rapidtables.com/convert/number/index.html

| Binary | Decimal | Hex | Octal |
|:---|:---|:---|:---|
| 00000000 | 0 | 0 | 0 |
| 00001010 | 10| A | 12 |
| 00000011 | 3 | 3 | 3 |
| 11111110 | 254| FE | 376 |

https://www.asciitable.com/

| | |  
|:---|:---|
| 0-9 | 48 - 57 |
| A-Z | 65 - 90 |
| a-z | 97 - 172 |
| 0 - 127 | standard ASCII |
| 128 - 255 | extended ASCII |

## PAIN model

P - privacy
A - authenticity
I - Integrity
N - Non-repudiation

### Types of cipher:

- Stream cipher
- Block cipher
- Transposition cipher

## Symmetric Key Algorithms

| Term | Definition |
|--|--|
| DES | Data Encryption Standard |
| AES | Advanced Encryption Standard |
| openssl | Initializes the OpenSSL program. |
|| openssl enc -pbkdf2 -nosalt -aes-256-cbc -in meetingplace.txt -out meetingplace.txt.enc -base64 -K AFEF9A1FCF15F01267474A9B7D240C101DD356B8FFC2751077D0AF83A93848E0 -iv A005FF19C4229D4EE586FAF5E685E536|
| enc | Stands for “encryption.” |
| -pbkdf2 | Specifies the encryption key type. |
| -nosalt | Specifies that salting will not be applied. (Salting, which we’ll cover in more depth later, adds a random value.) |
| -aes-256-cbc | Is the name of the cipher used. |
| -k | PASSWORD Creates a key, with the password mypassword. |
| -P > key_and_IV | Prints out the key and IV to a file called key_and_IV. |

## Asymetric encryption and Hashing

GPG
Hashing and data integrity
Digital signature
