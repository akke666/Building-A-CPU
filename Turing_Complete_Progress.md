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
