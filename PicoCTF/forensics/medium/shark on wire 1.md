# shark on wire 1 

## Challenge Description 

<img width="929" height="462" alt="image" src="https://github.com/user-attachments/assets/bdcf73fd-9e4d-43ab-a543-8525c2c4b2aa" />

## Solution and Analysis 

First download the given packet capture file and open it in a tool like wireshark. 

<img width="1885" height="718" alt="image" src="https://github.com/user-attachments/assets/962416a7-2cfb-4535-a19c-80f3e71f79ee" />

A lot of misguiding information are given in here, focus only on the **UDP** packets. You can filter out using the display filter box

<img width="1887" height="712" alt="image" src="https://github.com/user-attachments/assets/33471678-423b-4dd5-a203-4de893cd2852" />

Right click on any UDP packet and click on follow stream. "Follow Stream" is a powerful feature that allows you to reconstruct and view the complete conversation between two endpoints.When you're analyzing network traffic, data is captured in individual packets. A single activity, like loading a webpage, can involve hundreds or even thousands of packets. The "Follow Stream" feature pieces together these related packets, presenting the application-level data in a way that's easy to read and understand.

<img width="1895" height="914" alt="image" src="https://github.com/user-attachments/assets/4ffd49e2-a8da-4509-844a-9725643dbe7f" />

You may have the change the option to **ASCII** under the show as box below. To get the flag simply change the stream number to **6** in the lower right hand side of the window. The number, often referred to as the "Stream index," is a simple, sequential number that Wireshark assigns to each unique conversation it identifies in a capture file.The first conversation will be stream 0, the next will be stream 1, and so on.
This number is an internal identifier used by Wireshark to keep track of conversations.

<img width="1919" height="873" alt="image" src="https://github.com/user-attachments/assets/bbe4fd49-bc46-4ac3-8681-f7cbed9ad448" />


