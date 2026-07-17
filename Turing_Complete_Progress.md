# Turing Complete
There are total of 6 chapters in the game Turing Complete, and I will skip sharing the first two chapter here as the first two chapters mainly introduce the fundamentals of digital logic.I will share my progress of Turing Complete here.
## CPU Architecture
### Registers
Objective:<br>
          &emsp;&emsp;Create a Circuit which can move data to a destination from a source.<br><br>
My Thought Process:
                <br>&emsp;&emsp;A 1-byte instruction is given by the game, and I need to use this instruction to determine which register is the destination, which one is the source.
At the beginning, I directly connect a 3-bit decoder to the instruction. Soon I realized that it can only tell me the source, but how can I determine the destination?
To solve this problem, I changed my circuit with a splitter to split the instruction to 8 bits. bit 0-2 are used for determining the source, and bit 3-5 are used for
determining the destination. Then I apply makers to merge the bit0-2 and bit3-5 into two separate 3-bit values. After that, using the 3-bit decoder to decode those two
value, this way I can clearly distinguish between sources and destinations. To move the value in between muiltiple registers, I connect each register‘s input and output
together. To avoid short circuit, switches are necessary to be added into the circuit. I put switch at every single input and output of all the registers.
<br><br>My Solution:<br>
<img width="768" height="792" alt="image" src="https://github.com/user-attachments/assets/723a68d1-c05c-4ec3-9d8f-84a0654ae0fc" />
<br><br><br>
### ALU
Objective:<br>
          &emsp;&emsp;Merge in the Arithemetic Logic Unit circuit with the Register I build previously<br><br>
My Thought Process:
                <br>&emsp;&emsp;Last time, I've built a register circuit that can move data from a source to a destination. But this time I need to apply the ALU into the circuit. Same instruction as the Register unit, the bit 6-7 are using in this level. I need to apply the bit 6-7 to determine the mode. As usual, I use decoder, since there's only two bit for 
determining the mode, I use a two bit decoder.To apply the ALU to reg 1-3, I just simply connect the wire together. There was a problem I faced that is how to disable the move component when it is in other mode. There was a hint given says the 3-bit decoder has a enable input. I tried to connect data from the decoder to the enable input, and it doesn't work. After careful reviewing, I found out that this input is only for disable, if the data send is 0, the decoder is enable, vice versa, so I need to put a "NOT" Gate in between the instruction data and the decoder.
<br><br>My Solution:<br>
<img width="1204" height="1251" alt="Screenshot 2026-07-14 153144" src="https://github.com/user-attachments/assets/7636df94-c269-46aa-8587-00dcee52d830" />
### Immediate Value
Objective:<br>
          &emsp;&emsp;Directly move the number represent by instruction to reg 0<br><br>
My Thought Process:
                <br>&emsp;&emsp;It is still a add-on of the previous circuit. What I need to do is just move the value given by 
instruction to the register 0. I simply connect the instruction's value to the reg 0. Since there's two condition that will enable the reg 0. I tried to directly connect the decoder's signal to the enable component of reg 0, but it cause the short circuit. To solve this problem, I use an "OR" gate and connect the wire used for "move" mode and wire used for "immediate" mode to the input of the "OR" gate and then connect the output of the "OR" gate to the enable component of reg 0.
<br><br>My Solution:<br>
<img width="1279" height="1291" alt="image" src="https://github.com/user-attachments/assets/e832b6db-df74-478d-bf35-691f6bd1b0af" />
### Turing Complete
Objective:<br>
          &emsp;&emsp;Apply the counter and the overwrite function to build a real computer<br><br>
My Thuoght Process:
          <br>&emsp;&emsp;In this level, which is the last level of CPU Architecture, I need to apply the counter and it's overwrite function to the circuit. Before, there was a level named " Condition", the circuit I created was great suitable to accomplish this goal. Here is the "Condition" circuit:
          <br><img width="1053" height="509" alt="image" src="https://github.com/user-attachments/assets/f019bfa0-056b-41d8-8e02-dbe48906428d" /><br>
          Since I had already create this function, so I just simply made it to a component so I can apply it into the Turing Complete level. The decision logic was compare the value of reg 3 and the signal from the RAM to determine if overwrite the value of the counter with reg 0. After a reasonable connection, the Turing Complete Computer finished.
<br><br>My Solution:<br>
<img width="1470" height="957" alt="Screenshot 2026-07-14 172531" src="https://github.com/user-attachments/assets/5d602a06-6ccd-42d3-af78-1ea27f3aa351" />
## PROGRAMMING
### Punchcard Programming
Objective:<br>
          &emsp;&emsp;Add 5 to the input<br><br>
My Thuoght Process:
          <br>&emsp;&emsp;This level's goal is really simple, just add 5 to the input value. You need to edit the "Program", giving out the specific instruction to the "Program" to accomplish the goal of adding 5 to the input I apply the binary programming. First I "immediate" 5 into reg 0, and then move the value in reg 0 to the reg 1, because the ALU can only do work on reg 1 and reg 2, the output for ALU can only be stored in reg 3.Then I move the input value into the reg 2, after that, I apply the ALU to add reg 1 and reg 2 together. Finally, move the value stored in reg 3 to the output.<br> This level is really interesting, I spent a lot of time making my CPU and now I can finally command my CPU.
<br><br>My Solution:<br>
<img width="1368" height="990" alt="Screenshot 2026-07-15 191417" src="https://github.com/user-attachments/assets/1ba0b062-0999-4d42-8a06-1a6879cfc505" />
### Assembly Programming
Objective:<br>
          &emsp;&emsp;Add 5 to the input using assembly programming<br><br>
My Thuoght Process:
          <br>&emsp;&emsp;It is basiclly the same thing as yesterday, the only difference is change the binary programming into assembly programming. The only thing I need to do is using words to decribe the steps.
<br>My Solution:<br>
<img width="999" height="297" alt="Screenshot 2026-07-16 201417" src="https://github.com/user-attachments/assets/779a5689-5bf2-47a8-a1a0-ee343d45320e" />
### Circumference
Objective:<br>
          &emsp;&emsp;Use the given radius to cacuiate the circumference. The formula is 2pir, pi can be round to 3 in this case.<br><br>
My Thuoght Process:
          <br>&emsp;&emsp;Since the pi is round to 3 in this case, so the easiest way to accomplish multiplication is through its foundamental principal that. adding a value n times is the same thing as time the value by n. Since 2 times 3 is 6, so the goal is simple, I just need to add radius 6 times. Here's how I did that.
<br>My Solution:<br>
<img width="329" height="444" alt="Screenshot 2026-07-16 204655" src="https://github.com/user-attachments/assets/5a165fa4-7f2c-440f-9881-5b1e6f472117" />
<br>&emsp;&emsp; But then I realized the use of r0 can be skipped, because although the value in r1 and r2 have been added up and send to r3, but the value in r1 and r2 remained.
<br>Here is the code after modified<br>
<img width="327" height="477" alt="Screenshot 2026-07-16 210216" src="https://github.com/user-attachments/assets/2c868a28-c93f-4e28-bc13-03ab799b0a3d" />


          
          
