# Glory of the Garden
## Challenge Description

  <img width="931" height="631" alt="Screenshot 2025-08-08 114802" src="https://github.com/user-attachments/assets/48b28333-3c44-4e8f-b668-0b1f5bb784d5" />

## Analysis and Solution

Just to start the analysis we can use the **file** command to see what kind of file it is and understand it better, to do so 

```bash
└─$ file garden.jpg                    
garden.jpg: JPEG image data, JFIF standard 1.01, resolution (DPI), density 72x72, segment length 16, baseline, precision 8, 2999x2249, components 3

```

nothing of significance is found here , to see if any flag is hidden within the data of the image itself we can use the **strings** command as shown 
```bash
└─$ strings garden.jpg
JFIF
```

A bunch of data goes by and the flag is found at the bottom of the result

Submit the flag to complete the challenge!
