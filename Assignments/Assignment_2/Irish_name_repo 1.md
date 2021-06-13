# PicoGym Web Exploitation Writeup


Author: [Samarth Arora](https://github.com/Samadeol) 

Challenge Page: [Irish-Name-Repo 1] (http://jupiter.challenges.picoctf.org:39720)

## Walkthrough
Went to the admin login section in the menu.(irish be hot btw)!
Put username as admin and when i put a `'` in the password there is an error which hints me towards sqli vulnerabilities.
So i tried the most basic sql injection using password as `' or 1=1--` and i got the flag. :)

## Flag
`picoCTF{s0m3_SQL_c218b685}`
