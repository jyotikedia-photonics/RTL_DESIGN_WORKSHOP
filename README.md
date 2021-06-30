
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

![alt text](https://github.com/jyotikedia-photonics/RTL_DESIGN_WORKSHOP/blob/main/Figures/4.PNG)

### VERILOG SIMULATION:
#### LAB SESSION:
##### Steps/commands:
- load the library for all standard cells of sky130 and Verilog models  files that contain all designs and test benches.
- This can be done using cloning a github repo using command:

   git clone link of repo

- Load Verilog design file and test bench using following command:

   iverilog good_mux.v tb_good_mux.v

![alt text](https://github.com/jyotikedia-photonics/RTL_DESIGN_WORKSHOP/blob/main/Figures/5.PNG)

![alt text](https://github.com/jyotikedia-photonics/RTL_DESIGN_WORKSHOP/blob/main/Figures/6.PNG)

![alt text](https://github.com/jyotikedia-photonics/RTL_DESIGN_WORKSHOP/blob/main/Figures/7.PNG)

![alt text](https://github.com/jyotikedia-photonics/RTL_DESIGN_WORKSHOP/blob/main/Figures/8.PNG)

![alt text](https://github.com/jyotikedia-photonics/RTL_DESIGN_WORKSHOP/blob/main/Figures/9.PNG)

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
