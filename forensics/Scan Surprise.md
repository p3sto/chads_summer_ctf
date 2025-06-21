# Scan Surprise
Tags: `Easy` `Forensics` `picoCTF 2024` `shell` `browser_webshell_solvable` `qr_code`</br>
Link: https://play.picoctf.org/practice/challenge/444

### Challenge
```
I've gotten bored of handing out flags as text. Wouldn't it be cool if they
were an image instead? You can download the challenge files here:
  challenge.zip
```

<details>
  <summary>Hint 1</summary> 
  
  ```QR codes are a way of encoding data. While they're most known for storing URLs, they can store other things too.``` 
</details>

<details>
  <summary>Hint 2</summary>
  
  ```Mobile phones have included native QR code scanners in their cameras since version 8 (Oreo) and iOS 11``` 
</details>

<details>
  <summary>Hint 3</summary>
  
  ```If you don't have access to a phone, you can also use zbar-tools to convert an image to text```
</details>

### Solution
Simply downloading and extracting the challenge.zip file produces the flag.png in `challenge/home/ctf-player/drop-in/` . This is a QR code that 
provides the challenge's flag when scanned with a QR code scanner. I used zbarimg from the `zbar-tools` [package](https://zbar.sourceforge.net/).

```sh
~/challenge/home/ctf-player/drop-in$ zbarimg flag.png 
QR-Code:picoCTF{[REDACTED]}
scanned 1 barcode symbols from 1 images in 0 seconds
```

<details>
  <summary>Flag</summary>
  
  `picoCTF{p33k_@_b00_0194a007}`
</details>


