# Led_Run
## Function:

## Code:
``` Verilog
module Led_run(
input clk,
input reset_n,
output reg [7:0]Led
    );
    reg [25:0] counter;
    always @(posedge clk or negedge reset_n)
        if (!reset_n)
            counter<=0;
        else if(counter==25000000-1)
            counter<=0;
        else
            counter <=counter +1;
            
    always @(posedge clk or negedge reset_n)
        if (!reset_n)
           Led=8'b0000_0001;
        else if (counter==25000000-1)begin
            if ((Led==8'b1000_0000)|Led==8'b0000_0000)
                Led<=8'b0000_0001;
        else
            Led<=Led<<1;
        end
            
endmodule
```
testbench, schematic... will upload tmr.
