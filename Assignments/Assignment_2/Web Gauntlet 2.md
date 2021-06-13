# PicoGym Web Exploitation Writeup


Author: [Samarth Arora](https://github.com/Samadeol) 

Challenge Page: [Web Gauntlet 2](http://mercury.picoctf.net:21336/)

## Walkthrough
for this question we cannot use
`or and true false union like = > < ; -- /* */ admin`
so we need username as "admin"
So went ahead and learnt something called sqlite where u could break the word.
So username= `ad'||'min`.
Since we had no other choice i went back to basic sqlite commands and used the not to get password to True.
and password as `aaa' is not 'a`.
the username should become admin and he password should evalute to True.
hence giving us the flag in filter.php


## Flag
`picoCTF{0n3_m0r3_t1m3_838ec9084e6e0a65e4632329e7abc585}`
