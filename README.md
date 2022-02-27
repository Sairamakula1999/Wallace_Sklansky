# Wallace_Sklansky
4x4 Wallace tree multiplier using Sklansky
## Table of Contents

- [Introduction](https://github.com/Sairamakula1999/Wallace_Sklansky/blob/main/README.md#introduction)
- [Circuit Design](https://github.com/Sairamakula1999/Wallace_Sklansky/blob/main/README.md#Circuit%20design)
- [Circuit Implementation](https://github.com/Sairamakula1999/Wallace_Sklansky/blob/main/README.md#Circuit%20Implementation)
- [Simulation Results](https://github.com/Sairamakula1999/Wallace_Sklansky/blob/main/README.md#simulation-results)
- [Performance Comparison](https://github.com/Sairamakula1999/Wallace_Sklansky/blob/main/README.md#performance-comparison)
- [Conclusion](https://github.com/Sairamakula1999/Wallace_Sklansky/blob/main/README.md#conclusion)
- [Author](https://github.com/Sairamakula1999/Wallace_Sklansky/blob/main/README.md#author) 
- [Acknowledgements](https://github.com/Sairamakula1999/Wallace_Sklansky/blob/main/README.md#acknowledgements)
- [References](https://github.com/Sairamakula1999/Wallace_Sklansky/blob/main/README.md#references)

## Introduction
In high performance processing units & computing systems, multiplication of two binary numbers is primitive and most frequently used arithmetic operation. Wallace tree multiplier is area efficient & high speed multiplier. This paper, we are also using Sklansky parallel prefix adder to speed up the circuit. The design has been created on Synopsis [Custom Compiler](https://www.synopsys.com/implementation-and-signoff/custom-design-platform/custom-compiler.html) software and simulated using [PrimeWave](https://www.synopsys.com/implementation-and-signoff/ams-simulation/primewave.html) environment. 

<p align="center">
<img src="images/Wallace-Tree-Multiplier-using-full-and-half-adders.png">
</p>
<p align="center">
Fig 1. conventional wallace multplier
</p>

## Circuit design
In this instead of approaching a circuit in a conventional  manner, every alternate stages are inverted to remove extraneous inverters which saves area by a lot and use of sklansky increases performance of circuit by a lot. So, in this we have tried to get best of both worlds like min area by decreasing no. transistors and less propagation delay by wallace with sklansky parallel prefix adder.

Partial products are generated using nand gates which decreased no.of transistors required by a lot. Using conventional and gate we may require 6(transistors for a single and gate) x 16(partial products)= 96 g. but in our approach we may require 4(transistors for a single nand gate) x 16(partial products) + 2(transistors for an inverter) x 5( inverted since they are used for not the first stage after partial products but for a second stage. So, one has to make them inverted again to get required output) = 74 gates  
<p align="center">
<img src="images/kk.png" width =400 height= 400>
</p>
<p align="center">
Fig 2. partial products
</p>

Ripple sum and carry adder is used as it also inverts the Sum and carry each stage. If inverted inputs are given to this adder we get correct sum and carry and vice-versa.
<p align="center">
<img src="images/cs.png">
</p>
<p align="center">
Fig 3. full adder
</p>

for half carry adder xor and nand gates in odd stage and xor and nor in even stage.
<p align="center">
<img src="images/h_o.png">
<img src="images/h_e.png">
</p>
<p align="center">
Fig 4. half adder
</p>

Instead of using ripple carry adder Sklansky adder is used to reduce propagation delay and  and improve speed of circuit at the final stage and based on even or odd stage, grey and black cell used may be varied to remove extraneous inverters.
<p align="center" >
<img src="images/sk.png" width =400 height= 400>
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
<img src="images/inv.png" >
</p>
<p align="center">
Fig 7. inverter
</p>
nand implementation
<p align="center" >
<img src="images/nand.png" >
</p>
<p align="center">
Fig 8. nand
</p>
nor implementation
<p align="center" >
<img src="images/nor.png" >
</p>
<p align="center">
Fig 9. nor
</p>
xor implementation
nor implementation
<p align="center" >
<img src="images/xor.png" >
</p>
<p align="center">
Fig 10. xor
</p>
sum implementation
nor implementation
<p align="center" >
<img src="images/sum.png" >
</p>
<p align="center">
Fig 11. sum
</p>
grey cell implementation
nor implementation
<p align="center" >
<img src="images/grey_e.png" >
<img src="images/grey_o.png" >
</p>
<p align="center">
Fig 12. grey
</p>
black cell implementation
<p align="center">
<img src="images/black.png" >
</p>
<p align="center">
Fig 13. black
</p>
