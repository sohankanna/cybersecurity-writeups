# Ph4nt0m 1ntrud3r 

## Challenge Details 

<img width="664" height="780" alt="Screenshot 2025-08-08 124115" src="https://github.com/user-attachments/assets/2f5d84b9-ff14-427f-931e-bc72bbd15c58" />

## Analysis and Solution 

 After downloading the file, we can see it is a **pcap** file, we can use **wireshark** which is a robust packet analysis tool for this as shown 

 <img width="1914" height="639" alt="Screenshot 2025-08-08 124436" src="https://github.com/user-attachments/assets/f4e41bc4-060a-4446-83bf-6dee35db93be" />

we can see that the packets are not ordered, the time each packet has arrived is different and not in any concise order

<img width="965" height="292" alt="Screenshot 2025-08-08 124443" src="https://github.com/user-attachments/assets/669a2d0e-4b3b-4b87-9116-147f7c0fb119" />

Further more on the above image we can see small amounts of data base 64 encoded as well. To extract this information we can use the **strings** command to do so. 

```bash
└─$ strings myNetworkTraffic.pcap 
ezF0X3c0cw==
cGljb0NURg==
bnRfdGg0dA==
Yt8ksMM=
3psv5C4=
YQEFzIU=
YmhfNHJfOQ==
a23/UbI=
TOGSGg4=
bpzQ0R8=
fQ==
nfu4Vww=
J4auZMY=
ePRXDio=
fjIzQwk=
XThGxuE=
ckBkZLk=
CJr4oDk=
BgJLB0c=
XzM0c3lfdA==
NTlmNTBkMw==
dgV9v0s=

```

However this is not in order, to order them according to the time in which they were sent we have to make use of tshark which is a CLI based packet analysis tool. 

```bash
└─$ tshark -r myNetworkTraffic.pcap -Y "tcp.len > 0" -T fields -e frame.time_epoch -e tcp.payload | sort -n | cut -f 2- | while read payload; do if [ -n "$payload" ]; then echo ${payload//:} | xxd -r -p; echo; fi; done
ePRXDio=
dgV9v0s=
nfu4Vww=
XThGxuE=
CJr4oDk=
TOGSGg4=
ckBkZLk=
YQEFzIU=
3psv5C4=
a23/UbI=
BgJLB0c=
Yt8ksMM=
fjIzQwk=
bpzQ0R8=
J4auZMY=
cGljb0NURg==
ezF0X3c0cw==
bnRfdGg0dA==
XzM0c3lfdA==
YmhfNHJfOQ==
NTlmNTBkMw==
fQ==
             
```
submit the base64 decoded flag to complete the challenge!
