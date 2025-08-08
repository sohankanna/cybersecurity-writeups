# picoCTF 2019 (forensics) - extensions

## Challenge Description

We have the following challenge:

<img width="917" height="642" alt="Screenshot 2025-08-08 090600" src="https://github.com/user-attachments/assets/69c4762b-2213-46fe-9310-1114a0324dad" />


To download the file we can use the `wget` command as shown:

```bash
wget https://jupiter.challenges.picoctf.org/static/e7e5d188621ee705ceeb0452525412ef/flag.txt
```

Upon inspecting the downloaded file using the `file` command we get the result:

```bash
└─$ file flag.txt                      
flag.txt: PNG image data, 1697 x 608, 8-bit/color RGB, non-interlaced
```

Since the data inside the file is in PNG format, we just need to change the extension of the originally downloaded file from `.txt` to `.png`. To do so we can use the `mv` command as shown: [5]

```bash
mv flag.txt flag.png
```

This will rename the file from the `.txt` extension to the `.png` extension. After doing this just view the image to get the flag.

## Answer
<img width="766" height="327" alt="Screenshot 2025-08-08 090843" src="https://github.com/user-attachments/assets/86b44457-6c98-4004-9305-f03bdf476456" />


Submit the flag to complete the challenge!
