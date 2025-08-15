# m00nwalk 

## Challenge Description 

<img width="927" height="460" alt="image" src="https://github.com/user-attachments/assets/ad1d5422-bdbe-4861-93e5-7ce8ff1c0b68" />

## Solution and Analysis 

The hint is referring to the way images were transmitted back from the moon, one of the technology used was slow-scan television (SSTV). Specifically, the Apollo 11 mission utilized a black and white SSTV camera to capture the first steps on the Moon. The SSTV signal was then converted to the standard broadcast format (NTSC) for global viewing.
SSTV, or Slow Scan Television, is a method used by amateur radio operators to transmit and receive still images over radio waves. Unlike regular television that sends frames rapidly, SSTV sends images much slower, hence the name "slow scan". This technique allows for the transmission of pictures over bandwidths typically used for voice communication

To decode this you will need to install the following package on your machine(preferably linux)

```bash
git clone https://github.com/colaclanth/sstv.git
python setup.py install
```

Credits: https://github.com/colaclanth/sstv

Once the setup is done just run the following command 

```bash
sstv -d message.wav -o result.png
```
And the flag will be in the resulting image 

<img width="317" height="252" alt="image" src="https://github.com/user-attachments/assets/62f737c5-5c64-4443-956a-fa7f981a08c8" />
