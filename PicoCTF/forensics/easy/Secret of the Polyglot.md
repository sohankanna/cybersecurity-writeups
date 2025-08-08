# Secret of the Polyglot

## Challenge Description 

<img width="656" height="812" alt="Screenshot 2025-08-08 121937" src="https://github.com/user-attachments/assets/a89533d1-2789-4e3b-824e-c9fe3adcf504" />

## Solution 

After downloading the file, open the pdf to get the last half of the flag 

<img width="831" height="848" alt="Screenshot 2025-08-08 121038" src="https://github.com/user-attachments/assets/ec627806-b579-4b31-86b7-043933599125" />

We can use the **file** command to see the true nature of the file as shown 

```bash
└─$ file flag2of2-final.pdf 
flag2of2-final.pdf: PNG image data, 50 x 50, 8-bit/color RGBA, non-interlaced
```

as we can see it is actually a PNG file, use the **mv** command to rename the file from .pdf to .png extension 

```bash
└─$ mv flag2of2-final.pdf something.PNG    
```

And then open the file to get the first half of the flag 
<img width="204" height="186" alt="Screenshot 2025-08-08 121810" src="https://github.com/user-attachments/assets/1eaf031f-6f41-486f-99eb-a8f80fcde439" />

Submit the complete flag to complete the challenge!
