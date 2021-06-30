
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

# Day-2 

Timing libs, hierarchical vs flat synthesis and efficient flop coding styles

On Day 1 we understood that library contains all standard cells or basic digital modules which can be used to synthesize any given HDL code. Today we are going to view what is there inside the library file and we will also understand the significance of nomenclature of lib file.
Open the lib file using gvim command by specifying the relative path or going to that folder and open that to view.

![alt text](https://github.com/jyotikedia-photonics/RTL_DESIGN_WORKSHOP/blob/main/Figures/10.PNG)

The window that opens is

![alt text](https://github.com/jyotikedia-photonics/RTL_DESIGN_WORKSHOP/blob/main/Figures/11.PNG)

The first line in library specifies its name:
library ("sky130_fd_sc_hd__tt_025C_1v80"). Looking at a library file, three words coming into picture
P: Process
V: voltage
T: temperature


- First of all, one should not edit this file.
   The library is created to model the variation possible in circuits due to process, voltage or temperature. The circuit behaviour is          different when it is fabricated at different time, when there is different voltage or when temperature is different. So the design           libraries develop their model to count upon all such variations in the circuit to model it as close to an actual circuit. 
- The library file tells the technology, delay, power and area. Each logical cell has different versions with low power, medium power or high   power, fast or slow etc. this is because circuits require all variety of gates or modules to design the circuits as per the specifications.
- So this is all about the library file which we can understand better if you look at it carefully. 
- Next we're going to see that how we can synthesise a top level entity when we give command Synth- top. We are also going to see that if we    have a hierarchical design that is using various other modules as a part of it that is if a design is instantiating a module of other        block or other design then how we can synthesise it as a black box and we can go deep into the circuit by flattening it and going to the      circuit level off the individual blocks included in the top most entity.
- So we can see in the screenshot back the multiple module is instantiating two sub modules sub module one and 2 as a part of it and it is      mapping its own signals to those of the sub modules. So let us see when we synthesise this circuit what do we get.

![alt text](https://github.com/jyotikedia-photonics/RTL_DESIGN_WORKSHOP/blob/main/Figures/12.PNG)

![alt text](https://github.com/jyotikedia-photonics/RTL_DESIGN_WORKSHOP/blob/main/Figures/13.png)

![alt text](https://github.com/jyotikedia-photonics/RTL_DESIGN_WORKSHOP/blob/main/Figures/14.png)

![alt text](https://github.com/jyotikedia-photonics/RTL_DESIGN_WORKSHOP/blob/main/Figures/15.png)

![alt text](https://github.com/jyotikedia-photonics/RTL_DESIGN_WORKSHOP/blob/main/Figures/16.png)

It is not showing the actual gates but is showing the names as sub module 1 and submodule 2. It is showing a hierarchy as the multiple modules has instantiated submodule 1 and 2. Also we can see at the net list back to sub-modules are instantiated inside the design multiple modules.

![alt text](https://github.com/jyotikedia-photonics/RTL_DESIGN_WORKSHOP/blob/main/Figures/17.png)

Now If we want to look at that what is there inside the sub modules we can do that by running command flatten. during synthesis if we use flatten we can see in the netlist that as compared to the hierarchical design net list there are no sub modules shown but only the lowest level circuit is listed there. We can also see in the circuit diagram that we get after synthesis, that it is no more showing sub module as the black boxes but it is showing the proper gates which were there inside the sub modules.

![alt text](https://github.com/jyotikedia-photonics/RTL_DESIGN_WORKSHOP/blob/main/Figures/18.png)

![alt text](https://github.com/jyotikedia-photonics/RTL_DESIGN_WORKSHOP/blob/main/Figures/19.png)

![alt text](https://github.com/jyotikedia-photonics/RTL_DESIGN_WORKSHOP/blob/main/Figures/20.png)

## FLIP FLOPS 
- Let us look at the need of the flip flops in digital circuits. Whenever we design a combinational circuit the outputs are evaluated as soon as whenever there is a change in the input. So due to the delays that is propagation delay across the various gates sometimes the correct outputs are not evaluated because intermediate values propagate or reach to their final value only after the propagation delay and during that time if those intermediate values are used by the other gates cascaded then those cascaded gates are going to evaluate a wrong output for sometime. Although finally they will be reaching their exact or the correct value but momentarily the output of the combinational gates will be incorrect. This is known as glitch in order to avoid this glitching which may result into an altogether incorrect output when we have a series of cascaded gates we can use a storage element in between these cascaded combinations which can hold onto their previous value for sometime.
- So in this session we're going to look at the designs of D flip flop with various combinations of synchronous or asynchronous set or reset inputs. The set or reset inputs are nothing but the inputs which are used to initialize the flops.

# ASYNCHRONOUS RESET
Here is an example of a D flip flop with asynchronous reset. Asynchronous reset means that output can be 0 whenever the reset input goes high irrespective of the clock pulse.

![alt text](https://github.com/jyotikedia-photonics/RTL_DESIGN_WORKSHOP/blob/main/Figures/21.png)

![alt text](https://github.com/jyotikedia-photonics/RTL_DESIGN_WORKSHOP/blob/main/Figures/22.png)

It is clearly visible in the above two wave forms that when reset is zero the output follows the input on the next clock pulse whenever it arrives but when reset input is high the output goes to zero irrespective of the clock pulse.

# ASYNCHRONOUS SET
Similarly we have next example in which there is an asynchronous set input that sets the output of  D flip flop to 1 whenever set input goes high. And if set input is low the output will follow the input on the next clock pulse arrival.

![alt text](https://github.com/jyotikedia-photonics/RTL_DESIGN_WORKSHOP/blob/main/Figures/23.png)

![alt text](https://github.com/jyotikedia-photonics/RTL_DESIGN_WORKSHOP/blob/main/Figures/24.png)

# SYNCHRONOUS RESET
This is the example of synchronous reset. What happens here is that whenever reset goes to 1 the output goes to zero only when the new clock arrives since this reset input is synchronized with the clock. And further when this reset input goes low output will follow the input again on the next clock pulse arrival.

![alt text](https://github.com/jyotikedia-photonics/RTL_DESIGN_WORKSHOP/blob/main/Figures/25.png)

![alt text](https://github.com/jyotikedia-photonics/RTL_DESIGN_WORKSHOP/blob/main/Figures/26.png)

# And in the next few snapshots we can see the synthesizer circuit of the flip flops with asynchronous/synchronous set or reset
SYNTHESIS OF ASYNCHRONOUS FLIP FLOP

![alt text](https://github.com/jyotikedia-photonics/RTL_DESIGN_WORKSHOP/blob/main/Figures/27.png)

**ASYNCHRONOUS SET**
![alt text](https://github.com/jyotikedia-photonics/RTL_DESIGN_WORKSHOP/blob/main/Figures/28.png)

**SYNCHRONOUS RESET**
![alt text](https://github.com/jyotikedia-photonics/RTL_DESIGN_WORKSHOP/blob/main/Figures/29.png)

# OPTIMIZATION
Now let us look at few interesting optimizations in the design. Although the detailed sequential and combinational optimizations are shown in the next session. But here we see very commonly used and interesting optimizations. For example let us say we want to multiply a given 3 bit number buy two. If we write down the truth table showing input as a 3 bit number and an output as a multiple of input number by 2. We will observe that output is having it's 3 most significant bids same as that of the input and the LSB is zero throughout. this means that we need not to have any circuitry to multiply a given number by two rather we can just copy the input number and append a zero as a LSB. so this kind of optimization can lead to a great reduction of this circuit which is anticipated while writing a code.

   module mul2 (input [2:0] a, output [3:0] y);
      assign y = a * 2;
   endmodule

![alt text](https://github.com/jyotikedia-photonics/RTL_DESIGN_WORKSHOP/blob/main/Figures/30.png)

![alt text](https://github.com/jyotikedia-photonics/RTL_DESIGN_WORKSHOP/blob/main/Figures/31.png)

**Netlist**
![alt text](https://github.com/jyotikedia-photonics/RTL_DESIGN_WORKSHOP/blob/main/Figures/32.png)

So like we can see in the synthesised circuit and the generated netlist that there is no circuit at all but the input is directly going as output and a zero is appended at the rightmost bit. The same thing can also be verified in the netlist generated.

# DAY-3
## COMBINATIONAL AND SEQUENTIAL OPTIMIZATIONS
As we know we have two types of circuits in digital logic design one is combinational and other is sequential so whenever we design any circuit in VLSI we always look for where we can design our circuit optimising on area and power so that is why whenever we are making and RTL design we need to optimise
The techniques of combinational optimisation:
1. constant propagation 
Direct Optimisation technique 
2. Boolean logic Optimisation : a more efficient simplified Boolean logic expression using techniques like 
K map 
Quin McCluskey algorithms

So let us take the first example. As it can be seen from the verilog code that it is trying to design a two input mux in which output why will be assigned the value be when a input is 1. And output will get a value of zero if a input is zero. What is expected out of the code is as shown in the diagram below. But when we analyze it we find that the boolean expression for Y is
Y= ab+a’0
If you look at the boolean expression carefully we can see that the second term becomes zero and what we are left with is Y is equal to a and b. it means that we can realise or synthesise the given code only using an and gate instead of a multiplexer. Let us check this optimization using our simulator and synthesiser.
This optimization can be done using the following command:
opt_clean -purge

![alt text](https://github.com/jyotikedia-photonics/RTL_DESIGN_WORKSHOP/blob/main/Figures/33.png)

![alt text](https://github.com/jyotikedia-photonics/RTL_DESIGN_WORKSHOP/blob/main/Figures/34.png)

![alt text](https://github.com/jyotikedia-photonics/RTL_DESIGN_WORKSHOP/blob/main/Figures/35.PNG)

![alt text](https://github.com/jyotikedia-photonics/RTL_DESIGN_WORKSHOP/blob/main/Figures/36.png)

- So it can be clearly seen in the synthesizer circuit that it is not a two input multiplexer but the design can be realised only using an AND gate.

- Here is another example optimization check. As we can see again from the code, hello let it can be two cascaded multiplexers having control input as A and B. The circuit that is expected is as follows


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
