# PicoGym Web Exploitation Writeup


Author: [Samarth Arora](https://github.com/Samadeol) 

Challenge Page: [Web Gauntlet](http://jupiter.challenges.picoctf.org:54319/)

## Walkthrough
in round 1 we cant use `or` in our sqli.
let try username as `admin';` and an arbritary password and it works.
in round 2 we cant use `or`,`and`,`like`,`=`,`--` but we already used none of these.
lets try the same credentials again, and we get it !
the new filters are `<` and `>`.
for round 3 we cant use `admin`.
searching on sqlite concatenation we find the `||` operator ,
new filter => `union`,
retrying the same for round 5.
we find the flag in the filter file .


## Flag
`picoCTF{y0u_m4d3_1t_a5f58d5564fce237fbcc978af033c11b}`
