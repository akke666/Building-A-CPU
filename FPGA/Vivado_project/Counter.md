# Counter
## Function：
Toggles the LED output after counting a specific number of clock cycles based on a 25-bit register.
## Code:

```Verilog
module blink(
    input clk,
    input reset,
    
    output reg LED
);
   reg [24:0]count;
always @(posedge clk or negedge reset)
    begin

    if (!reset)
        count <= 0;
    else if (count ==25000000-1)
        count <= 0;
    else
        count <= count + 1;
    end
always @(posedge clk or negedge reset)
    begin
        if (!reset)
            LED <= 0;
        else if (count == 25000000-1)
            LED <= ~LED;
    end
endmodule
```

## Testbench
```Verilog
`timescale 1ns/1ns
module blink_tb();
    reg clk;
    reg reset;
    wire LED;
    
    blink blink(
         .clk(clk),
         .reset(reset),    
         .LED(LED)
    );
    
    initial clk=1;
    always #10 clk=!clk;
    
    initial begin
        reset=0;
        #201;
        reset=1;
        #2000000000;
        $stop;
    end
endmodule
```
## Schematic
<img width="1673" height="318" alt="image" src="https://github.com/user-attachments/assets/0053be13-7b77-4204-8e32-8357b3ecf4fa" />

## Behavioral Simulation Waveform
<img width="1909" height="957" alt="image" src="https://github.com/user-attachments/assets/1cdcb5b1-177a-4bbc-b8f0-51d5c146e291" />
