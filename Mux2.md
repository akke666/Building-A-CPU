# FPGA
Here is my progress of study Verilog<br>
## Mux2
### Code:
```Verilog
module mux2(
    a,
    b,
    sel,
    out);
    input a;
    input b;
    input sel;
    output out;
    assign out= (sel==0)? a:b;
endmodule
```
### Testbench:
```Verilog
`timescale 1ns/1ns
module mux2_tb();
reg S0;
reg S1;
reg S2;

wire mux_out;

mux2 mux2_inst0(
    .a(S0),
    .b(S1),
    .sel(S2),
    .out(mux_out));
    
initial begin
    S2=0; S1=0; S0=0;
    #20;
    S2=1; S1=0; S0=0;
    #20;
    S2=1; S1=1; S0=0;
    #20;
    S2=1; S1=1; S0=1;
    #20;
    S2=0; S1=1; S0=0;
    #20;
    S2=0; S1=1; S0=1;
    #20;
    S2=0; S1=0; S0=1;
    #20;
    S2=1; S1=0; S0=1;
    #20;
end
endmodule
```
