# What Lies Within 

## Challenge Description 
<img width="934" height="473" alt="image" src="https://github.com/user-attachments/assets/770d9c1c-32ba-40fd-8c33-5e32d14be4f0" />

## Solution and Analysis 

This is a classic steganography challenge. First download the image into your machine. To get the flag I used the **zsteg** tool which is execellent for solving steganographic related problems. Just run the following command to get the flag 

```bash
zsteg buildings.png   
```

#### Output

```bash
zsteg buildings.png                                  
b1,r,lsb,xy         .. text: "^5>R5YZrG"
b1,rgb,lsb,xy       .. text: "picoCTF{FLAG_IN_HERE}"
b1,abgr,msb,xy      .. file: OpenPGP Secret Key
b2,b,lsb,xy         .. text: "XuH}p#8Iy="
b3,abgr,msb,xy      .. text: "t@Wp-_tH_v\r"
b4,r,lsb,xy         .. text: "fdD\"\"\"\" "
b4,r,msb,xy         .. text: "%Q#gpSv0c05"
b4,g,lsb,xy         .. text: "fDfffDD\"\""
b4,g,msb,xy         .. text: "f\"fff\"\"DD"
b4,b,lsb,xy         .. text: "\"$BDDDDf"
b4,b,msb,xy         .. text: "wwBDDDfUU53w"
b4,rgb,msb,xy       .. text: "dUcv%F#A`"
b4,bgr,msb,xy       .. text: " V\"c7Ga4"
b4,abgr,msb,xy      .. text: "gOC_$_@o"
```
