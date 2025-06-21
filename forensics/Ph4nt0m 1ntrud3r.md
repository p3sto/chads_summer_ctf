# Ph4nt0m 1ntrud3r
Tags: `Easy` `Forensics` `picoCTF 2025` `browser_webshell_solvable`</br>
Link: https://play.picoctf.org/practice/challenge/459

### Challenge
```
A digital ghost has breached my defenses, and my sensitive data has been stolen! 😱💻
Your mission is to uncover how this phantom intruder infiltrated my system and retrieve
the hidden flag. To solve this challenge, you'll need to analyze the provided PCAP file
and track down the attack method. The attacker has cleverly concealed his moves in well
timely manner. Dive into the network traffic, apply the right filters and show off your
forensic prowess and unmask the digital intruder! Find the PCAP file here Network Traffic
PCAP file and try to get the flag. 
```

<details>
  <summary>Hint 1</summary> 
  
  ```Filter your packets to narrow down your search.``` 
</details>

<details>
  <summary>Hint 2</summary>
  
  ```Attacks were done in timely manner.``` 
</details>

<details>
  <summary>Hint 3</summary>
  
  ```Time is essential```
</details>

### Solution
After downloading and opening the PCAP file in Wireshark, we notice that the TCP payloads contain Base64-encoded data. 

![image](https://github.com/user-attachments/assets/db173b21-372f-45e9-b098-0d29db0e886f)


We also notice that the packets are also out of order by number and sort by the time field, this also ties in with hints 2 and 3. Extracting and decoding the base64-encoded using a decoder like Cyberchef, from all the packets, we notice that only a few of them decode into readable text. This outputs the chanllenge's flag


<details>
  <summary>Flag</summary>
  
  `picoCTF{1t_w4snt_th4t_34sy_tbh_4r_f318db22}`
</details>


