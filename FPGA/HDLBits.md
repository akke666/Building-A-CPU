## About This Project
This repository contains my personal notes and Verilog solutions for exercises on **HDLBits**. 

### Copyright and Disclaimer
* **Problem Assets**: All problem descriptions, vector diagrams, and initial module declarations are the intellectual property of [HDLBits (01xz.net)](https://01xz.net).
* **Solutions**: The Verilog code implementations provided in this repository are written by me for personal learning, academic discussion, and reference purposes only.
* **Removal Request**: If you are the copyright owner and believe that any content in this repository infringes upon your rights, please open an issue or contact me, and I will remove the relevant material immediately.

# Verilog Language
## Basics
### Declareing wires
#### Goal:
<img width="620" height="264" alt="image" src="https://github.com/user-attachments/assets/bbf74985-b4d5-4624-9505-8712f5b9b6d2" /><br>
#### Code:

```verilog
`default_nettype none
module top_module(
    input a,
    input b,
    input c,
    input d,
    output out,
    output out_n   ); 
	wire andor1;
    wire andor2;
    assign andor1=a & b;
    assign andor2=c & d;
    assign out=andor1 | andor2;
    assign out_n=~out;
endmodule
```
### 7458
#### Goal:
<img width="723" height="428" alt="image" src="https://github.com/user-attachments/assets/8130876a-6212-4b67-89d1-1562414c8e8c" /><br>
#### Code:

```verilog
module top_module ( 
    input p1a, p1b, p1c, p1d, p1e, p1f,
    output p1y,
    input p2a, p2b, p2c, p2d,
    output p2y );
	wire a;
    wire b;
    wire c;
    wire d;
    assign a=p2a & p2b;
    assign b=p2c & p2d;
    assign p2y=a | b;
    assign c=p1c & p1b & p1a;
    assign d=p1f & p1e & p1d;
    assign p1y= c | d;

endmodule
```
## Vectors
### Vector0
#### Goal:
<img width="690" height="227" alt="image" src="https://github.com/user-attachments/assets/7ee3c443-504d-4ecf-81cf-14715db9fef8" />

#### Code:

```Verilog
module top_module ( 
    input wire [2:0] vec,
    output wire [2:0] outv,
    output wire o2,
    output wire o1,
    output wire o0  ); // Module body starts after module declaration
	assign outv=vec;
    assign o2=vec[2];
    assign o1=vec[1];
    assign o0=vec[0];
endmodule
```

