# PicoGym Web Exploitation Writeup


Author: [Samarth Arora](https://github.com/Samadeol) 

Challenge Page: [Some Assembly Required 2](http://mercury.picoctf.net:21939/)

## Walkthrough
the `Wasm` code is almost the same as the first part of this series.
Upon spotting the difference in the copy function we see that every character of the string stored
at memory address 1024 has been XOR'ed with 8 and then stored at the position b from 1024.
So to get the real flag we operate the string with bitwise XOR with 8.


## Flag
`picoCTF{6b247e06e36c9984b7500db8d992f3fe}`
