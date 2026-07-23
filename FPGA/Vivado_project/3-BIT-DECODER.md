# 3-BIT-DECODER
## Function:
Toggles between 8 outputs based on a 3 bit input
## Code:

``` Verilog
 module mux3(
    input a0,
    input a1,
    input a2,
    output reg o0,
    output reg o1,
    output reg o2,
    output reg o3,
    output reg o4,
    output reg o5,
    output reg o6,
    output reg o7
    );
always @(*)
    case ({a2,a1,a0})
        3'b000: {o7,o6,o5,o4,o3,o2,o1,o0}=8'b00000001;
        3'b001: {o7,o6,o5,o4,o3,o2,o1,o0}=8'b00000010;
        3'b010: {o7,o6,o5,o4,o3,o2,o1,o0}=8'b00000100;
        3'b011: {o7,o6,o5,o4,o3,o2,o1,o0}=8'b00001000;
        3'b100: {o7,o6,o5,o4,o3,o2,o1,o0}=8'b0001000₀;
        3'b101: {o7,o6,o5,o4,o3,o2,o1,o0}=8'b00100000;
        3'b110: {o7,o6,o5,o4,o3,o2,o1,o0}=8'b01000000;
        3'b111: {o7,o6,o5,o4,o3,o2,o1,o0}=8'b10000000;
        default: {o7,o6,o5,o4,o3,o2,o1,o0}=8'b00000000;
    endcase
 endmodule

 ```
 
 ## Testbench

``` Verilog
`timescale 1ns/1ns

module decoder3_tb();
    reg a0;
    reg a1;
    reg a2;
    wire o0;
    wire o1;
    wire o2;
    wire o3;
    wire o4;
    wire o5;
    wire o6;
    wire o7;
    decoder3 decoder3_inst0(
    .a0(a0),
    .a1(a1),
    .a2(a2),
    .o0(o0),
    .o1(o1),
    .o2(o2),
    .o3(o3),
    .o4(o4),
    .o5(o5),
    .o6(o6),
    .o7(o7)
    );
    
    initial begin
        a2=0; a1=0; a0=0;
        #20;
        a2=0; a1=0; a0=1;
        #20;
        a2=0; a1=1; a0=0;
        #20;
        a2=0; a1=1; a0=1;
        #20;
        a2=1; a1=0; a0=0;
        #20;
        a2=1; a1=0; a0=1;
        #20;
        a2=1; a1=1; a0=0;
        #20;
        a2=1; a1=1; a0=1;
        #20;
        $stop;
    end
endmodule
```

## RTL Schematic:
 <img width="397" height="918" alt="image" src="https://github.com/user-attachments/assets/5133c219-dc5f-4a57-b5ae-5fea3ebd4498" />
 
## Behavioral Simulation Waveform
<img width="1426" height="715" alt="image" src="https://github.com/user-attachments/assets/f3db6cd3-417f-49b5-84a1-e192e434307b" />

    
    

 
