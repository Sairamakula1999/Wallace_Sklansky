# Wallace_Sklansky
4x4 Wallace tree multiplier using Sklansky
## Table of Contents

- [Introduction](https://github.com/Sairamakula1999/Wallace_Sklansky/blob/main/README.md#introduction)
- [Circuit Design](https://github.com/Sairamakula1999/Wallace_Sklansky/blob/main/README.md#Circuit-Design)
- [Circuit Implementation](https://github.com/Sairamakula1999/Wallace_Sklansky/blob/main/README.md#Circuit-Implementation)
- [Simulation Results](https://github.com/Sairamakula1999/Wallace_Sklansky/blob/main/README.md#simulation-results)
- [Conclusion](https://github.com/Sairamakula1999/Wallace_Sklansky/blob/main/README.md#conclusion)
- [Author](https://github.com/Sairamakula1999/Wallace_Sklansky/blob/main/README.md#author) 
- [Acknowledgements](https://github.com/Sairamakula1999/Wallace_Sklansky/blob/main/README.md#acknowledgements)
- [References](https://github.com/Sairamakula1999/Wallace_Sklansky/blob/main/README.md#references)

## Introduction
In high performance processing units & computing systems, multiplication of two binary numbers is primitive and most frequently used arithmetic operation. Wallace tree multiplier is area efficient & high speed multiplier. This paper, we are also using Sklansky parallel prefix adder to speed up the circuit. The design has been created on Synopsis [Custom Compiler](https://www.synopsys.com/implementation-and-signoff/custom-design-platform/custom-compiler.html) software and simulated using [PrimeWave](https://www.synopsys.com/implementation-and-signoff/ams-simulation/primewave.html) environment. 

<p align="center">
<img src="images/Wallace-Tree-Multiplier-using-full-and-half-adders.png" width =400 height= 400>
</p>
<p align="center">
Fig 1. conventional wallace multplier
</p>

## Circuit Design
In this instead of approaching a circuit in a conventional  manner, every alternate stages are inverted to remove extraneous inverters which saves area by a lot and use of sklansky increases performance of circuit by a lot. So, in this we have tried to get best of both worlds like min area by decreasing no. transistors and less propagation delay by wallace with sklansky parallel prefix adder.

Partial products are generated using nand gates which decreased no.of transistors required by a lot. Using conventional and gate we may require 6(transistors for a single and gate) x 16(partial products)= 96 transistors. but in our approach we may require 16(partial products) x  nand(4 transistors) + inverter(2 transistors) x 5(inverted since they are used for not the first stage after partial products but for a second stage. So, one has to make them inverted again to maintain polarity) = 74 transistors. So nearly 22 transistors save in this stage only.
<p align="center">
<img src="images/kk.png" width =400 height= 500>
</p>
<p align="center">
Fig 2. partial products
</p>

Ripple sum and carry adder is used as it also inverts the Sum and carry each stage. If inverted inputs are given to this adder we get correct sum and carry and vice-versa.
Total 5x full adder(24 transistors)= 120 transistors.
<p align="center">
<img src="images/cs.png">
</p>
<p align="center">
Fig 3. full adder
</p>

for half carry adder xor and nand gates in odd stage, xor and nor in even stage. since in both carry is taken from nand/ nor i.e. 2 transistors are saved per each carry. 3 x half adder(xor(12 transistors) + carry(4 transistors for nand/ nor))= 48 transistors.
<p align="center">
<img src="images/h_o.png">
<img src="images/h_e.png">
</p>
<p align="center">
Fig 4. half adder
</p>

Instead of using ripple carry adder Sklansky adder is used to reduce propagation delay and  and improve speed of circuit at the final stage and based on even or odd stage, grey and black cell used may be varied to remove extraneous inverters but if even-even or odd-odd stage connection requires inverters to be added in between them to maintain the polarity and maintain functioning. Since, pg generated in even stage xor and nor are used. if it is generated in odd stage xor and nand can be used. Total transistors for pg generation  4 x pg generation(p(12 transistors for xor) + g(4 transistors for nand/ nor))= 64 transistors. 1 x black cell(10 transistors) + 3 x grey cell(6 transistors) + 2x inverters(2 transistors) + 3 x xor gates(12 transistors)= 68 transistors. Total transistor in this sklansky stage= 64+68= 132 transistors.
<p align="center" >
<img src="images/sk.png" width =400 height= 500>
</p>
<p align="center">
Fig 5. sklanasky adder
</p>
<p align="center" >
<img src="images/g.png" >
</p>
<p align="center">
Fig 6. black and grey cell
</p>

## Circuit Implementation

inv implementation
<p align="center" >
<img src="images/inv.png" width =300 height= 300>
</p>
<p align="center">
Fig 7. inverter
</p>

nand implementation
<p align="center" >
<img src="images/nand.png" width =400 height= 400>
</p>
<p align="center">
Fig 8. nand
</p>

nor implementation
<p align="center" >
<img src="images/nor.png" width =400 height= 400>
</p>
<p align="center">
Fig 9. nor
</p>

xor implementation
<p align="center" >
<img src="images/xor.png" width =500 height= 500>
</p>
<p align="center">
Fig 10. xor
</p>

sum implementation
<p align="center" >
<img src="images/sum.png" width =600 height= 400>
</p>
<p align="center">
Fig 11. sum
</p>

grey cell implementation
<p align="center" >
<img src="images/grey_e.png" width =400 height= 400>
<img src="images/grey_o.png" width =400 height= 400>
</p>
<p align="center">
Fig 12. grey cells for even and odd stages
</p>

black cell implementation
Since only one stage in black. So, it is created for only even stage.
<p align="center">
<img src="images/black.png" width =300 height= 300>
</p>
<p align="center">
Fig 13. black
</p>

<p align="center">
<img src="images/ckt.png" width =600 height= 400>
</p>
<p align="center">
Fig 14. Designed 4x4 wallace sklansky tree multiplier.
</p>

## Simulation results

<p align="center">
<img src="images/ckt_sim.png" width =700 height= 300>
</p>
<p align="center">
Fig 15. ckt used for simulation
</p>

<p align="center">
<img src="images/sim.png" width =1000 height= 500>
</p>
<p align="center">
Fig 16. Simulation results
</p>

As one can observe for inputs all one(i.e 1.8v) which gives A=15 & B=15, we gout output (1000111)= 1+32+64+128=225(15x15). So, our results are evaluated one can check similarly with other inputs in simulation and intially all inputs are one unless they are changed. So, one may observe output accordingly. 






## More changes to be done till March 1st So please wait till then to evaluate
