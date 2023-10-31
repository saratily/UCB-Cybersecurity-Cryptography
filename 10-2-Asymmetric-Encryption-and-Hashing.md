# Asymetric encryption and Hashing

- [Asymetric encryption and Hashing](#asymetric-encryption-and-hashing)
  * [Overview](#overview)
    + [ACTIVITY - 02_Cryptography_Refresher](#activity---02-cryptography-refresher)
  * [Symmetric VS Asymmetric key management](#symmetric-vs-asymmetric-key-management)
    + [ACTIVITY - 06_Optimizing_w_Asymmetric](#activity---06-optimizing-w-asymmetric)
  * [GPG - GNU Provacy Guard](#gpg---gnu-provacy-guard)
    + [DEMO](#demo)
      - [Julie key setup](#julie-key-setup)
      - [Tim steps to encrypt msg](#tim-steps-to-encrypt-msg)
      - [Julie steps to decrypt the msg](#julie-steps-to-decrypt-the-msg)
    + [ACTIVITY - 09_GPG](#activity---09-gpg)
  * [Hashing and data integrity](#hashing-and-data-integrity)
    + [DEMO - Creating Hashes on the Command Line](#demo---creating-hashes-on-the-command-line)
    + [ACTIVITY - 13_Generating_Hashes](#activity---13-generating-hashes)
  * [Digital signature](#digital-signature)
    + [DEMO -](#demo--)
    + [ACTIVITY - 17_Digital_Signature_Activity](#activity---17-digital-signature-activity)

<small><i><a href='http://ecotrust-canada.github.io/markdown-toc/'>Table of contents generated with markdown-toc</a></i></small>


## Overview

- Calculate required  # of keys for symmetric and asymmetric, based on # of ppl
- GPG - generate keys, and encrypt/decrypt private messages.
- Use hashes to validate the integrity of data.
- Use digital signatures to validate the authenticity of data. (Integrity)

### ACTIVITY - 02_Cryptography_Refresher

1. Choose a partner, preferably the same partner as in the previous class.

```text
$ nano meetingplace.txt

Hi partner, this is alpha. Lets meet tomorrow at 6:00 pm  at Lou's Cafe to discuss the attack plan.
```

2. Write an updated message using your code name, indicating the meeting is now at 6:00 p.m. at Lou's Cafe.

    - Encrypt the message with OpenSSL.
    - Send the encrypted message to your partner with the key and IV.

- Once you received your partner's encrypted message, key, and IV, decrypt it with Open SSL.

```text
$ openssl enc -pbkdf2 -nosalt -aes-256-cbc -k helloworld -P > key_and_IV

$ cat key_and_IV 
key=AFEF9A1FCF15F01267474A9B7D240C101DD356B8FFC2751077D0AF83A93848E0
iv =A005FF19C4229D4EE586FAF5E685E536

$ openssl enc -pbkdf2 -nosalt -aes-256-cbc -in meetingplace.txt -out meetingplace.txt.enc -base64 -K AFEF9A1FCF15F01267474A9B7D240C101DD356B8FFC2751077D0AF83A93848E0 -iv A005FF19C4229D4EE586FAF5E685E536

$ cat meetingplace.txt.enc 
MHOTSYbJ7znITstttIPeRHcVjZPuKrACmvCM29/U4SabGDHwARqxlYpFksXnHVvW
zNo4qJ1p0yfFUofn3JaCT0Na7zirFjwPg/GACAFJhIBLKWlRYPAuy7fjnHZRpzyb
KXorZm1YX9B0kqs2l5BnEw==
```

3. After decrypting your partner's message, answer the following questions:

- What method did you use to transfer the key and IV?
- Is this a secure method for transmitting the key and IV? Why or why not?

## Symmetric VS Asymmetric key management

- Symetric - same key to encryot and decrypt
    |_Disadv: # of keys increase drastically
    |_ e.g. for N employees. # of keys = N(N-1)/2
            for 7 employess. # of keys = 7(7-1)/2 = 42/2 = 21
            for 1000 employees. # of keys = 1000(1000-1)/2 = 499,500

- Asymmetric - pair of public/private key
|_INtroduce by Diffie-Hellman
|_ key can be any alphanumeric string
|_e.g. ssh, DKIM, Digital signature, etc.
|_ Use map to generate keys
|_WORKFLOW: Tim wants to send encrypted msg to Julie (using Julie's public key)
    |_ Julie -> generate pvt/pub key pair
            -> send public key to Tim (via Slack, email)
            -> Tim encrypt msg using Julie public key
            -> Send encrypted msg to Julie
            -> Julie decrypt msg using her pvt key

MD5 - not secure anymore
RSA
    |_today standard
    |_ asymmetric algorithm standard used around the world
    |_ works by employing the complexity of factoring large numbers

### ACTIVITY - 06_Optimizing_w_Asymmetric

For each of the following Hill Valley police divisions, calculate how many asymmetric and symmetric keys will be required for secure communication based on the number of officers.
SWAT team: 10 officers
Canine Unit: 25 officers
Internal Affairs: 45 officers

1. Document how many fewer keys will be required after moving from symmetric to asymmetric cryptography for each division. For example: The SWAT team will need X fewer keys after moving from symmetric to asymmetric cryptography.

```
# of employees      Symmetric       Asymmetric
10                  45              20
25                  300             50
45                  990             90
```

## GPG - GNU Provacy Guard

https://en.wikipedia.org/wiki/GNU_Privacy_Guard

- For generating and Applying public key
- Used to simplify the creation, encryption, and decryption of asymmetric key cryptography.
- Available on many Linux distributions that run symmetric and asymmetric encryption algorithms.

### DEMO

use the bank account scenario with GPG to create a key pair for asymmetric encryption and decryption.

#### Julie key setup

1. Generate public/pvt key pair
gpg --gen-key

2. List all keys
gpg --list-key

3. View - key + garbage - hard to understand
cat ~./gnupg/pubring.kbx

4. Send public key, <key_file>.gpg, export using email
gpg --armor --output <key_file>.gpg --export <email>

5. key_garbage
cat <key_file>.gpg

#### Tim steps to encrypt msg

1. Import Julie public key
gpg --import <key_file>.gpg

2. Create a plain msg file
$ echo "Hi Julie, my bank account number is 12345." > plain.txt

3. Encrypt <plain>.txt, and generate <encrypted>.txt
gpg --armor --output <encrypted>.txt --encrypt --recipient <email> <plain>.txt

4. encrypted version of plain text file
cat <encrypted_file>.txt

#### Julie steps to decrypt the msg

1. cmd to decrypt the encrypted file
gpg --output <decrypt>.txt --decrypt <encrypted_file>.txt


### ACTIVITY - 09_GPG

1. Write an updated message, using your code name, that describes your idea to catch the insider titled secret_idea.txt. For example, an idea might be: Wiretapping all the detective phones.

```
$ nano secret_idea.txt
lets Wiretap all the detective phones to identify Alphabet Bandit insider
```

2. Generate a key pair, export your public key with armor and share it with your partner.

```
$ gpg --gen-key
gpg (GnuPG) 2.2.4; Copyright (C) 2017 Free Software Foundation, Inc.
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.

gpg: keybox '/home/sysadmin/.gnupg/pubring.kbx' created
Note: Use "gpg --full-generate-key" for a full featured key generation dialog.

GnuPG needs to construct a user ID to identify your key.

Real name: Sara 
Name must be at least 5 characters long
Real name: Sara T
Email address: sarat@email.com
You selected this USER-ID:
    "Sara T <sarat@email.com>"

Change (N)ame, (E)mail, or (O)kay/(Q)uit? o
We need to generate a lot of random bytes. It is a good idea to perform
some other action (type on the keyboard, move the mouse, utilize the
disks) during the prime generation; this gives the random number
generator a better chance to gain enough entropy.
We need to generate a lot of random bytes. It is a good idea to perform
some other action (type on the keyboard, move the mouse, utilize the
disks) during the prime generation; this gives the random number
generator a better chance to gain enough entropy.
gpg: /home/sysadmin/.gnupg/trustdb.gpg: trustdb created
gpg: key 18A14F7ACEC2DD2A marked as ultimately trusted
gpg: directory '/home/sysadmin/.gnupg/openpgp-revocs.d' created
gpg: revocation certificate stored as '/home/sysadmin/.gnupg/openpgp-revocs.d/17B15A51DF3102467462F41618A14F7ACEC2DD2A.rev'
public and secret key created and signed.

pub   rsa3072 2023-05-17 [SC] [expires: 2025-05-16]
      17B15A51DF3102467462F41618A14F7ACEC2DD2A
uid                      Sara T <sarat@email.com>
sub   rsa3072 2023-05-17 [E] [expires: 2025-05-16]

sysadmin@UbuntuDesktop:~/Documents/gpg$ gpg --list-key
gpg: checking the trustdb
gpg: marginals needed: 3  completes needed: 1  trust model: pgp
gpg: depth: 0  valid:   1  signed:   0  trust: 0-, 0q, 0n, 0m, 0f, 1u
gpg: next trustdb check due at 2025-05-16
/home/sysadmin/.gnupg/pubring.kbx
---------------------------------
pub   rsa3072 2023-05-17 [SC] [expires: 2025-05-16]
      17B15A51DF3102467462F41618A14F7ACEC2DD2A
uid           [ultimate] Sara T <sarat@email.com>
sub   rsa3072 2023-05-17 [E] [expires: 2025-05-16]

$ gpg --armor --output sara.gpg --export sarat@email.com 
$ ls
sara.gpg  secret_idea.txt
$ cat sara.gpg 
-----BEGIN PGP PUBLIC KEY BLOCK-----

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
gJc+C7PTPMOlIy/qWYu1fA==
=1r1T
-----END PGP PUBLIC KEY BLOCK-----
```

3. Import your partner's public key.

4. Encrypt the message with your partner's public key using GPG, save the encrypted file as [yourname]_secret_idea.txt.enc.

5. Transmit the encrypted message to your partner using Slack.

6. After you receive your partner's encrypted message, decrypt it using your private key.

## Hashing and data integrity

    |_ cryptic method to verify data integrity
    |_ Changes data completely from original data
    |_ diff from encryption
        1. No key 
        2. Irreversable
        3. input size doesn't matter, always generate same length hash
        4. Goal is integrity (encryption is for privacy)
    |_ algorithms
        SHA - SHA1 and SHA2 (SHA-256 and SHA-512)
        MD5 - not secure anymore - MD2, MD4, and MD5
        LM and NTLM - hashes used by Windows.

### DEMO - Creating Hashes on the Command Line

```
$ echo "Hello World" > foo.txt

$ cat fool.txt
Hello World

$ md5sum foo.txt

$ mv foo.txt bar.txt

$ md5sum bar.txt.           change in filename has no impact on hash

sha256sum foo.txt           hexdecimal encoding
```

### ACTIVITY - 13_Generating_Hashes

1. Extract the investigation files provided to you.

- Note that there are directories titled current and backup, each of which contain the investigation report files. It's quite likely that the Alphabet Bandit modified the data in the current files.

2. Use md5sum to generate hashes of all the files into a single file called hashes.

```
cd backup
md5sum * > hashes
cd ..
```

3. Compare the hashes with a single md5sum command to determine which of the files were changed in the current directory.

```
$ mv hashes current
$ cd current
$ md5sum -c hashes 
Investigation_1101: FAILED
Investigation_1108: OK
Investigation_1110: FAILED
Investigation_1112: OK
Investigation_1116: OK
md5sum: WARNING: 2 computed checksums did NOT match
```

4. Use the diff command to figure out what was changed in the modified files.

```
$ cd ..
$ diff backup/Investigation_1101 current/Investigation_1101 
13c13
< Dr Browns Residence was burgalarized, exotic car was taken as well as several containers of Gasoline
---
> Dr Browns Residence was burgalarized, exotic car was taken as well as several containers of Plutonium.
$ diff backup/Investigation_1110 current/Investigation_1110
13c13
< Jennifer Parkers House was burglarized, mostly jewlery was stolen and no damage occured at the house
---
> Jennifer Parkers House was burglarized, mostly jewlery was stolen and significant damage occured at the house


```

## Digital signature

- Validate authenticity of data
- mathematical scheme used to verify the authenticity of digital data.
- STEPS:

1. Tim generate public/private key
2. Tim creates a message
3. sign the msg using pvt key -> done by gpg (msg hash -> encrypt hash -> add to the massage)
4. Send msg to Julie (msg + public key + signature (hidden))
5. Julie validate Tim signature

### DEMO -

- Use all the concepts discuss in this session to generate digital signature

1.a. Tim generate pair of pub/pvt keys

```
$ gpg --gen-key
gpg (GnuPG) 2.2.4; Copyright (C) 2017 Free Software Foundation, Inc.
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.

Note: Use "gpg --full-generate-key" for a full featured key generation dialog.

GnuPG needs to construct a user ID to identify your key.

Real name: Tim Person
Email address: tim@email.com
You selected this USER-ID:
    "Tim Person <tim@email.com>"

Change (N)ame, (E)mail, or (O)kay/(Q)uit? O
We need to generate a lot of random bytes. It is a good idea to perform
some other action (type on the keyboard, move the mouse, utilize the
disks) during the prime generation; this gives the random number
generator a better chance to gain enough entropy.
We need to generate a lot of random bytes. It is a good idea to perform
some other action (type on the keyboard, move the mouse, utilize the
disks) during the prime generation; this gives the random number
generator a better chance to gain enough entropy.
gpg: key B8115E420882344B marked as ultimately trusted
gpg: revocation certificate stored as '/home/sysadmin/.gnupg/openpgp-revocs.d/4878E8588D041C205A6737EFB8115E420882344B.rev'
public and secret key created and signed.

pub   rsa3072 2023-05-18 [SC] [expires: 2025-05-17]
      4878E8588D041C205A6737EFB8115E420882344B
uid                      Tim Person <tim@email.com>
sub   rsa3072 2023-05-18 [E] [expires: 2025-05-17]

$ gpg --list-key
gpg: checking the trustdb
gpg: marginals needed: 3  completes needed: 1  trust model: pgp
gpg: depth: 0  valid:   2  signed:   0  trust: 0-, 0q, 0n, 0m, 0f, 2u
gpg: next trustdb check due at 2025-05-16
/home/sysadmin/.gnupg/pubring.kbx
---------------------------------
pub   rsa3072 2023-05-17 [SC] [expires: 2025-05-16]
      17B15A51DF3102467462F41618A14F7ACEC2DD2A
uid           [ultimate] Sara T <sarat@email.com>
sub   rsa3072 2023-05-17 [E] [expires: 2025-05-16]

pub   rsa3072 2021-11-23 [SC] [expires: 2023-11-23]
      0207CF61AF3D845A343CBCDA6D6AEDBE8260E423
uid           [ unknown] strickland <strickland@hillvalleypd.com>
sub   rsa3072 2021-11-23 [E] [expires: 2023-11-23]

pub   rsa3072 2023-05-18 [SC] [expires: 2025-05-17]
      4878E8588D041C205A6737EFB8115E420882344B
uid           [ultimate] Tim Person <tim@email.com>
sub   rsa3072 2023-05-18 [E] [expires: 2025-05-17]

```

1.b.  Export the public key

```
$ gpg --armor --output key.gpg --export tim@email.com
$
```

2. Create a msg

```
$ echo Transfer $500 to my account 12345 > Tim_mssage.txt
$ cat Tim_mssage.txt 
Transfer 00 to my account 12345
```

3.a. Tim sign the message

```
gpg --output Tim_signature --armor --detach-sig Tim_message.txt
```

3.b. View Tim signature

```
$ cat Tim_signature 
-----BEGIN PGP SIGNATURE-----

iQGzBAABCgAdFiEEF7FaUd8xAkZ0YvQWGKFPes7C3SoFAmRmN0AACgkQGKFPes7C
3SqT0Av+LU5hx/qKK2pEvAmROooTbQyYHOeu3mjklw7uejwnlPga4RICRShPbRKG
l+r93tfXc/liSwlQTLVx8hPdfnVuXSBwGV1sqLXqE1efoCIAQG0toHMxmwjKfjwP
SrvSzDyRbJzny1bt1NL4+iAFwv//zEhEdDL75uINdzIyxZPclResPMzK+23cdLLT
dEmfr4WR8FLPedVFyYOF5HzDW2LvoNa27j4hXrmuXVF/xJKJkI0TzbV4KVrUgyzd
r21YP10xR4+5uu89WpoamK0R68KqtIT2jvtmlCK9GZSrO3boU1owfLom4ysw0ekV
5avJSYcEN+WX8TM/HT5nmZDc6iOPigGDfTFpegCUtMl2IVmX2X+wmuzDnfGXoDqX
jVT0+cphcvPc0QigoVM8exxoHDhTbgwkhNnonIIH8rvf6FO+Dg9fPvQjE+bNVFNd
haam/ZsnCp67K3e3sp3U3K4KA0+6cmqTOXGlbXgP4iSQkSrJpb8MQbFx8kIxv51B
mZ+055CT
=cITZ
-----END PGP SIGNATURE-----

```

5. At Julie's end, verify the message (import and verify shold be 2 different steps)

```
$ gpg --import key.gpg --verify Tim_signature Tim_message.txt
// throws error - do import and verify separately

$ gpg --import key.gpg
gpg: key B8115E420882344B: "Tim Person <tim@email.com>" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1

$ gpg --verify Tim_signature Tim_message.txt
gpg: Signature made Thu 18 May 2023 10:33:36 AM EDT
gpg:                using RSA key 17B15A51DF3102467462F41618A14F7ACEC2DD2A
gpg: Good signature from "Sara T <sarat@email.com>" [ultimate]

// Made some change to file (e.g. add 6 at the end of msg)
- then signature and text will not match
$ nano Tim_mssage.txt 

$ gpg --verify Tim_signature Tim_mssage.txt 
gpg: Signature made Thu 18 May 2023 10:33:36 AM EDT
gpg:                using RSA key 17B15A51DF3102467462F41618A14F7ACEC2DD2A
gpg: BAD signature from "Sara T <sarat@email.com>" [ultimate]

```

### ACTIVITY - 17_Digital_Signature_Activity

1. Extract the messages from Captain Strickland.
Download resources/Stricklands_messages.zip and unzip it

```
$ unzip Stricklands_messages.zip 
Archive:  Stricklands_messages.zip
  inflating: message1.sig            
  inflating: message2.sig            
  inflating: message3.sig
 ```

2. Import Captain Strickland's public key.
Download resources/strickland_publickey.gpg

```
$ gpg --import strickland_publickey.gpg
gpg: key 6D6AEDBE8260E423: "strickland <strickland@hillvalleypd.com>" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
```

3. Use GPG to determine which of the messages are not authentic and thus not from Captain Strickland.

```
$ gpg --verify  message1.sig
gpg: Signature made Tue 23 Nov 2021 04:14:01 PM EST
gpg:                using RSA key 0207CF61AF3D845A343CBCDA6D6AEDBE8260E423
gpg: Good signature from "strickland <strickland@hillvalleypd.com>" [unknown]
gpg: WARNING: This key is not certified with a trusted signature!
gpg:          There is no indication that the signature belongs to the owner.
Primary key fingerprint: 0207 CF61 AF3D 845A 343C  BCDA 6D6A EDBE 8260 E423

$ gpg --verify  message2.sig
gpg: Signature made Tue 23 Nov 2021 04:14:19 PM EST
gpg:                using RSA key 0207CF61AF3D845A343CBCDA6D6AEDBE8260E423
gpg: Good signature from "strickland <strickland@hillvalleypd.com>" [unknown]
gpg: WARNING: This key is not certified with a trusted signature!
gpg:          There is no indication that the signature belongs to the owner.
Primary key fingerprint: 0207 CF61 AF3D 845A 343C  BCDA 6D6A EDBE 8260 E423

$ gpg --verify  message3.sig
gpg: CRC error; 3E8F12 - AF8243
gpg: packet(2) with unknown version 0
gpg: no signature found
gpg: the signature could not be verified.
Please remember that the signature file (.sig or .asc)
should be the first file given on the command line.
```
