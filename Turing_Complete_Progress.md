# Turing Complete
There are total of 6 chapters in the game Turing Complete, and I will skip sharing the first two chapter here. Starting with the third chapter---CPU Architecture
## Registers
Objective:<br>
          &emsp;&emsp;Create a Circuit which can move value to a destination from a source.<br><br>
My Thought Process:
                <br>&emsp;&emsp;A 1-byte instruction is given by the game, and I need to use this instruction to determine which register is the destination, which one is the source.
At the beginning, I directly connect a 3-bit decoder to the instruction. Soon I realized that it can only tell me the source, but how can I determine the destination?
To solve this problem, I changed my circuit with a splitter to split the instruction to 8 bits. bit0-2 are used for determining the source, and bit3-5 are used for
determining the destination. Then I apply makers to merge the bit0-2 and bit3-5 into two separate 3-bit values. After that, using the 3-bit decoder to decode those two
value, this way I can clearly distinguish between sources and destinations. To move the value in between muiltiple registers, I connect each register‘s input and output
together. To avoid short circuit, switches are necessary to be added into the circuit. I put switch at every single input and output of all the registers.
<br><br>My Solution:
<img width="768" height="792" alt="image" src="https://github.com/user-attachments/assets/723a68d1-c05c-4ec3-9d8f-84a0654ae0fc" />
