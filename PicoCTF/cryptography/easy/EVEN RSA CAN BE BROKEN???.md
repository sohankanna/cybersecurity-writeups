# EVEN RSA CAN BE BROKEN???

## Challenge Description 

<img width="660" height="663" alt="Screenshot 2025-08-10 102447" src="https://github.com/user-attachments/assets/977ee043-1145-4b91-b3cd-bd2ebce4eca5" />

## Solution and Analysis 

So we are given an interface to connect with to get the challenge as shown 

```bash
└─$ nc verbal-sleep.picoctf.net 52407
N: 15670486633893804323762212898637871667941398551553578363563974262544320326343226952124610464821239940822183541368003266183968698469079838930901694272149938
e: 65537
cyphertext: 310102334696548197739612678442676178490285386313271835684795664800269603703092004716398389311274125654000177546456200342351279763176030718474728195357539
```

In RSA encryption, **`e`**, **`n`**, and **`c`** are essential public components used to lock a message.

Think of it like sending a secret message using a public lockbox. 📦

***

#### n (The Modulus): The Lockbox

**`n`** is a very large public number. It acts as the **lockbox** itself. It's created by multiplying two secret, large prime numbers. Everyone can see and use this lockbox, but only the intended recipient has the key to open it.

***

#### e (The Public Exponent): The "Lock" Button

**`e`** is another public number that acts as the **"lock" button** on the box. Anyone can take a message, place it inside the lockbox (`n`), and press this button (`e`) to securely lock it. A common choice for `e` is 65537 because it makes the locking process fast.

***

#### c (The Ciphertext): The Locked Message

**`c`** is the **scrambled, unreadable message** after it has been locked. This is what's actually sent over the internet. It's calculated by taking the original message (`m`) and applying the public values in a formula:

$$c = m^e \pmod{n}$$

To anyone else, `c` looks like random numbers. Only the person with the corresponding private key can unlock the box and reveal the original message `m`. 

To decrypt this message we can use online tools, one such is https://www.dcode.fr/rsa-cipher
<img width="878" height="804" alt="Screenshot 2025-08-10 102822" src="https://github.com/user-attachments/assets/13f8b7c8-a131-4f5c-b6ce-d00cfdeafa38" />

