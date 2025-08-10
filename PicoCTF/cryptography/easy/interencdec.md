# interencdec 

## Challenge Description 

<img width="659" height="839" alt="Screenshot 2025-08-10 103502" src="https://github.com/user-attachments/assets/d2afdeaf-0091-47e5-9e0b-db9fc7f3e158" />

## Solution and Analysis 

We are given a file to be downloaded, which can be done by the **wget** command as shown 

```bash
└─$ wget https://artifacts.picoctf.net/c_titan/1/enc_flag
```

To view the content of the flag simply use the **cat** command 

```bash
└─$ cat enc_flag   
YidkM0JxZGtwQlRYdHFhR3g2YUhsZmF6TnFlVGwzWVROclgyeG9OakJzTURCcGZRPT0nCg==                                                                            
```

It seems like the flag is encoded using base 64, to decode this we can use online tools one such is https://gchq.github.io/CyberChef/

<img width="1858" height="687" alt="image" src="https://github.com/user-attachments/assets/f956e70e-9ce5-4cee-9547-a203bba991d2" />

The decoded text is also in the form of base64 but remove the ' and the letter b as well or else it wont decode correctly 

<img width="1534" height="726" alt="image" src="https://github.com/user-attachments/assets/4668fb8a-6a1d-4e1f-9f99-486a2ce4d377" />

The resulting text seems to be encrypted using caesar cipher, to decrypt it we can use online tools, one such is https://www.dcode.fr/caesar-cipher

<img width="1019" height="313" alt="image" src="https://github.com/user-attachments/assets/dbcd451b-0c8e-4599-841c-95d46edb5113" />

Submit the flag to complete the challenge!
