# PicoGym Web Exploitation Writeup


Author: [Samarth Arora](https://github.com/Samadeol) 

Challenge Page: [caas](https://caas.mars.picoctf.net/)

## Walkthrough
I examined the file we got in the q sqli doesnt seem like the way to go .
instead the terminal commands seem like the solutions .
trying `;ls;` as the cowsay message ,we get the list of files and we notice  
a file named "falg.txt" so doing `;cat falg.txt;` we get our flag. 

## Flag
`picoCTF{moooooooooooooooooooooooooooooooooooooooooooooooooooooooooooo0o}`
