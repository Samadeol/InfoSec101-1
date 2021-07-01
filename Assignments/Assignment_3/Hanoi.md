# MicroCTF Writeup


Author: [Samarth Arora](https://github.com/Samadeol) 

Level: Hanoi

## Walkthrough
Here is a login function
```
4520 <login>
4520:  c243 1024      mov.b	#0x0, &0x2410
4524:  3f40 7e44      mov	#0x447e "Enter the password to continue.", r15
4528:  b012 de45      call	#0x45de <puts>
452c:  3f40 9e44      mov	#0x449e "Remember: passwords are between 8 and 16 characters.", r15
4530:  b012 de45      call	#0x45de <puts>
4534:  3e40 1c00      mov	#0x1c, r14
4538:  3f40 0024      mov	#0x2400, r15
453c:  b012 ce45      call	#0x45ce <getsn>
4540:  3f40 0024      mov	#0x2400, r15
4544:  b012 5444      call	#0x4454 <test_password_valid>
4548:  0f93           tst	r15
454a:  0324           jz	$+0x8
454c:  f240 4700 1024 mov.b	#0x47, &0x2410
4552:  3f40 d344      mov	#0x44d3 "Testing if password is valid.", r15
4556:  b012 de45      call	#0x45de <puts>
455a:  f290 5400 1024 cmp.b	#0x54, &0x2410
4560:  0720           jne	#0x4570 <login+0x50>
4562:  3f40 f144      mov	#0x44f1 "Access granted.", r15
4566:  b012 de45      call	#0x45de <puts>
456a:  b012 4844      call	#0x4448 <unlock_door>
456e:  3041           ret
4570:  3f40 0145      mov	#0x4501 "That password is not correct.", r15
4574:  b012 de45      call	#0x45de <puts>
4578:  3041           ret
```
On obsering that we can see that in order to get to the block  which calls the unlock_door 
function we need the condition `455a:  f290 5400 1024 cmp.b	#0x54, &0x2410` to 
be true . cmp.b command compares values bitwise
the password starts storing at the memory address `#0x2400`.
the byte at address `#0x2400` should be `0x54`. 
There must be 16 dummy bytes
`6969696969696969696969696969696954`
## Password
`6969696969696969696969696969696954`
