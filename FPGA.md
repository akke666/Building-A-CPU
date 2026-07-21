#FPGA
Here is my progress of study Verilog<br>
##Mux2
###Code:
module mux2(<br>
    a,<br>
    b,<br>
    sel,<br>
    out);<br>
    input a;<br>
    input b;<br>
    input sel;<br>
    output out;<br>
    assign out= (sel==0)? a:b;<br>
endmodule<br>
