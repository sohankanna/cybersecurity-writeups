# picoCTF 2019 (forensics) - So Meta 

## Challenge Description

We have the following challenge:

<img width="923" height="638" alt="Screenshot 2025-08-08 090248" src="https://github.com/user-attachments/assets/fde509c1-d824-4d84-8283-1b00215f699f" />


To download the file we can use the `wget` command as shown:

```bash
https://jupiter.challenges.picoctf.org/static/89b371a46702a31aa9931a2a2b12f8bf/pico_img.png
```


Using the exiftool command which allows us to see the metadata of the file we get the following result
```bash
└─$ exiftool pico_img.png 
ExifTool Version Number         : 13.25
File Name                       : pico_img.png
Directory                       : .
File Size                       : 109 kB
File Modification Date/Time     : 2020:10:27 00:08:23+05:30
File Access Date/Time           : 2025:08:08 09:00:44+05:30
File Inode Change Date/Time     : 2025:08:08 09:00:44+05:30
File Permissions                : -rw-rw-r--
File Type                       : PNG
File Type Extension             : png
MIME Type                       : image/png
Image Width                     : 600
Image Height                    : 600
Bit Depth                       : 8
Color Type                      : RGB
Compression                     : Deflate/Inflate
Filter                          : Adaptive
Interlace                       : Noninterlaced
Software                        : Adobe ImageReady
XMP Toolkit                     : Adobe XMP Core 5.3-c011 66.145661, 2012/02/06-14:56:27
Creator Tool                    : Adobe Photoshop CS6 (Windows)
Instance ID                     : xmp.iid:A5566E73B2B811E8BC7F9A4303DF1F9B
Document ID                     : xmp.did:A5566E74B2B811E8BC7F9A4303DF1F9B
Derived From Instance ID        : xmp.iid:A5566E71B2B811E8BC7F9A4303DF1F9B
Derived From Document ID        : xmp.did:A5566E72B2B811E8BC7F9A4303DF1F9B
Warning                         : [minor] Text/EXIF chunk(s) found after PNG IDAT (may be ignored by some readers)
Artist                          : picoCTF{FLAG_IN_HERE}
Image Size                      : 600x600
Megapixels                      : 0.360
```


## Answer

Submit the flag to complete the challenge!
