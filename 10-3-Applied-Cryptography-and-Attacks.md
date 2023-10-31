# 10.3: Applied Cryptography and Attacks

 [Applied Cryptography and Attacks](#applied-cryptography-and-attacks)
  * [Overview](#overview)
  * [Previous class review](#previous-class-review)
    + [ACTIVITY - 02_Cryptography_Refresher](#activity---02-cryptography-refresher)
  * [Applied cryptography](#applied-cryptography)
    + [Digital Forensics](#digital-forensics)
  * [Stegnography - hidden msg in media (image/audio, etc)](#stegnography---hidden-msg-in-media--image-audio--etc-)
    + [DEMO - steghide](#demo---steghide)
    + [ACTIVITY - 04_Steganography](#activity---04-steganography)
  * [SSL cert - authenticate website](#ssl-cert---authenticate-website)
      - [CA authorities](#ca-authorities)
      - [Steps for cert generation](#steps-for-cert-generation)
      - [SSL certs in browser](#ssl-certs-in-browser)
    + [DEMO](#demo)
    + [ACTIVITY - 07_SSL_Certificates](#activity---07-ssl-certificates)
  * [Cryptographic attacks](#cryptographic-attacks)
    + [Types of crypto attacks](#types-of-crypto-attacks)
    + [ACTIVITY - 11_Crypto_Attacks](#activity---11-crypto-attacks)
  * [Rainbow table](#rainbow-table)
  * [Hashcat](#hashcat)
    + [ACTIVITY - 14_Hashcat](#activity---14-hashcat)

<small><i><a href='http://ecotrust-canada.github.io/markdown-toc/'>Table of contents generated with markdown-toc</a></i></small>



## Overview
- Previous class review
- Applied cryptography
- Stegnography - hidden msg in media (image/audio, etc)
- SSL cert - authenticate website
- Cryptographic attacks
- Rainbow table
- Hashcat

## Previous class review
- Symmetric/asymmetric key
- Hashing 
- Digital signature

### ACTIVITY - 02_Cryptography_Refresher

1. Verify that you can see your gpg key by running: gpg --list-keys.
Note: If you can't see your gpg key, reinstall it using gpg --gen-key.
sysadmin@UbuntuDesktop:~$ gpg --list-keys
/home/sysadmin/.gnupg/pubring.kbx
---------------------------------
pub   rsa3072 2020-05-27 [SC] [expires: 2022-05-27]
      FE5AAFF8365F5CD2DB305089DDD05BF1DC3F40C8
uid           [ultimate] sysadmin
sub   rsa3072 2020-05-27 [E] [expires: 2022-05-27]


2. Write a simple message reminding your fellow Hill Valley officers to sign and verify all messages until further notice.
```
$ echo "Great work so far on your investigations! I have reason to believe the Alphabet Bandit has been a long time member of the Hill Valley PD

Sincerely,
Captain Strickland
" >  message1.txt
```

3. Using GPG, clearsign the message with a digital signature, and name your output file with your name, such as: Important_Communication_by_Myname
Observation: its using SHA512 hashing, in base64 

```
$ gpg --output Important_Communication_by_Sara --armor --clear-sign  message1.txt
sysadmin@UbuntuDesktop:~/Downloads/10-3$ cat Important_Communication_by_Sara
-----BEGIN PGP SIGNED MESSAGE-----
Hash: SHA512

- -----BEGIN PGP SIGNED MESSAGE-----
Hash: SHA512

Great work so far on your investigations! I have reason to believe the Alphabet Bandit has been a long time member of the Hill Valley PD

Sincerely,
Captain Strickland
- -----BEGIN PGP SIGNATURE-----

iQGzBAEBCgAdFiEEAgfPYa89hFo0PLzabWrtvoJg5CMFAmGdWZkACgkQbWrtvoJg
5COC1AwAiarzQIFbk7OoHXXytrWCkfS0hBjIJBIYYB5bsGfW4PPBViTUOkVRrMwY
mXFbuigZ/dob9K6whKMyvmAB6YRwYy4D7/399U9PI77NGNnzRXk7P8FcFZgzboHp
qEdiATJZN6KGI1xGGMD9qD6zwdNCA2onuN4hnfwI/LDr08HjtYUjsB64Qr6oLAd+
8vjQ5yqQSzZlZ4ULnIJeEuCs8BSTJtgcRBgjtOLy5hVi00rHNZnupwzEsiGMbHlL
x21Gx0x+5AsL2xOqd1ZGoNZCzE5dfCvyUc/aggfcP+8soiW3l/t4XQ2S2ttiHHGM
yja9XZQwwt4UMRz1xYD/Msoiy3sOblmBkjIoTpkDGclcu/MhXbGP6ag/Awl7Pt/Q
N2t+1P/FiooH8ICbySosCVXWnYD8smmKorrhm/bUyvezMjpVnESsa2NOFji7Xw7e
bZsssu+yRUtWxpOrSB6A1ZKR5mpcCVjEr2tqEfvHX+gh7b79/um9WDWlJmMhu4XH
yxCNB2HJ
=qjl4
- -----END PGP SIGNATURE-----
-----BEGIN PGP SIGNATURE-----

iQGzBAEBCgAdFiEEF7FaUd8xAkZ0YvQWGKFPes7C3SoFAmRm1/4ACgkQGKFPes7C
3SqH0Qv9EAY3fhVWkNDR4GUo8qI8yZ1mgFB5lh9ZFTouxESlP6BAk2BuIaBJhVU9
pG3maJiUo8l3Poke+xAMkUfmzMvn1ZiLFz4HVMGQyzWFkb4A4YsxXnra7POkWX1P
3tjiAVxHhmq2O88uzv3K7lRwixrfblk+Xa1itgWcJi4TxhiJVDJPZgUFAgfn/p7E
MfsxVqKQOiQgYj6JgzClq1JAh6WrOx1JFrOHaU2vl2lznjNFS+UNwKKZ04JcHxQW
7uDBtwxVEIiwprRQrfs3D819S5Q8yiaRYHxxuCrmaM6Au0eIXpzkKQQYSeCih/1T
xYMGAGxnkhs7dYskiXuxkJhRNTuDVddzGG4j4XuxrB5yZAZidJRd5KkqrQvGyyg5
gy34VT6cfAiUlSKZ+GcZKjnueEAwAPOcPh+vs6SAuAaCMg7KxY1u0wCxoTj9BWPd
9cubW2XmP7Sfyxy8XgdVeddyF15+07gZz4CBcDTLb2Yj/mVMthaJ8HB9U6AuncOo
+AdfIpjc
=YCt2
-----END PGP SIGNATURE-----
```

4. Working with the same partner as in the assymetric key activity from last class, send the clearsigned message to the partner.
Note: If this partner isn't available, join another group to exchange exported public keys and clearsigned messages with.


5. Once you receive the clearsigned message from your partner, use GPG to verify the message is authentic.

## Applied cryptography
- used to secure potable devices
-   bitlocker - Windows
-   FileVault - Mac
-   E/MIME pr PGP - for emails
-   SSL for websites (any version other than TLS v1.2, v1.3 are vulnerable)

### Digital Forensics
- Professional investigation of digital evidence from computer or cell phone
- A forensic examiner is a cybersecurity professional who captures and investigates digital evidence from computers, cell phones, and other devices containing digital data
- Evidence is used in private industry and public legal and criminal investigations.

## Stegnography - hidden msg in media (image/audio, etc)
- text hidden in media (file, image, audio, video, etc.)
- no difference b/w original img and img with hidden text
- too much data can result in destroted media
- Tool like steghide - takes img + txt -> generate img with hidden txt
- It uses least significant bit 
- Some other tools kight be used to embed exe, or shell cmd 
- ML tools might help in identifying media with hidden msg

### DEMO - steghide
0. explore steghide
man steghide

1. Download an image, e.g family.jpg

2. Make a copy of that image
$ cp family.jpg foo.jpg

3. Create a file with message
$ echo "My secret message" > hidden.txt

4. hide message in image
$ steghide embed -cf foo.jpg -ef hidden.txt
-cf means content file
-ef means embed file

5. Enter a passphease (pwd) while embedding msg
e.g. abc
Note: Visually compare family.jpg and foo.jpg, there is no difference

6. Open image from cmd line
eog *.jpg           will open all jpg files

7.  Extract hidden message
steghide extract -sf foo.jpg
-sf means steged file
Enter passphrase (pwd - entered in step 5) to extract img 

### ACTIVITY - 04_Steganography
- In this activity, you will use steganography tools to determine if images contain any hidden messages

1. Download the image of the car from here onto your virtual machine, then open the file.
2. Run steghide to determine if the image file contains a secret message.
Hint: The password is the brand of the car. If you get stuck, ask your instructor or TA for help.
```
$ steghide extract -sf mydreamcar.jpg 
Enter passphrase: 
wrote extracted data to "list_of_targets.txt".
```

3. If the image contains a secret message, find out what it says.
```
$ cat list_of_targets.txt 
List of Homes to Break into

Doctor Brown House - Done
Mayor Wilson's House - Done
Mrs Peaboday's House - Done
Captain Stricklands house - Next
```
## SSL cert - authenticate website
- http -> port 80 -> unsecure connection
- SSL certificates are small data files that use public key cryptography to secure
- An X.509 certificate is the current standard of SSL certificates for securing online communications.
- connections between the browser and the web server. 

#### CA authorities 
- create and manage certs for sites
- Individual/company has to pay to CA to manage/distribute cert on their behalf
-- GlobalSign
-- Digicert
-- Comodo
-- Symantec
-- godaddy
-- letsencrypt.org - free 3 month certs
- When a user visit a website, its cert will be downloaded in the browser
- self-signed certs - mostly used for internal use - not trust
- SSL certificates validate authenticity using a chain of trust.
- SSL certs - might break in 5-10 years

#### Steps for cert generation
1. Company documents - for CA to validate submitting company, to  prevent scammers from getting a real certificate for a fraudulent website.

2. A unique IP address or range  or Full Qualified Domain Name (FQDN)
- subdomains are separate domain from main domain 
- if a single cert covers all subdomain - CA will charge more

3. A certificate signing request (CSR), a block of encrypted data that is created on the web server where the SSL certificate will eventually be installed.
- pub/pvt key is created while generating CSR
- only public key is sent to CA, to distribute it

#### SSL certs in browser
- Browsers have a pre-established list of trusted CAs, called a root store.
? Root certificate authorities are a list of CAs trusted by your browser. They’re at the top of the trust chain and are typically not the organizations that issue SSL certificates.
? Intermediate certificate authorities usually issue certificates and report up to a root certificate authority.

### DEMO 
- Open VM -> Firefox  -> preference -> privacy & security -> certificates
- 4 tabs
1. Certificates
2. Servers - list of all the sites visited 
3. Authorities - CA issued certs
4. 
```
badssl.com - explore different cert status 
```
```
www.google.com
- secure - green lock
    |_ click on lock to view cert 
        |_ secure connection
            |_ more information
                |_ View certificate

CN - my organization which I allow
Serial # - unique for each cert
Period of validity - mostly 90 days (3 months)
SHA256 - used for signature
Certificate hierarchy
```

```
stupidmachines.io
- connection is not secure
more information -> no cert tab, becasue there is no certificate
```

### ACTIVITY - 07_SSL_Certificates

1. Access the website that was sent to several Hill Valley officers.
hillvalleypd.org vs. hillvalleypd.com.

2. Click on the purple icons on each page to view the SSL certificate information.
Note: Clicking the purple house on each page will take you back to the homepage.

3. Answer the following questions:
- What is the root certificate for this website?
No Verification Certificate Authority

- What is the intermediate certificate for this website?
Alphabet Bandit Certificate Authority

- Why is the browser giving a warning about the certificate?
it is a self-signed certificate, and can't be trusted

4. Provide a summary to your captain about your findings and recommend what should be communicated to all the Hill Valley PD staff.
- hillvalleypd.org is using self-signed certificate, tht is why this site can't be trusted
- notify the secops dept about the suspicious email, and donot open any link in the email

## Cryptographic attacks
### Types of crypto attacks
1. Statistical attack
    |_ exploits weakness in algo
    |_ try to determine if the “random” values produced are actually predictable. 
    |_ heat coming from CPU
    |_ Lavalamp image - pick color from a random pixel 

2. brute force
    |_ attackers use many passwords or user and password combinations until one eventually works. 
    |_ To mitigate 
        |_ Limit number of login attempts
        |_ increase wait time with every wrong attempt 

3. Birthday attacks exploit the probability that two separate plaintexts that use the same hash algorithm will produce the Same ciphertext. (Also known as collision and hashing collision.)
    |_ probability of having same bday in a room (50% for 23, 99.9% for 70)!
    |_ Mitigate: 
        |_ Stronger hashing algorithms limit the possibilities of hashing collision. 
4. Frequency analysis is a method for cracking substitution algorithms. 
    |_ An attacker can note the most frequently used letters in the\ ciphertext and substitute them with the most frequently used letters in the English language (e, t, o, a). After inferring the ciphertext, the plaintext can be cracked.
    |_ Mitigate:
       using more advanced encryption algorithms. 

5.  replay attacks
    |_ attacker intercepts an encrypted message and replays it to the receiving party to get access.
    |_ e.g.  An attacker can obtain an encrypted signal from a garage door opener. The attacker can replay the encrypted signal at a later time to open the garage.
    |_ Mitigate:
        |_ set expiration time for the encrypted data, so it can’t be replayed at a later date.

6. Attacker has sample plain and cipher text -> try to guess algo
    |_ e.g. analyze common phrases

             h  e  l  l  0          g  o  o  d  b  y  e
            08 05 12 12 15          07 15 15 04 02 25 05
    |_ Mitigate: 
        |_ Use advanced encryption
        |_ limitted access to ciphertext and associated plaintext. 

7. Attacker knows algo + cipher text -> try to guess plain text
e.g. transposition
```
Plain       boy         red         hot
Cipher      oby         erd         oht
```

### ACTIVITY - 11_Crypto_Attacks

In this activity, you will use cryptographic methods to crack a cipher and reveal a plaintext password.

1. Enter any plaintext into the Password Encrypter and determine the algorithm being used for encryption. 
Note: To run the password encrypter, run: python3 encrypter.py.
Hint: Try multiple plaintext passwords to help determine the algorithm.
```
$ python3 encrypter.py 
What is your Password? abcdef
Your Password is: abcdef
Your Encrypted Password is: tuvwxy
t -> a

$ python3 encrypter.py 
What is your Password? hello world
Your Password is: hello world
Your Encrypted Password is: axeehphkew
h -> o
p -> w

sysadmin@UbuntuDesktop:~/Downloads$ python3 encrypter.py 
What is your Password? topsecret
Your Password is: topsecret
Your Encrypted Password is: mhilxvkxm
m -> t

$ python3 encrypter.py 
What is your Password? hijack
Your Password is: hijack
Your Encrypted Password is: abctvd

b -> i
c -> j

$ python3 encrypter.py 
What is your Password? goodbye
Your Password is: goodbye
Your Encrypted Password is: zhhwurx
z -> g

```

2. Once the algorithm has been determined for encryption, apply this method in reverse to determine Tannen's plaintext password from his encrypted password,
```
cbzhptmm.
c -> j
b -> i
z -> g
h -> o
p -> w
t -> a 
m -> t
jigowatt

```
3. Apply this password on Tannen's login website to confirm that the password is correct. Look for any hard evidence that suggests Detective Tannen is the Alphabet Bandit. To test Tannen's Login password, run: python3 password.py.
```
$ python3 password.py 
Hi Mr Tannen,  What is your password (lowercase only) ? jigowatt
Hello Detective Tannen, the last file you accessed is: topsecret.txt
```

## Rainbow table
- uses precomputed hashes with the associated plaintext passwords.
- search for matching hash, and returns plain txt associated with it
- Some rainbow tables are extremely large.
- They can take up a lot of storage space and CPU to use effectively

- Only hash - without salt
    |_ easy to predict
    |_ if mulitple user have same pwd, then same hash
- It is important to add salt, it is almost impossible to predict pwd
- Salt is a random alpha numeric value
- /etc/shadow file also store salt value as clear text

## Hashcat
- alt: crackstation.net
- Command line tool
- uses wordlists dict, rainbow tables, and brute force - to automate pwd cracking
- ideal for gpu 

### DEMO - Hashcat
This walkthrough will demonstrate the steps necessary to determine the root user’s plaintext password with Hashcat.
```
$ cd /usr/share         rockyou.txt

```


### ACTIVITY - 14_Hashcat

1. Use Hashcat to determine the plaintext value of the hash found on Detective Tannen's computer.
Note: The hash found on Detective Tannen's computer is f31663d6c912b0b1ced885a6c6bbab7c.
Hint: The hashing algorithm was created in 1992 by Ronald Rivest.

```
https://crackstation.net/
pwd: 	ilovelorraine
md5
```

2. With the plaintext password, open the encrypted file with the command unzip secret.zip and confirm whether it contains the evidence needed to lock up the Alphabet Bandit.

```
$ unzip secret.zip 
Archive:  secret.zip
[secret.zip] secret password: 
  inflating: secret                  

~/Downloads$ ls
google-chrome-stable_current_amd64.deb  secret  secret.zip

~/Downloads$ cat secret
CONGRATULATIONS TO THE CYBER SLEUTH THAT FINDS THIS MESSAGE!!


    My Confession

     I, Detective Tannen, am confessing that I am the Alphabet Bandit! 

     I am the one solely responsible for all of the Hill Valley Break-ins.

     Since I wasn't promoted to Captain, I have been determined to cause havoc to the Hill Valley community and tie up the Hill Valley Resources.

     Unfortunately, since you have found this message, I will assume that I will be prosecuted and the break-ins will cease.

    Sincerely,
     Detective Tannen
```