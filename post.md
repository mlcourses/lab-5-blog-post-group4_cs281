# Lab 5: Designing a Sequential Circuit!


## Overview and goals: 
In this lab we build a circuit that reads a binary number and determines if that input is divisible by 3. The circuit will read one bit at a time and every time we add 0 or 1 to the circuit the bit will be appended to the back of the number. Also, we will use a clock such that each bit will be clocked into the circuit using a separate clock input. It is important to know that the output is showing whether the current binary number is divisible by 3 or not. If the binary number is divisible by 3, say the binary number is 6, the output will be high. In contrast, if the binary number is non divisible by 3, the output will be low. It is also very important to know that at the beginning of the string, when it's empty, the output needs to be high, because we treat the empty string as a binary number divisible by 3. 

Main goal: Build a circuit that reads a binary number and outputs high when the string is divisible by 3 and low otherwise.


## Materials 
The materials we will be using in this lab are:
..* PB-503 breadboard
..* Wires
..* Arduino kit
..* Arduino controller with the USB adapter
..* computer for the Arduino IDE
..* 7404 chip (NOT gate)
..* 7408 chip (AND gate)
..* 7476JKff (jk flip flop)
..* 7486 chip (XOR gate)

## Project Steps 
Step 1: Build a DFA 
In this step we will build a DFA that consists of three states, in which the only binary strings that will be accepted are those who are divisible by three in decimal. Only one state will be an accepting state (q0) and each state will have precisely two arrows, with a 1 and with a 0. (add photo)

**Step 2: Decide how many jk flip flops you need**
In this step, we decide how many jk flip flops we need based on the number of states in the DFA. we always have log_2(#number of states) and round this up. In this case, since we have 3 states we will have 2 jk flip flops. (add photo)

**Step 3: design a logic for the two combinational circuits, next-state and output.**
In this step we are to design a mini truth table that has three columns: state, Q1, Q0. at each state we decide what Q1, Q0 are. Since we have only three states, and there are 4 rows (00,01,10,11), the last row 11 will go to a don't care state x. (add photo)
 
**Step 4: Create a Boolean Truth Table (function table) diagram**
In this step we are to build a function table with the current state and the corresponding Q’s, then a column with the next input (x), then the new state and its corresponding Q’s. After that we fill the four columns (j1,k1,j0,k0 ) based on the values of the initial state Q1 and Q0 to the values of the new states Q1’ and Q0’. Then, the last column will be the output, which is basically indicating if we we are accepting the string (1 if so)  or rejecting it (0 if so). 

**Step 5: build a K-map for each output**
In this step we are to build a k-map for each J, K, and the out value. The reason we are doing that is because we want to simplify as much as possible our logic operands for the circuit we are going to build and k-maps are the perfect tool to simplify complicated boolean algebra. 

**Step 6: Build the circuit**
This is the step where we are actually building the circuit. Steps 1-5 were necessary in order to get to this step, and now when we have the simplified algebra from the k-maps we can build the circuit.

## Observation and Takeaways
We have a not gate, two gates, an xor gate, a clock, and two jk flip flops.
We start from input x, which is going to be inverted and connected to k1 (second flip flop). The output of the first flip flop will go to an and gate with the inverted x, and their output will go to j1 (second flip flop). 

The output of the second flip flop will go to an xor gate with the input x, and their output will go to j0 (first flip flop), k0 (first flip flop) will always be 1. The clock is connected to the push button and connected to both flip flops. We also have a reset (clear) that connects to the logic switches in a way that we can reset our binary number any time we reset with the switch. 
We wire output to the last logic probe, that way we can keep track of the result of our circuit. 


## Testing
After building the circuit, we proceeded to test it out. To input the number, we simply flip the switch for x, flipping it to 1 if we want to append 1 to the back of the binary number and vice versa, flipping it to 0 if we want to append 0 to the back of the binary number. The circuit will update depending on the clock, so if we want to update the binary string, we simply push the button acting as the clock, and then the circuit will update and the new bit will be added to the string. We tested with numbers both divisible by 3 and not divisible by 3, and the circuit behaved like what we expected exactly like the DFA. As long as it is not in an accepting state i.e. the current number is not divisible by 3, the probing light will be set to low; and whenever we move the data input to or back to the accepting state i.e. the current number is divisible by 3, the probe will be set to high, which is what we desire. We also tested out the CLEAR feature for the FFs, and it also worked as expected: when we set the switch for the reset to low and then to high again, all of the memory is cleared off, and we can input a new binary number to the circuit.



## Conclusion
In this lab, we were able to successfully build a sequential circuit that can take in a binary number and determine whether or not the number is divisible by 3. From this lab, we were able to utilize our newly learned knowledge of constructing a sequential circuit. We went through many steps: building a DFA, creating a boolean truth table (function table) diagram, building K-Maps, and then constructing the circuit in logisim to test it out before actually building it. In the end, the lab has taught us new things, mainly the process of building a sequential circuit and using J-K Flip Flops, and has left us with the confidence to face even more challenging projects in the future.

