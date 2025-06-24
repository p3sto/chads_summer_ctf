# RED
Tags: `Easy` `Forensics` `picoCTF 2024` `browser_webshell_solvable`</br>
Link: https://play.picoctf.org/practice/challenge/460

### Challenge
```
RED, RED, RED, RED
Download the image: red.png
```

<details>
  <summary>Hint 1</summary> 
  
  ```The picture seems pure, but is it though?``` 
</details>

<details>
  <summary>Hint 2</summary>
  
  ```Red?Ged?Bed?Aed?``` 
</details>

<details>
  <summary>Hint 3</summary>
  
  ```Check whatever Facebook is called now.```
</details>

### Solution
Using exiftools on the image yields metadata about the image, notably the `Poem` field. Separating each sentence on a new line produces a new hint using each of the capital letters. 

```
Crimson heart, vibrant and bold,.
Hearts flutter at your sight..
Evenings glow softly red,.
Cherries burst with sweet life..
Kisses linger with your warmth..
Love deep as merlot..
Scarlet leaves falling softly,.
Bold in every stroke.
```

CHECKLSB. This indicates that the flag is encoded using LSB Stegonography and with a tool like [`zsteg`](https://github.com/zed-0xff/zsteg) we can extract the message:

```sh
$ zsteg red.png 

meta Poem           .. text: "Crimson heart, vibrant and bold,\nHearts flutter at your sight.\nEvenings glow softly red,\nCherries burst with sweet life.\nKisses linger with your warmth.\nLove deep as merlot.\nScarlet leaves falling softly,\nBold in every stroke."
b1,rgba,lsb,xy      .. text: "cGljb0NURntyM2RfMXNfdGgzX3VsdDFtNHQzX2N1cjNfZjByXzU0ZG4zNTVffQ==cGljb0NURntyM2RfMXNfdGgzX3VsdDFtNHQzX2N1cjNfZjByXzU0ZG4zNTVffQ==cGljb0NURntyM2RfMXNfdGgzX3VsdDFtNHQzX2N1cjNfZjByXzU0ZG4zNTVffQ==cGljb0NURntyM2RfMXNfdGgzX3VsdDFtNHQzX2N1cjNfZjByXzU0ZG4zNTVffQ=="
b1,rgba,msb,xy      .. file: OpenPGP Public Key
b2,g,lsb,xy         .. text: "ET@UETPETUUT@TUUTD@PDUDDDPE"
b2,rgb,lsb,xy       .. file: OpenPGP Secret Key
b2,bgr,msb,xy       .. file: OpenPGP Public Key
b2,rgba,lsb,xy      .. file: OpenPGP Secret Key
b2,rgba,msb,xy      .. text: "CIkiiiII"
b2,abgr,lsb,xy      .. file: OpenPGP Secret Key
b2,abgr,msb,xy      .. text: "iiiaakikk"
b3,rgba,msb,xy      .. text: "#wb#wp#7p"
b3,abgr,msb,xy      .. text: "7r'wb#7p"
b4,b,lsb,xy         .. file: 0421 Alliant compact executable not stripped
```

Again we see the poem from the metadata, but also a repeating Base64 string `cGljb0NURntyM2RfMXNfdGgzX3VsdDFtNHQzX2N1cjNfZjByXzU0ZG4zNTVffQ==`. Putting this value in any Base64 decoder will output the flag.

<details>
  <summary>Flag</summary>
  
  `picoCTF{r3d_1s_th3_ult1m4t3_cur3_f0r_54dn355_}`
</details>
