# SIMULATION AND IMPLEMENTATION OF MULTIPLIER
## AIM: 
 To simulate and synthesis multiplier using Xilinx ISE.

## APPARATUS REQUIRED:
Xilinx 14.7
Spartan6 FPGA
  
## PROCEDURE:
#### STEP:1  Start  the Xilinx navigator, Select and Name the New project.
#### STEP:2  Select the device family, device, package and speed.       
#### STEP:3  Select new source in the New Project and select Verilog Module as the Source type.                       
#### STEP:4  Type the File Name and Click Next and then finish button. Type the code and save it.
#### STEP:5  Select the Behavioral Simulation in the Source Window and click the check syntax.                       
#### STEP:6  Click the simulation to simulate the program and  give the inputs and verify the outputs as per the truth table.               
#### STEP:7  Select the Implementation in the Sources Window and select the required file in the Processes Window.
#### STEP:8  Select Check Syntax from the Synthesize  XST Process. Double Click in the  FloorplanArea/IO/Logic-Post Synthesis process in the User Constraints process group. UCF(User constraint File) is obtained. 
#### STEP:9  In the Design Object List Window, enter the pin location for each pin in the Loc column Select save from the File menu.
#### STEP:10 Double click on the Implement Design and double click on the Generate Programming File to create a bitstream of the design.(.v) file is converted into .bit file here.
#### STEP:11  On the board, by giving required input, the LEDs starts to glow light, indicating the output.

## Logic Diagram:
### 2 bit Multiplier

![image](https://github.com/navaneethans/VLSI-LAB-EXP-3/assets/6987778/7713750f-65e6-41c0-8082-5005eac4031c)
## Verilog code
## 2 bit Multiplier
```
module HalfAdder(a,b,sum,carry);
input a,b;
output sum,carry;
xor (sum,a,b);
and (carry,a,b);
endmodule
	
module Multiplier(a,b,y);
input [1:0]a,b;
output [3:0]y;
wire w1,w2,w3,w4;
and a1(y[0],a[0],b[0]);
and a2(w1,a[1],b[0]);
and a3(w2,a[0],b[1]);
and a4(w3,a[1],b[1]);
HalfAdder h0(w1,w2,y[1],w4);
HalfAdder h1(w3,w4,y[2],y[3]);
Endmodule
```


## Output Waveform
### 2 bit Multiplier:
![image](https://github.com/sowmithraramesh/VLSI-LAB-EXP-3/assets/166893766/ea76546f-1e61-431d-8335-27654e19091f)

## 4 Bit Multiplier
![image](https://github.com/navaneethans/VLSI-LAB-EXP-3/assets/6987778/d95215dd-8cf1-4e08-93cc-96adfdd7fbdc)

## 4 Bit Multiplier
```
module ha(s,c,a,b);
input a,b;
output s,c;
xor g1(s,a,b);
and g2(c,a,b);
endmodule

module fa(s,co,a,b,c);
input a,b,c;
output s,co;
wire w1,w2,w3;
xor g1(w1,a,b);
xor g2(s,w1,co);
and g3(w2,w1,c); 
and g4(w3,a,b);
or g5(co,w2,w3);
endmodule

module mul4(p,a,b);
input [3:0] a, b;
output [7:0] p;
wire [15:1] w;
wire [10:1] c;
wire [6:1] s;
and g1(p[0],a[0],b[0]);
and g2(w[1],a[1],b[0]);
and g3(w[2],a[2],b[0]);
and g4(w[3],a[3],b[0]);
and g5(w[4],a[0],b[1]);
and g6(w[5],a[1],b[1]);
and g7(w[6],a[2],b[1]);
and g8(w[7],a[3],b[1]);
and g9(w[8],a[0],b[2]);
and g10(w[9],a[1],b[2]);
and g11(w[10],a[2],b[2]);
and g12(w[11],a[3],b[2]);
and g13(w[12],a[0],b[3]);
and g14(w[13],a[1],b[3]);
and g15(w[14],a[2],b[3]);
and g16(w[15],a[3],b[3]);
ha ha1(p[1],c[1],w[4],w[1]);
fa fa1(s[1],c[2],w[5],w[2],c[1]);
fa fa2(s[2],c[3],w[6],w[3],c[2]);
ha ha2(s[3],c[4],w[7],c[3]);
ha ha3(p[2],c[5],w[8],s[1]);
fa fa3(s[4],c[6],s[2],w[9],c[5]);
fa fa4(s[5],c[7],s[3],w[10],c[6]);
fa fa5(s[6],c[8],c[4],w[11],c[7]);
ha ha4(p[3],c[9],w[12],s[4]);
fa fa6(p[4],c[10],w[13],s[5],c[9]);
fa fa7(p[5],c[11],w[14],s[6],c[10]);
fa fa8(p[6],p[7],w[15],c[8],c[11]);
endmodule

```

### 4 Bit Multiplier:
![image](https://github.com/sowmithraramesh/VLSI-LAB-EXP-3/assets/166893766/17bc9957-0c81-4dd2-a6cd-094c876bab6d)


## Result:
        Thus,The 2-bit multiplier and 4-bit multiplier implemented and stimulated successfully.



