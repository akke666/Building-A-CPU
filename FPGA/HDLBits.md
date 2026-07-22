# Verilog Language
## Basics
### Declareing wires
#### Goal:
<img width="620" height="264" alt="image" src="https://github.com/user-attachments/assets/bbf74985-b4d5-4624-9505-8712f5b9b6d2" />
#### Code:
```Verilog
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
    wire ornot;
    assign andor1=a & b;
    assign andor2=c & d;
    assign out=andor1 | andor2;
    assign out_n=~out;
endmodule
```
