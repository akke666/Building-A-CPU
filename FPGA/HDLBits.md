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

