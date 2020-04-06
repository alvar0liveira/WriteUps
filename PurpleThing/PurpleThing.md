# Purple Thing
From [CTFlearn](https://ctflearn.com/challenge/108)

This challenge gives an image and tells us that there is another image inside which contains the flag.
![PurpleThing](./PurpleThing.jpeg)

A tool for searching for files and executable code in image formats is **binwalk**

```bash 

$ binwalk PurpleThing.jpeg


DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             PNG image, 780 x 720, 8-bit/color RGBA, non-interlaced
41            0x29            Zlib compressed data, best compression
153493        0x25795         PNG image, 802 x 118, 8-bit/color RGBA, non-interlaced



```
Running binwalk on the image gives the files and their position, you can see there are images (original at 0x0 and the flag at 0x25795). To get files by their type signatures you can use: 

```bash

$ binwalk --dd='.*' PurpleThing.jpeg

```

Which will create a folder with the extracted files

```bash
$ ls 

PurpleThing.jpeg  _PurpleThing.jpeg.extracted 

$ ls PurpleThing.jpeg.extracted

0  25795  29  29-0


```
You can see there is a file with name 25795 which is the flag.

![Flag](./flag.png)


Also you could use another tool called [CyberChef](https://gchq.github.io/CyberChef) which is graphical and easy to use.
