# Verify 

## Challenge Description 

<img width="918" height="825" alt="image" src="https://github.com/user-attachments/assets/ab18d7d1-491b-4a3f-9442-627043b9e45d" />

## Solution and Analysis 

First launch the challenge instance so as to connect to the interface. Once connected run the **ls** command to see all the files in the given directory 

```bash
ctf-player@pico-chall$ ls
checksum.txt  decrypt.sh  files
```

The checksum file contains the following 

```bash
ctf-player@pico-chall$ cat checksum.txt
3ad37ed6c5ab81d31e4c94ae611e0adf2e9e3e6bee55804ebc7f386283e366a4
```

The decrypt file contains

```bash
ctf-player@pico-chall$ cat decrypt.sh 

        #!/bin/bash

        # Check if the user provided a file name as an argument
        if [ $# -eq 0 ]; then
            echo "Expected usage: decrypt.sh <filename>"
            exit 1
        fi

        # Store the provided filename in a variable
        file_name="$1"

        # Check if the provided argument is a file and not a folder
        if [ ! -f "/home/ctf-player/drop-in/$file_name" ]; then
            echo "Error: '$file_name' is not a valid file. Look inside the 'files' folder with 'ls -R'!"
            exit 1
        fi

        # If there's an error reading the file, print an error message
        if ! openssl enc -d -aes-256-cbc -pbkdf2 -iter 100000 -salt -in "/home/ctf-player/drop-in/$file_name" -k picoCTF; then
            echo "Error: Failed to decrypt '$file_name'. This flag is fake! Keep looking!"
        fi
        ctf-player@pico-chall
```

in this the above code does the following 


  Checks for a filename: The script first makes sure you've provided a filename when you run it.
  
  Verifies the file: It then checks if the filename you gave it actually exists in the /home/ctf-player/drop-in/ directory.
  
  Tries to decrypt: The core of the script uses the OpenSSL tool to try and decrypt the file you specified.

The files folder contains a lot of files as shown 
<img width="652" height="435" alt="image" src="https://github.com/user-attachments/assets/7e2f2214-d620-4337-91ae-121c04368945" />

and one of them contains the flag which matches the checksum given to us in the checksum file. To verify which file has the correct checksum we can run the following code 

```bash
ctf-player@pico-chall$ sha256sum files/* | grep 3ad37ed6c5ab81d31e4c94ae611e0adf2e9e3e6bee55804ebc7f386283e366a4
```

This command gets the hash of each file (SHA256) and compares that with the existing checksum which will display the one file which has it. Once you get the correct file run the below code to get the flag 
In my case the file with the correct checksum was e018b74

```bash
ctf-player@pico-chall$ ./decrypt.sh files/e018b574 
picoCTF{FLAG_IN_HERE}
```

Submit the flag to complete the challenge!
