# shark on wire 2

## Challenge Description 

<img width="923" height="489" alt="image" src="https://github.com/user-attachments/assets/1446fdd3-726c-4890-b864-da6c36a09e34" />

## Solution and Analysis 

Download the capture file and open it in wireshark, You will get the following 

<img width="1863" height="712" alt="image" src="https://github.com/user-attachments/assets/0c1ed623-cc43-4c1c-a9d2-c10eca707f8f" />

Going thru the packet file majority of the protocols being used are **TCP** and **UDP**, nothing much of interest is found in the TCP section, however going thru the UDP section we find a suspicious IP address namely **10.0.0.66** as it seems to be changing ports everytime as shown below

<img width="1919" height="629" alt="image" src="https://github.com/user-attachments/assets/5b72f587-6487-4a4e-ae77-2f26077038f1" />

5000 and similar numbers (e.g., 5112, 5105): These represent the source ports on the client machine. When a computer initiates a connection to a server, it uses a high-numbered, ephemeral port for its end of the communication

The flag is hidden with the last 3 numbers of the Port numbers, just convert them into **ASCII** to reveal the flag 

```text
5000
5112
5105
5099
5111
5067
5084
5070
5123
5112
5049
5076
5076
5102
5051
5114
5051
5100
5095
5100
5097
5116
5097
5095
5118
5049
5097
5095
5115
5116
5051
5103
5048
5125
```

Use any online tools to recover the flag as shown 

<img width="968" height="841" alt="image" src="https://github.com/user-attachments/assets/b7868ad6-869a-473b-882d-3d3387f88e89" />
