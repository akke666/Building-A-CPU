# Mux2
## Function:
Toggles between 2 values
## Code:
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
## RTL Schematic:
<img width="1484" height="610" alt="image" src="https://github.com/user-attachments/assets/221d385d-1e0e-48ad-9fe7-05f76fabe9a4" />
## Behavioral Simulation Waveform
<img width="1093" height="400" alt="image" src="https://github.com/user-attachments/assets/acf517b7-4915-49da-b9e3-964e87e3f13b" />

