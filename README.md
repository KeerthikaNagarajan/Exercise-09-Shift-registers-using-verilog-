
# Experiment--09-Implementation-of Shift-registers-using-verilog-

### AIM:
To implement PISO , PIPO, SIPO using verilog and validating their functionality using their functional tables

### HARDWARE REQUIRED:   
PC, Cyclone II , USB flasher

### SOFTWARE REQUIRED:   
Quartus prime

### THEORY 
Shift registers are basically of 4 types. These are:

Serial In Serial Out shift register
Serial In parallel Out shift register
Parallel In Serial Out shift register
Parallel In parallel Out shift register
Serial-In Serial-Out Shift Register (SISO) –
The shift register, which allows serial input (one bit after the other through a single data line) and produces a serial output is known as Serial-In Serial-Out shift register. Since there is only one output, the data leaves the shift register one bit at a time in a serial pattern, thus the name Serial-In Serial-Out Shift Register.

The logic circuit given below shows a serial-in serial-out shift register. The circuit consists of four D flip-flops which are connected in a serial manner. All these flip-flops are synchronous with each other since the same clock signal is applied to each flip flop.

![image](https://user-images.githubusercontent.com/36288975/172337366-540cc45e-11fe-4cce-9503-560dc704bc7d.png)
FIGURE -01 
erial-In Parallel-Out shift Register (SIPO) –
The shift register, which allows serial input (one bit after the other through a single data line) and produces a parallel output is known as Serial-In Parallel-Out shift register.

The logic circuit given below shows a serial-in-parallel-out shift register. The circuit consists of four D flip-flops which are connected. The clear (CLR) signal is connected in addition to the clock signal to all the 4 flip flops in order to RESET them. The output of the first flip flop is connected to the input of the next flip flop and so on. All these flip-flops are synchronous with each other since the same clock signal is applied to each flip flop.

![image](https://user-images.githubusercontent.com/36288975/172337438-03416c7e-7c9d-4939-ba34-c355b9fc79c5.png)
FIGURE-02
The above circuit is an example of shift right register, taking the serial data input from the left side of the flip flop and producing a parallel output. They are used in communication lines where demultiplexing of a data line into several parallel lines is required because the main use of the SIPO register is to convert serial data into parallel data.
Parallel-In Serial-Out Shift Register (PISO) –
The shift register, which allows parallel input (data is given separately to each flip flop and in a simultaneous manner) and produces a serial output is known as Parallel-In Serial-Out shift register.

The logic circuit given below shows a parallel-in-serial-out shift register. The circuit consists of four D flip-flops which are connected. The clock input is directly connected to all the flip flops but the input data is connected individually to each flip flop through a multiplexer at the input of every flip flop. The output of the previous flip flop and parallel data input are connected to the input of the MUX and the output of MUX is connected to the next flip flop. All these flip-flops are synchronous with each other since the same clock signal is applied to each flip flop.
![image](https://user-images.githubusercontent.com/36288975/172337544-1632407f-1743-4b17-b480-00663d01e59f.png)
FIGURE-03
A Parallel in Serial out (PISO) shift register us used to convert parallel data to serial data.

Parallel-In Parallel-Out Shift Register (PIPO) –
The shift register, which allows parallel input (data is given separately to each flip flop and in a simultaneous manner) and also produces a parallel output is known as Parallel-In parallel-Out shift register.

The logic circuit given below shows a parallel-in-parallel-out shift register. The circuit consists of four D flip-flops which are connected. The clear (CLR) signal and clock signals are connected to all the 4 flip flops. In this type of register, there are no interconnections between the individual flip-flops since no serial shifting of the data is required. Data is given as input separately for each flip flop and in the same way, output also collected individually from each flip flop![image](https://user-images.githubusercontent.com/36288975/172337661-babb1f90-6286-4d14-8cbd-26a380ee085e.png)
FIGURE-04
A Parallel in Parallel out (PIPO) shift register is used as a temporary storage device and like SISO Shift register it acts as a delay element.

### Procedure:
```
1.Use quartus software and import required modules.

2.Assign inputs and outputs for shift registers.

3.Assign logic for input to give output at positive edge.

4.Perform opertaions and produce rtl circuit.

5.End module
```

### PROGRAM:
```
Program for  Implementation-of Shift-registers-using-verilog-
Developed by: Keerthika N
RegisterNumber: 212221230049
```

## Serial Input Parallel Output (SIPO):
```
module sipo(SI,CLK,Po);
input SI,CLK;
output[0:7]Po;
reg[0:7]temp;
always@(posedge CLK)
begin
temp={temp[0:6],SI};
end
assign Po=temp;
endmodule
```

### RTL LOGIC  REGISTERS:
<img width="641" alt="siportl" src="https://user-images.githubusercontent.com/93427089/172893707-adf988b7-ef92-48d9-bb79-02a3eac5b8d8.png">

### TIMING DIGRAMS FOR SHIFT REGISTERS:
![sipotiming](https://user-images.githubusercontent.com/93427089/172898210-f5f67b7d-4e58-4bda-b989-356d4b74a1e6.png)


## Parallel Input Serial Output (PISO):
```
module piso(Clk, Parallel_In,load, Serial_Out);
input Clk,load;
input [3:0]Parallel_In;
output reg Serial_Out;
reg [3:0]tmp;
always @(posedge Clk)
begin
if(load)
tmp<=Parallel_In;
else
begin
Serial_Out<=tmp[3];
tmp<={tmp[2:0],1'b0};
end
end
endmodule
```

### RTL LOGIC  REGISTERS:  
<img width="511" alt="pisortl" src="https://user-images.githubusercontent.com/93427089/172893791-5a098637-e28d-4cfb-ae80-d8a2bdf36273.png">

### TIMING DIGRAMS FOR SHIFT REGISTERS:
<img width="843" alt="pisow" src="https://user-images.githubusercontent.com/93427089/172893844-f76d572e-b0b3-4956-8f4e-c8c46af94afe.png">

## Parallel Input Parallel Output (PIPO):
```
module pipo(PIn,CLK,Po);
input CLK;
input[3:0]PIn;
output reg[3:0]Po;
always@(posedge CLK)
begin
Po=PIn;
end
endmodule
```

### RTL LOGIC  REGISTERS:
<img width="734" alt="pipo rtl" src="https://user-images.githubusercontent.com/93427089/172893876-e16c025e-3f9f-47e7-98fc-55147736d83f.png">

### TIMING DIGRAMS FOR SHIFT REGISTERS:
<img width="932" alt="pipo wave" src="https://user-images.githubusercontent.com/93427089/172893905-39c28b1b-b7f4-4ae5-9648-e00200011255.png">

### RESULTS:
Thus, PISO , PIPO, SIPO are implemented using verilog and their functionality using their functional tables is validated.

