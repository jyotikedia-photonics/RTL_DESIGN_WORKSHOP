
# RTL Design using Verilog with SKY130 Technology
![alt text](https://github.com/jyotikedia-photonics/RTL_DESIGN_WORKSHOP/blob/main/Figures/1.png)
Organized By [VSD DESIGN](https://github.com/kunalg123)


## Know About Me

![alt text](https://github.com/NANOPHOTONIC-RESEARCH-SOCIETY-AT-PEC/STC_on_Integrated_Optics/blob/main/Guest%20Speakers/Dr%20Kedia.PNG)

[Dr JYOTI KEDIA](https://pec.ac.in/jyoti-kedia)

**(Assistant Professor @PEC(Deemed to be university)**

# Table of Contents

- [Day 1.](#Day-1)
- [Day 2.](#Day-2)
- [Day 3.](#Day-1)
- [Day 4.](#Day-1)
- [Day 5.](#Day-1)


# Day-1
## Introduction to Verilog RTL design and Synthesis

As we all know hardware description languages are used to design, simulate and synthesize the digital electronic circuits. Any HDL simulator looks for changes on input. Whenever there is a change in primary inputs, the output is evaluated. If there is no change in input, then no output will be evaluated. So any design has primary inputs and primary outputs.
However, a test bench has no primary inputs and outputs. A test bench is used to check that whether the design behaves as expected or not. It has a stimulus generator corresponding to all input combinations for primary inputs of design and has a stimulus observer that observes the expected output collected from primary outputs of the design. 

![alt text](https://github.com/jyotikedia-photonics/RTL_DESIGN_WORKSHOP/blob/main/Figures/2.png)

In this workshop SKY130 technology and iverilog software tool has been used to compile, simulate and synthesize Verilog codes. Following is the iverilog process flow:

![alt text](https://github.com/jyotikedia-photonics/RTL_DESIGN_WORKSHOP/blob/main/Figures/3.png)

We can see that in iverilog process flow, the design code and its test bench is given as input file which generates a VCD file (Value change dump format) file on simulation. And then using gtkwave one can see the waveforms generated after simulation.

### VERILOG SIMULATION:
#### LAB SESSION:
##### Steps/commands:
- load the library for all standard cells of sky130 and Verilog models  files that contain all designs and test benches.
- This can be done using cloning a github repo using command:

   git clone link of repo

- Load Verilog design file and test bench using following command:

   iverilog good_mux.v tb_good_mux.v
   a.out file will be created which we need to execute using:
   ./a.out
- This will generate a VCD file which can be used to generate waveforms using gtkwave.
   gtkwave tb_good_mux.vcd
- The command to read the Verilog file and see or edit the code is:
   !gvim good_mux.v

**Screenshot showing step no. 3,4 and 5:**

![alt text](https://github.com/jyotikedia-photonics/RTL_DESIGN_WORKSHOP/blob/main/Figures/4.PNG)

**Screenshot showing waveforms of multiplexer:**

![alt text](https://github.com/jyotikedia-photonics/RTL_DESIGN_WORKSHOP/blob/main/Figures/5.PNG)

## SYNTHESIS:

A synthesizer converts RTL into netlist. The netlist is a representation of the design in terms of standard cells such as and, or, not gates. We have Yosys as a synthesizer tool. The flow of Yosys synthesizer is as follows:

![alt text](https://github.com/jyotikedia-photonics/RTL_DESIGN_WORKSHOP/blob/main/Figures/6.PNG)

## LAB SESSION:
### Steps/commands:
#### Read the library for all standard cells of sky130 using command:

   read_liberty -lib path of library
- Read the Verilog file which we want to synthesize using command:
   read_verilog good_mux.v
- Synthesize the top level entity in the given design using following command:
   synth -top good_mux 
- Generate the netlist using:
   abc -liberty path of library
- The netlist can be written in readable format and then read using 
   a) write_verilog -noattr good_mux_netlist.v
   b) !gvim good_mux_netlist.v
- At the end the circuit synthesized can be viewed using command:
   show

after synth command: shows statistics of how many number of blocks are there etc.

![alt text](https://github.com/jyotikedia-photonics/RTL_DESIGN_WORKSHOP/blob/main/Figures/7.PNG)

This is the synthesized circuit. As we can see it is a 2 input multiplexer mapped with inputs and outputs of our design.

![alt text](https://github.com/jyotikedia-photonics/RTL_DESIGN_WORKSHOP/blob/main/Figures/8.PNG)

This is the netlist generated:

![alt text](https://github.com/jyotikedia-photonics/RTL_DESIGN_WORKSHOP/blob/main/Figures/9.PNG)

# Day 2 

Timing libs, hierarchical vs flat synthesis and efficient flop coding styles

On Day 1 we understood that library contains all standard cells or basic digital modules which can be used to synthesize any given HDL code. Today we are going to view what is there inside the library file and we will also understand the significance of nomenclature of lib file.
Open the lib file using gvim command by specifying the relative path or going to that folder and open that to view.

![alt text](https://github.com/jyotikedia-photonics/RTL_DESIGN_WORKSHOP/blob/main/Figures/10.PNG)

![alt text](https://github.com/jyotikedia-photonics/RTL_DESIGN_WORKSHOP/blob/main/Figures/11.PNG)

![alt text](https://github.com/jyotikedia-photonics/RTL_DESIGN_WORKSHOP/blob/main/Figures/12.PNG)

![alt text](https://github.com/jyotikedia-photonics/RTL_DESIGN_WORKSHOP/blob/main/Figures/13.png)

![alt text](https://github.com/jyotikedia-photonics/RTL_DESIGN_WORKSHOP/blob/main/Figures/14.png)

![alt text](https://github.com/jyotikedia-photonics/RTL_DESIGN_WORKSHOP/blob/main/Figures/15.png)

![alt text](https://github.com/jyotikedia-photonics/RTL_DESIGN_WORKSHOP/blob/main/Figures/16.png)

![alt text](https://github.com/jyotikedia-photonics/RTL_DESIGN_WORKSHOP/blob/main/Figures/17.png)

![alt text](https://github.com/jyotikedia-photonics/RTL_DESIGN_WORKSHOP/blob/main/Figures/18.png)

![alt text](https://github.com/jyotikedia-photonics/RTL_DESIGN_WORKSHOP/blob/main/Figures/19.png)

![alt text](https://github.com/jyotikedia-photonics/RTL_DESIGN_WORKSHOP/blob/main/Figures/20.png)

![alt text](https://github.com/jyotikedia-photonics/RTL_DESIGN_WORKSHOP/blob/main/Figures/21.png)

![alt text](https://github.com/jyotikedia-photonics/RTL_DESIGN_WORKSHOP/blob/main/Figures/22.png)

![alt text](https://github.com/jyotikedia-photonics/RTL_DESIGN_WORKSHOP/blob/main/Figures/23.png)

![alt text](https://github.com/jyotikedia-photonics/RTL_DESIGN_WORKSHOP/blob/main/Figures/24.png)

![alt text](https://github.com/jyotikedia-photonics/RTL_DESIGN_WORKSHOP/blob/main/Figures/25.png)

![alt text](https://github.com/jyotikedia-photonics/RTL_DESIGN_WORKSHOP/blob/main/Figures/26.png)

![alt text](https://github.com/jyotikedia-photonics/RTL_DESIGN_WORKSHOP/blob/main/Figures/27.png)

![alt text](https://github.com/jyotikedia-photonics/RTL_DESIGN_WORKSHOP/blob/main/Figures/28.png)

![alt text](https://github.com/jyotikedia-photonics/RTL_DESIGN_WORKSHOP/blob/main/Figures/29.png)

![alt text](https://github.com/jyotikedia-photonics/RTL_DESIGN_WORKSHOP/blob/main/Figures/30.png)

![alt text](https://github.com/jyotikedia-photonics/RTL_DESIGN_WORKSHOP/blob/main/Figures/31.png)

![alt text](https://github.com/jyotikedia-photonics/RTL_DESIGN_WORKSHOP/blob/main/Figures/32.png)

![alt text](https://github.com/jyotikedia-photonics/RTL_DESIGN_WORKSHOP/blob/main/Figures/33.PNG)

![alt text](https://github.com/jyotikedia-photonics/RTL_DESIGN_WORKSHOP/blob/main/Figures/34.png)

![alt text](https://github.com/jyotikedia-photonics/RTL_DESIGN_WORKSHOP/blob/main/Figures/35.png)

![alt text](https://github.com/jyotikedia-photonics/RTL_DESIGN_WORKSHOP/blob/main/Figures/36.png)

![alt text](https://github.com/jyotikedia-photonics/RTL_DESIGN_WORKSHOP/blob/main/Figures/37.PNG)

![alt text](https://github.com/jyotikedia-photonics/RTL_DESIGN_WORKSHOP/blob/main/Figures/38.png)

![alt text](https://github.com/jyotikedia-photonics/RTL_DESIGN_WORKSHOP/blob/main/Figures/39.png)

![alt text](https://github.com/jyotikedia-photonics/RTL_DESIGN_WORKSHOP/blob/main/Figures/40.PNG)

![alt text](https://github.com/jyotikedia-photonics/RTL_DESIGN_WORKSHOP/blob/main/Figures/41.png)

![alt text](https://github.com/jyotikedia-photonics/RTL_DESIGN_WORKSHOP/blob/main/Figures/42.png)

![alt text](https://github.com/jyotikedia-photonics/RTL_DESIGN_WORKSHOP/blob/main/Figures/43.png)

![alt text](https://github.com/jyotikedia-photonics/RTL_DESIGN_WORKSHOP/blob/main/Figures/44.png)

![alt text](https://github.com/jyotikedia-photonics/RTL_DESIGN_WORKSHOP/blob/main/Figures/45.png)

![alt text](https://github.com/jyotikedia-photonics/RTL_DESIGN_WORKSHOP/blob/main/Figures/46.png)

![alt text](https://github.com/jyotikedia-photonics/RTL_DESIGN_WORKSHOP/blob/main/Figures/47.png)

![alt text](https://github.com/jyotikedia-photonics/RTL_DESIGN_WORKSHOP/blob/main/Figures/48.png)

![alt text](https://github.com/jyotikedia-photonics/RTL_DESIGN_WORKSHOP/blob/main/Figures/49.png)

![alt text](https://github.com/jyotikedia-photonics/RTL_DESIGN_WORKSHOP/blob/main/Figures/50.png)

![alt text](https://github.com/jyotikedia-photonics/RTL_DESIGN_WORKSHOP/blob/main/Figures/51.png)

![alt text](https://github.com/jyotikedia-photonics/RTL_DESIGN_WORKSHOP/blob/main/Figures/52.png)

![alt text](https://github.com/jyotikedia-photonics/RTL_DESIGN_WORKSHOP/blob/main/Figures/53.png)

![alt text](https://github.com/jyotikedia-photonics/RTL_DESIGN_WORKSHOP/blob/main/Figures/54.PNG)

![alt text](https://github.com/jyotikedia-photonics/RTL_DESIGN_WORKSHOP/blob/main/Figures/55.png)

![alt text](https://github.com/jyotikedia-photonics/RTL_DESIGN_WORKSHOP/blob/main/Figures/56.png)

![alt text](https://github.com/jyotikedia-photonics/RTL_DESIGN_WORKSHOP/blob/main/Figures/57.png)

![alt text](https://github.com/jyotikedia-photonics/RTL_DESIGN_WORKSHOP/blob/main/Figures/58.png)

![alt text](https://github.com/jyotikedia-photonics/RTL_DESIGN_WORKSHOP/blob/main/Figures/59.png)

![alt text](https://github.com/jyotikedia-photonics/RTL_DESIGN_WORKSHOP/blob/main/Figures/60.png)

![alt text](https://github.com/jyotikedia-photonics/RTL_DESIGN_WORKSHOP/blob/main/Figures/61.png)

![alt text](https://github.com/jyotikedia-photonics/RTL_DESIGN_WORKSHOP/blob/main/Figures/62.png)

![alt text](https://github.com/jyotikedia-photonics/RTL_DESIGN_WORKSHOP/blob/main/Figures/63.png)

![alt text](https://github.com/jyotikedia-photonics/RTL_DESIGN_WORKSHOP/blob/main/Figures/64.png)

![alt text](https://github.com/jyotikedia-photonics/RTL_DESIGN_WORKSHOP/blob/main/Figures/65.png)

![alt text](https://github.com/jyotikedia-photonics/RTL_DESIGN_WORKSHOP/blob/main/Figures/66.png)

![alt text](https://github.com/jyotikedia-photonics/RTL_DESIGN_WORKSHOP/blob/main/Figures/67.png)

![alt text](https://github.com/jyotikedia-photonics/RTL_DESIGN_WORKSHOP/blob/main/Figures/68.png)

![alt text](https://github.com/jyotikedia-photonics/RTL_DESIGN_WORKSHOP/blob/main/Figures/69.png)

![alt text](https://github.com/jyotikedia-photonics/RTL_DESIGN_WORKSHOP/blob/main/Figures/70.png)

![alt text](https://github.com/jyotikedia-photonics/RTL_DESIGN_WORKSHOP/blob/main/Figures/71.PNG)

![alt text](https://github.com/jyotikedia-photonics/RTL_DESIGN_WORKSHOP/blob/main/Figures/72.png)

![alt text](https://github.com/jyotikedia-photonics/RTL_DESIGN_WORKSHOP/blob/main/Figures/73.png)

![alt text](https://github.com/jyotikedia-photonics/RTL_DESIGN_WORKSHOP/blob/main/Figures/74.png)

![alt text](https://github.com/jyotikedia-photonics/RTL_DESIGN_WORKSHOP/blob/main/Figures/75.png)

![alt text](https://github.com/jyotikedia-photonics/RTL_DESIGN_WORKSHOP/blob/main/Figures/76.png)

![alt text](https://github.com/jyotikedia-photonics/RTL_DESIGN_WORKSHOP/blob/main/Figures/77.png)

![alt text](https://github.com/jyotikedia-photonics/RTL_DESIGN_WORKSHOP/blob/main/Figures/78.png)

![alt text](https://github.com/jyotikedia-photonics/RTL_DESIGN_WORKSHOP/blob/main/Figures/79.png)

![alt text](https://github.com/jyotikedia-photonics/RTL_DESIGN_WORKSHOP/blob/main/Figures/80.png)
