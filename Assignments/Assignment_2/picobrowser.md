# PicoGym Web Exploitation Writeup


Author: [Samarth Arora](https://github.com/Samadeol) 

Challenge Page: [picobrowser](https://jupiter.challenges.picoctf.org/problem/28921/)

## Walkthrough
Had to install firefox cuz chrome cant do simple resends.
Resend the html header request and change the field of `User-Agent` to `picobrowser`
and view its response which contains the flag.

## Flag
`picoCTF{p1c0_s3cr3t_ag3nt_84f9c865}`
