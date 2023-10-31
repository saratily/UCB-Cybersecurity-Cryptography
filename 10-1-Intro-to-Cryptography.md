# Introduction to Cryptography

- [Introduction to Cryptography](#introduction-to-cryptography)
  * [Overview](#overview)
- [Cryptography](#cryptography)
  * [The History of Cryptography](#the-history-of-cryptography)
  * [The Caesar Cipher](#the-caesar-cipher)
  * [The Enigma Machine](#the-enigma-machine)
    + [Key Creation](#key-creation)
    + [Encryption](#encryption)
    + [Decryption](#decryption)
    + [Cracking the Enigma Machine](#cracking-the-enigma-machine)
    + [ACTIVITY - 03_Caesar_Cipher_Code_Names](#activity---03-caesar-cipher-code-names)
  * [Introduction to Character Encoding](#introduction-to-character-encoding)
    + [Character Encoding](#character-encoding)
    + [ASCII Encoding](#ascii-encoding)
    + [ACTIVITY - 06_Decoding](#activity---06-decoding)
      - [1. Hex to ASCII](#1-hex-to-ascii)
      - [2. Binary to ASCII](#2-binary-to-ascii)
      - [3. HEX to ASCII](#3-hex-to-ascii)
      - [4. DECIMAL to ASCII](#4-decimal-to-ascii)
  * [Goals of Cryptography - Pain model](#goals-of-cryptography---pain-model)
  * [Introduction to Cryptography Ciphers](#introduction-to-cryptography-ciphers)
    + [DEMO Transposition cipher](#demo-transposition-cipher)
    + [ACTIVITY - 10_Ciphers](#activity---10-ciphers)
  * [Modern Cryptography](#modern-cryptography)
    + [Key](#key)
    + [DEMO - Encryption Strength](#demo---encryption-strength)
    + [ACTIVITY - 14_encryption_strength](#activity---14-encryption-strength)
  * [Symmetric Key Algorithms](#symmetric-key-algorithms)
  * [Security Tradeoffs](#security-tradeoffs)
  * [Finding the Balance](#finding-the-balance)
  * [DES - Data Encryption Standard](#des---data-encryption-standard)
  * [AES - Advanced Encryption Standard](#aes---advanced-encryption-standard)
  * [OpenSSL](#openssl)
    + [DEMO - OpenSSL](#demo---openssl)
    + [ACTIVITY - 17_openSSL](#activity---17-openssl)

<small><i><a href='http://ecotrust-canada.github.io/markdown-toc/'>Table of contents generated with markdown-toc</a></i></small>



## Overview

- Use basic transcription and substitution ciphers and keys to encrypt simple messages.
- Understand how encryption supports secure communication through the PAIN framework.
- Differentiate between encoding and encrypting.
- Calculate the strength and efficiency of various encryption levels.
- Use symmetric encryption tool OpenSSL to confidentially transmit secure messages. 

# Cryptography

https://en.wikipedia.org/wiki/Cryptography

- A primary method for keeping information secure
- Cryptography is the art and science of keeping information secure through the use of mathematical concepts and techniques.

## The History of Cryptography

https://en.wikipedia.org/wiki/Caesar_cipher

- While cryptography seems like a modern concept, cryptographic techniques were actually in use in early human civilizations.
- These early civilizations engaged in battles, politics, and fights for supremacy.
- Individuals needed to find methods to communicate securely and keep these communications hidden from enemies.

## The Caesar Cipher

In an effort to communicate with his military, the Roman general developed a cipher to hide his communication.

The goal of the Caesar cipher is not only to prevent unauthorized parties from reading the communication, but to also allow authorized parties, such as Caesar’s military, to receive and understand the hidden message.

They shall never crack my code!


| Plain Text | Encrypted ciphertext |
|:---|:---|
| Launch an attack at sunrise. | Odxqfk dq dwwdfn dw vxqulvh |


|Encrypted ciphertext | Plain Text |
|:---|:---|
| Odxqfk dq dwwdfn dw vxqulvh | Launch an attack at sunrise. |

The Caesar cipher works by shifting letters a set number of positions (the key) from the original letter.

```
A B C D E F G H I J K L M N O P Q R S T U V W X Y Z.
 \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \
  C D E F G H I J K L M N O P Q R S T U V W X Y Z A B
```

## The Enigma Machine

- As technology advanced, applied cryptography became more complex and harder to crack.
- After the end of World War I, a German engineer named Arthur Scherbius developed an advanced encryption tool known as the Enigma machine.
- The machine scrambles the 26 letters of alphabet, allowing for billions of ways to encrypt a message

### Key Creation

Settings were configured by the user.
● The key was created when the sender plugged wires into specific slots and arranged the roto settings.
● The exact settings were then used by the recipient for decryption.

### Encryption

To encrypt, the sender entered the plaintext message on the machine’s keyboard one letter at a time.

● After each letter was pressed on the keyboard, another letter lit up on the machine’s lampboard.
● The illuminated letters were documented, creating the ciphertext.
● The ciphertext was transmitted to the recipient.

### Decryption

The secret key combination was provided to the recipient in advance.

● The recipient used the key to configure their machine with the exact settings used for encryption.
● Ciphertext letters were entered one at a time on the keyboard, showing the original plaintext in the lampboard.
● The illuminated letters were documented one at a time,
converting the ciphertext back to plaintext.

### Cracking the Enigma Machine

During the height of World War II, English mathematician and computer scientist Alan Turing developed a method to exploit the weaknesses of the Enigmamachine’s design.
● Known as the Bombe, Turing’s machine helped decrypt the most complex versions of the Enigma cipher.
● Considered one of the most important victories of the Allied forces during the war, Turing’s machine was able to prevent many attacks by decrypting secret messages sent by the Germans.

### ACTIVITY - 03_Caesar_Cipher_Code_Names

you will play the role of security analysts working for the Hill Valley Police Department. You have been assigned to a top secret task force to find the Alphabet Bandit. You must create a code name, encrypt it, and send it to your partner. 

Hello World
Khoor Zruog


## Introduction to Character Encoding

- Encoding is used to transform some data, so it can be used by a different type of system 
- Encoding technique is usually known and data can be encoded and decoded publically by anyone
- The purpose of encoding is NOT to keep information secret, as compare to encryption, which is used to keep information from being accessed by unauthorized user.


### Character Encoding

- Most encryption of digital communication takes place at the level of binary data.
- Readable text is first converted to binary before applying encryption

There are many encoding schemes available. We’ll review a few common ones:

1. Binary - Binary data can be more efficiently stored and represented by encoding with the hexadecimal number system.

2. ASCII - used to represent computer-stored characters in a human-readable format

3. Hex - uses 16 symbols to represent the base values (0-9-A-F)

4. Octal - applies a principle similar to hex, but uses digits 0 through 7

```text
Binary to Text Conversion
browserling.com/tools/binary-to-text

Character Encoding for Numbers
rapidtables.com/convert/number/index.html
```

| Binary | Decimal | Hex | Octal |
|:---|:---|:---|:---|
| 00000000 | 0 | 0 | 0 |
| 00001010 | 10| A | 12 |
| 00000011 | 3 | 3 | 3 |
| 11111110 | 254| FE | 376 |

### ASCII Encoding

The representation of every upper- and lowercase letter of the English alphabet, as well as common punctuation marks and graphic and mathematical symbols, as a number between zero and 255

ASCII is used to represent computer-stored characters in a human-readable format.

https://www.asciitable.com/

| | |  
|:---|:---|
| 0-9 | 48 - 57 |
| A-Z | 65 - 90 |
| a-z | 97 - 172 |
| 0 - 127 | standard ASCII |
| 128 - 255 | extended ASCII |


### ACTIVITY - 06_Decoding

```text
48 61 20 48 61 20 48 61 21 20 59 6f 75 20 63 61 6e 20 6e 65 76 65 72 20 63 61 74 63 68 20 74 68 65 20 41 6c 70 68 61 62 65 74 20 42 61 6e 64 69 74 21 20 53 65 65 20 69 66 20 79 6f 75 20 63 61 6e 20 66 6f 6c 6c 6f 77 20 6d 65 20 68 65 72 65 3a 20 30 31 31 30 31 30 30 30 20 30 31 31 31 30 31 30 30 20 30 31 31 31 30 31 30 30 20 30 31 31 31 30 30 30 30 20 30 30 31 31 31 30 31 30 20 30 30 31 30 31 31 31 31 20 30 30 31 30 31 31 31 31 20 30 31 31 31 30 31 31 31 20 30 31 31 31 30 31 31 31 20 30 31 31 31 30 31 31 31 20 30 30 31 30 31 31 31 30 20 30 31 31 31 30 30 30 30 20 30 31 31 30 30 30 30 31 20 30 31 31 30 30 31 31 31 20 30 31 31 30 30 31 30 31 20 30 31 31 30 31 31 31 31 20 30 31 31 31 30 30 31 30 20 30 31 31 30 30 30 30 31 20 30 31 31 30 31 31 30 31 20 30 31 31 30 30 30 30 31 20 30 30 31 30 31 31 31 30 20 30 31 31 30 30 30 31 31 20 30 31 31 30 31 31 31 31 20 30 31 31 30 31 31 30 31 20 30 30 31 30 31 31 31 31 20 30 30 31 31 31 31 31 31 20 30 31 31 31 30 30 30 30 20 30 30 31 31 31 31 30 31 20 30 31 31 30 30 30 30 31 20 30 31 31 30 30 30 31 30 20 30 31 31 31 30 31 30 31 20 30 31 31 31 30 30 31 30 20 30 31 31 30 30 31 31 31 20 30 31 31 30 31 31 30 30 20 30 31 31 30 30 30 30 31 20 30 31 31 31 30 30 31 30 
```

#### 1. Hex to ASCII

```text
Ha Ha Ha! You can never catch the Alphabet Bandit! See if you can follow me here: 01101000 01110100 01110100 01110000 00111010 00101111 00101111 01110111 01110111 01110111 00101110 01110000 01100001 01100111 01100101 01101111 01110010 01100001 01101101 01100001 00101110 01100011 01101111 01101101 00101111 00111111 01110000 00111101 01100001 01100010 01110101 01110010 01100111 01101100 01100001 01110010
```

#### 2. Binary to ASCII

```text
http://www.pageorama.com/?p=aburglar

Clue1
The Mayor is just the beginning of my Reign, My next target will be:  68 74 74 70 3a 2f 2f 77 77 77 2e 70 61 67 65 6f 72 61 6d 61 2e 63 6f 6d 2f 3f 70 3d 63 6c 75 65 32 
```

#### 3. HEX to ASCII

```text
http://www.pageorama.com/?p=clue2
Impressive work solving my puzzles, my next target will be: 
68 111 99 116 111 114 32 66 114 111 119 110 39 115 32 72 111 117 115 101
```

#### 4. DECIMAL to ASCII

```text
Doctor Brown's House
```

## Goals of Cryptography - Pain model

P - Privacy (confidentiality) - keeps data secure from unauthorized parties. (encrypt email or data to maintain privacy)
A - Authentication is used to confirm the identities of the sender and receiver of data. (intruder impersuade user and send email)
I - Integrity ensures a message isn’t altered between when it’s sent and when it’s received (intercept email and change the content)
N - Non-repudiation prevents the original sender from denying they were the sender. (send in-appropriate msg)

## Introduction to Cryptography Ciphers

Algorithms are mathematical instructions that ciphers use for encryption.

Stream ciphers -  apply their algorithm one bit (character) at a time.
Block ciphers - apply their algorithm to chunks of characters
Transposition Ciphers - a block cipher -  rearranges the letters in each block

### DEMO Transposition cipher

- One prominent block cipher is the transposition cipher, which breaks an input message into equal-sized blocks and rearranges the letters of each block.

1. Break the message into blocks of three characters.
2. Replace the first, second, and third character of each block with the third, first, and second character.
3. Combine rearranged text.

Example:

```text
1 2 3
3 1 2

H E L L O !
L H E ! L O
```

### ACTIVITY - 10_Ciphers

you’ll continue to play the role of security analysts working for the Hill Valley Police Department. Your task is to use a found key to decrypt the most recent message left by the Alphabet Bandit. 

```text
u Yocanen vecar tcthh e phAlab Betant,di Mney xtar Tgeist  Cvialnsou Hse
Mapping:
1 -> 3
2 -> 4
3 -> 1
4 -> 2
5 -> 5
6 -> 6

Divide into baches of size 6, the use above map to replace
u Yoca
You ca

nen ve
n neve

car tc
r catc

thh e 
h the 

phAlab 
Alphab

 Betan
et Ban

t,di M
dit, M

ney xt
y next

ar Tge
 Targe

ist  C
t is C

vialns
alvins

ou Hse
 House

You can never catch the Alphabet Bandit, My next Target is Calvins House
```

## Modern Cryptography

For modern cryptography, key space is defined by the number of binary bits used in the key, known as bit size

- As technology improved, so did methods for cracking ciphers.
- Modern cryptography needed more complex algorithms and longer cryptographic keys

### Key 

Each algorithm has a possible range of numbers that can be used as a key, known as a key space.

For example:
If a password could only be one numerical digits, the possible values are from 0-9, i.e. key space is 10

| bit size | key space | value | 
| ---|---|---|
|1 bit | 2 ^ 1  = 2| 0, 1 |
|2 bit | 2 ^ 2  = 4| 00, 01, 10, 11 |
|3 bit | 2 ^ 3  = 8| 000, 001, 010, 011, 100, 101, 110, 111 |
|4 bit | 2 ^ 4  = 16| 0000, 0001, 0010, 0011, ..... |

### DEMO - Encryption Strength 

(10-Bit and 30-Bit)

- Key space for all alphabet
26 ^ 8 -> not enough for computers

- caps + lower +  numbers
(26+26+10) ^ 8 = 62^8 key space


### ACTIVITY - 14_encryption_strength

you’ll continue to play the role of security analysts working for the Hill Valley Police Department.
In this activity, you will compare several email security vendors and choose the most cost-effective one for protecting future emails.

Hint:
64 bit can be crack in 1 second
32 Million seconds in a year ~ 2^6 * 2^10 * 2^10  = 2^26 [ it will take 26 bit to crack in a year]

1. Twin Pines Email offers 84-bit encryption for $10,000 per month.
84-64= 20, which is less than 26, key will be cracked inless than a year

2. Marvin's Secure Email offers 96-bit encryption for $40,000 per month.
96-64= 32 which is more than 26, it will take longer than a year to crack

3. Milton's Steel Emails offers 103-bit encryption for $100,000 per month.

## Symmetric Key Algorithms

Modern symmetric key algorithms are secure and fast.

If larger bit size means stronger encryption, why don’t we just use a million-bit key?

## Security Tradeoffs

| | | |
|--|--|---|
| It takes time and computational resources to encrypt and decrypt larger keys. | OR | Is the encryption strength worth the time to use the key? |
| Do we want an incredibly strong cipher that’s hard to compute and difficult to decrypt? | OR | DO we prefer average security that’s faster? |

## Finding the Balance

Symmetric key algorithms use a single, shared key to encrypt and decrypt a message. This shared key needs to remain private. If exposed, the message can be decrypted by anyone.

Some widely known symmetric key algorithms include:
● Data Encryption Standard (DES)
● Triple DES (3DES)
● Advanced Encryption Standard (AES) 

## DES - Data Encryption Standard

DES is a 56-bit algorithm published by the United States government in 1977.
● Flaws were found in DES and additional security was added to create Triple 3DES.
● However, the security community banded together to develop a newer, more secure symmetric encryption algorithm.

## AES - Advanced Encryption Standard 

https://en.wikipedia.org/wiki/Advanced_Encryption_Standard
https://nvlpubs.nist.gov/nistpubs/FIPS/NIST.FIPS.197-upd1.pdf

- In 1997, the National Institute of Standards and Technology (NIST) announced they were seeking a replacement for DES.
- NIST opened a contest for cryptographers to submit algorithms.
- In the first round, 15 submissions were collected.
- The community attempted to break them all.
- In the second round, the five most promising algorithms were subjected to extensive cryptanalysis by the community.
- Eventually the Rijndael cipher was determined to be the strongest. After it was refined and standardized, it became the (AES)


## OpenSSL

https://en.wikipedia.org/wiki/OpenSSL

OpenSSL can generate a random key and initialization vector (IV). With the key and IV, OpenSSL can encrypt and decrypt a message with simple terminal commands.



### DEMO - OpenSSL

OpenSSL is a free command-line tool used for symmetric encryption and decryption.

Creating the key and IV:
```
openssl enc -pbkdf2 -nosalt -aes-256-cbc -k mypassword -P > key_and_IV
```

Encrypting:
```
openssl enc -pbkdf2 -nosalt -aes-256-cbc -in plainmessage.txt -out plainmessage.txt.enc -base64 -K 89E01536AC207279409D4DE1E5253E01F4A1769E696DB0D6062CA9B8F56767C8 -iv EE99333010B23C01E6364E035E97275C


enc -> encrpytion
-pbkdf2 -> key derivative
-aes-256-cbc -> cipher
-in <file> -> input plain text as file
-out <file> -> output encrypetd text as file
-base64 -> use base64 encoding
-K <value> -> key
-iv <value> -> intial vector value - reandom generated string
```

Decrypting:
```
openssl enc -pbkdf2 -nosalt -aes-256-cbc -in plainmessage.txt.enc -d -base64 -K 89E01536AC207279409D4DE1E5253E01F4A1769E696DB0D6062CA9B8F56767C8 -iv EE99333010B23C01E6364E035E97275C
```

### ACTIVITY - 17_openSSL

you’ll continue to play the role of security analysts working for the Hill Valley Police Department.
You must use OpenSSL to decrypt a message from the police captain. 

1. Download encrypted file
```
$ wget https://gist.githubusercontent.com/jmmeacham/d71fa8a987ea7d12e7be46dadc7f5986/raw/1ff3d2b04827a11ccd9b78eb14f5552e0d39b89d/communication.txt.enc
```

2. Download key and iv
```
$ https://gist.githubusercontent.com/jmmeacham/d894fcde2f5ed5613fe49fee433a6bbc/raw/809ea931822ac3ed30e93d864bf251f7c106166e/key-iv

$ cat key-iv
Key: key=346B3EFB4B899E8205C4B35E91F5A4605A54F89730AE65CA2C43AB464E76CA99
IV: iv =759D1B9BF335985F55E3E9940E751B67
```

3. Use OpenSSL with the key and IV provided to decrypt the message. Use the following options when decrypting:
-pbkdf2
-nosalt
-aes-256-cbc
-base64

```
$ openssl enc -pbkdf2 -nosalt -aes-256-cbc -in communication.txt.enc -d -base64 -K 346B3EFB4B899E8205C4B35E91F5A4605A54F89730AE65CA2C43AB464E76CA99 -iv 759D1B9BF335985F55E3E9940E751B67
From: Captain Strickland

Great Job Cracking all the Alphabet's coded messages so far, but we need to act faster.

I need you and your partner to meet me at Lou's Cafe tomorrow at noon.
I have some additional information to share about the Alphabet Bandit

I need you to do the following things:

1) Write a message called "meetingplace.txt" for your partner, letting them know about the secret meeting tomorrow 
2) In the message dont use your real names!
3) Create a new Key and IV with Open SSL
4) Use Open SSL with that Key and IV to encrypt the message
5) Dont send the message until we give you the green light
```
