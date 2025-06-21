# flags are stepic
Tags: `Medium` `Forensics` `picoCTF 2025` `browser_webshell_solvable`</br>
Link: https://play.picoctf.org/practice/challenge/481

### Challenge
```
A group of underground hackers might be using this legit site to communicate. Use your
forensic techniques to uncover their message
```

<details>
  <summary>Hint 1</summary> 
  
  ```In the country that doesn't exist, the flag persists``` 
</details>

### Solution
After launching the instance, we are taken to a webpage with a list of cards showing countries and their flags. However, one flag stands out 
as not being a real country i.e. The Republic of Upanzi. 

![image](https://github.com/user-attachments/assets/d87c7964-ee33-4c69-b4e6-61262f25b6ea)

After downloading the flag's PNG and running it through common stegonography tools like zsteg and exiftool yielded no meaningful results. I looked
further into the title and the word 'stepic' stood out. With some further research, I found out that stepic was actually a python library and CLI 
tool used for stegonography. After simply installing it and running the command with the correct arguments, the flag was produced.
```bash
$ stepic -d -i upz.png 
/usr/lib/python3/dist-packages/PIL/Image.py:3186: DecompressionBombWarning: Image size (150658990 pixels) exceeds limit of 89478485 pixels, could be decompression bomb DOS attack.
  warnings.warn(
picoCTF{[REDACTED]}
```
<details>
  <summary>Flag</summary>
  
  `picoCTF{fl4g_h45_fl4g9a81822b}`
</details>
