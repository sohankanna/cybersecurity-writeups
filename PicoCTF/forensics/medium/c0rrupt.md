# c0rrupt 

## Challenge Description 

<img width="923" height="456" alt="image" src="https://github.com/user-attachments/assets/87c3bf8f-4593-4268-936d-cbe5d239b790" />

## Solution and Analysis 


In this challenge, we were given a mysterious file named mystery that was unreadable by any standard program. Our goal was to perform digital forensics to repair the file, reveal its hidden contents, and capture the flag.
Part 1: Initial Investigation - What is this file?

The first step in any forensics challenge is to identify what you're working with.

I started by using the file command, which is a great utility for identifying file types based on their "magic numbers" (the first few bytes of the file).
code Bash

```bash 
file mystery
```
  
The output was simply mystery: data. This tells us that the file command couldn't recognize the file's signature. It's just a generic bag of bytes to it. This is a strong indicator of file header corruption.

Next, I decided to look at the raw bytes of the file in a hex editor format. The xxd command is perfect for a quick peek.
```bash
xxd mystery | more
```
  

This command shows the first few lines of the file in hexadecimal.
<img width="662" height="474" alt="image" src="https://github.com/user-attachments/assets/023dd10b-1863-4e90-9e34-ff9e4ae0c605" />


Looking at the output, two things immediately stood out:

    The first byte was 89, which is very common in PNG files.

    The ASCII column showed bits and pieces that looked like they could be part of a PNG header, like sRGB and gAMA.

This gave me a strong hypothesis: We are dealing with a PNG file with a corrupted header.

To fix a PNG, we need to know what a correct PNG looks like. A PNG file is made up of two main parts:

    A fixed 8-byte signature: This is always the same for every PNG file in the world. It acts as an unmistakable identifier.

        Correct Hex: 89 50 4E 47 0D 0A 1A 0A

        Correct ASCII: .PNG....

    A series of "chunks": Each chunk contains a piece of information about the image. The most important one is the first chunk, called IHDR (Image Header), which stores the image's width, height, and color details.

Each chunk has its own structure:

    4 bytes: Length of the chunk's data.

    4 bytes: The chunk's name (like IHDR, pHYs, IDAT).

    Data: The actual data for the chunk.

    4 bytes: A CRC checksum to verify the data isn't corrupted.

With this knowledge, I could begin the repair.

First, I made a backup copy to work on. You should never edit the original evidence!


    
```bash
cp mystery mystery_fixed.png
```
  

Then, I opened the file in a terminal-based hex editor called hexedit.

```bash
hexedit mystery_fixed.png
```
  

My first task was to fix the main 8-byte signature and the name of the first chunk.

    The Problem: The file started with 89 65 4e 34 0d 0a b0 aa and the first chunk was mislabeled as C"DR (43 22 44 52).

    The Goal: Change these to the correct values for a PNG and its IHDR chunk.

I made the following changes on the very first line of the hex editor:

    65 -> 50 (The 'P' in PNG)

    34 -> 47 (The 'G' in PNG)

    b0 -> 1a

    aa -> 0a

    43 -> 49 (The 'I' in IHDR)

    22 -> 48 (The 'H' in IHDR)
  


After fixing the main header, I used a tool called pngcheck to see if there were other errors. This tool is specifically designed to validate the structure of PNG files.

```bash    
pngcheck mystery_fixed.png
```
  

It immediately reported a CRC error in chunk pHYs. This told me the data inside the pHYs (Physical Pixel Dimensions) chunk was corrupted.

Looking at the hex for that chunk (on the line starting 00000040), I saw this:
... 73 aa 00 16 25 00 00 16 25 ...

The pHYs chunk stores the X and Y pixels per meter. The value for Y was 00 00 16 25. The value for X was aa 00 16 25. It's highly probable that the aa byte was the corruption and should have been 00.

    The Problem: A corrupted byte aa in the pHYs chunk data.

    The Goal: Change the corrupted byte to 00 to match the rest of the data and fix the checksum.

In hexedit, I navigated to the line starting with 00000040 and changed the aa to 00.

This was the biggest problem. pngcheck also reported an "invalid chunk length (too large)". This pointed to a very serious structural error.

On the line starting 00000050, I found the source of the error. This section should have been the start of the IDAT (Image Data) chunk, but it was completely wrong.

Following a more advanced analysis (calculating the distance from this chunk's data to the start of the next valid chunk), the correct length was determined to be 00 00 FF A5.

So, on the line starting with 00000050, I made the final changes:

    Changed the length from aa aa ff a5 to 00 00 ff a5.

    Changed the name from ab 44 45 54 to 49 44 41 54.

<img width="655" height="481" alt="Screenshot 2025-08-18 181743" src="https://github.com/user-attachments/assets/43e51f9f-d142-4587-83b1-c0af899eb4e2" />


After making these changes, I saved the file by pressing Ctrl+X and then Y.

#### Summary of all the changes made

The changes are listed by their location (offset) in the file.
1. PNG Signature Fix (The first 8 bytes)

   At offset 0x01, we changed 65 to 50 (to form the 'P' in PNG).

    At offset 0x03, we changed 34 to 47 (to form the 'G' in PNG).

    At offset 0x06, we changed B0 to 1A.

    At offset 0x07, we changed AA to 0A.

2. IHDR Chunk Name Fix (The first chunk)

    At offset 0x0C, we changed 43 to 49 (the 'I' in IHDR).

    At offset 0x0D, we changed 22 to 48 (the 'H' in IHDR).

3. pHYs Chunk Data Fix (Physical dimensions)

    At offset 0x48, we changed aa to 00 (to correct the corrupted X-axis pixel density value).

4. IDAT Chunk Fix (The main image data chunk)

    Length Correction:

      At offset 0x50, we changed aa to 00.

      At offset 0x51, we changed aa to 00.

    Name Correction:

      At offset 0x53, we changed ab to 49 (the 'I' in IDAT).

      At offset 0x56, we changed 45 to 41 (the 'A' in IDAT).


With all the corrupted sections repaired, the file was now a structurally valid PNG. I opened it with Kali's default image viewer
<img width="307" height="324" alt="Screenshot 2025-08-18 181957" src="https://github.com/user-attachments/assets/88ced079-1afa-46e6-8828-d0af54499966" />

Submit the flag to complete the challenge!

