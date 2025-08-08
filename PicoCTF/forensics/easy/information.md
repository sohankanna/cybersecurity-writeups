# information

## Challenge Description
<img width="921" height="680" alt="Screenshot 2025-08-08 094638" src="https://github.com/user-attachments/assets/adef4e6d-951c-46a0-99c8-0232a898c35e" />


## Analysis and Solution

The first step in analyzing any file in a forensics challenge is to understand what kind of file it is and to inspect its metadata. We can do so using the `exiftool` command as shown 
```bash
└─$ exiftool cat.jpg                                             
ExifTool Version Number         : 13.25
File Name                       : cat.jpg
Directory                       : .
File Size                       : 878 kB
File Modification Date/Time     : 2021:03:15 23:54:46+05:30
File Access Date/Time           : 2025:08:07 20:44:32+05:30
File Inode Change Date/Time     : 2025:08:07 20:44:24+05:30
File Permissions                : -rw-rw-r--
File Type                       : JPEG
File Type Extension             : jpg
MIME Type                       : image/jpeg
JFIF Version                    : 1.02
Resolution Unit                 : None
X Resolution                    : 1
Y Resolution                    : 1
Current IPTC Digest             : 7a78f3d9cfb1ce42ab5a3aa30573d617
Copyright Notice                : PicoCTF
Application Record Version      : 4
XMP Toolkit                     : Image::ExifTool 10.80
License                         : cGljb0NURnt0aGVfbTN0YWRhdGFfMXNfbW9kaWZpZWR9
Rights                          : PicoCTF
Image Width                     : 2560
Image Height                    : 1598
Encoding Process                : Baseline DCT, Huffman coding
Bits Per Sample                 : 8
Color Components                : 3
Y Cb Cr Sub Sampling            : YCbCr4:2:0 (2 2)
Image Size                      : 2560x1598
Megapixels                      : 4.1

```
We can see that the License isn't right, usually it is in the form of **CC BY (Attribution)** or **CC BY-SA (Attribution-ShareAlike)**. It looks like to be base64 encoded text. We can decode by using the following command
```bash
└─$ echo "cGljb0NURnttM3RhZDR0YV9pc191czNmdWxsfQo=" | base64 --decode
picoCTF{flag}

```
Submit the flag you get in the output of the command to solve the challenge
