# ICDC2019_grad_cell_based

## Description

This is a project for 2019 ic design contest graduation group, which implements an IoT Data Filter (IOTDF) that can process large IoT data from the sensors, and output the result in real-time.
<p align="center">
<img src="https://github.com/Howard-Liang/ICDC2019_grad_cell_based/blob/main/image/iotdf.PNG" width=40% height=40%>
</p>

## Block Diagram

<p align="center">
<img src="https://github.com/Howard-Liang/ICDC2019_grad_cell_based/blob/main/image/iotdf_block.PNG" width=40% height=40%>
</p>

Top module: IOTDF.v

## Clock Gating

Clock gating is used in this project.  
To do so, replace clk with other gated clock signal in the sequential block of RTL code.  
For example:
```
assign gclk = clk & enable;
always @ (posedge gclk or negedge rst_n) begin
```
When synthesizing the circuit, replace_clock_gates instruction should be placed before compile instruction.  
For example:
```
replace_clock_gates
compile_ultra
```
After compiling, you can check the gating result with the report command:
```
report_clock_gating -gating_elements
```

## Executing Program

A testbench code (./testfixture.v) and several golden data were provided by the contest host.  
The RTL behavior of the chip can be simulated by using the following command: 
```
$ source runall_rtl
```
To see the simulated wave form, use nWave
```
$ nWave &
```
to read the fsdb files generated by ncverilog.  

The gate-level circuit can be tested by using the following command:
```
$ source runall_syn
```

## ICD Contest Host
For more information, please download the spec and problem description at:  
http://icdc.ntust.edu.tw/2022/index2.php?page=OldExams

## Authors

Contributors names and contact info

Hao-Wei, Liang (b07502022@ntu.edu.tw) 

