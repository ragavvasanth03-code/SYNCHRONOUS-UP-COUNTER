### SYNCHRONOUS-UP-COUNTER

**AIM:**

To implement 4 bit synchronous up counter and validate functionality.

**SOFTWARE REQUIRED:**

Quartus prime

**THEORY**
A counter is a sequential circuit that counts the number of clock pulses applied to it. It is made up of a group of flip-flops that store binary information and change their state in a predefined sequence.

Counters are broadly classified into:

Asynchronous (Ripple) counters – flip-flops do not share the same clock.

Synchronous counters – all flip-flops are triggered simultaneously by the same clock pulse.

In a synchronous up counter, all flip-flops receive the same clock signal, ensuring that all bits change simultaneously, avoiding the propagation delay that occurs in ripple counters.

Each clock pulse increments the count by 1. When the counter reaches its maximum value (for a 4-bit counter, 1111 or decimal 15), the next pulse resets it to 0000 and the counting repeats.

WORKING PRINCIPLE:

The counter output is stored in the 4-bit register out[3:0].

On every positive edge of the clock (clk), the counter increments its value by 1 (out <= out + 1).

If the reset (rst) signal is high (1), the counter output is reset to 0 (out <= 0).

When rst is low (0), the counter continues to count upward with each clock pulse.

Thus, the counter counts in binary sequence from 0000 to 1111 and then rolls over to 0000.
**4 bit synchronous UP Counter**

If we enable each J-K flip-flop to toggle based on whether or not all preceding flip-flop outputs (Q) are “high,” we can obtain the same counting sequence as the asynchronous circuit without the ripple effect, since each flip-flop in this circuit will be clocked at exactly the same time:

![image](https://github.com/naavaneetha/SYNCHRONOUS-UP-COUNTER/assets/154305477/d5db3fa0-e413-404c-b80e-b2f39d82e7e8)


![image](https://github.com/naavaneetha/SYNCHRONOUS-UP-COUNTER/assets/154305477/52cb61eb-d04b-442d-810c-31185a68410b)

Each flip-flop in this circuit will be clocked at exactly the same time.
The result is a four-bit synchronous “up” counter. Each of the higher-order flip-flops are made ready to toggle (both J and K inputs “high”) if the Q outputs of all previous flip-flops are “high.”
Otherwise, the J and K inputs for that flip-flop will both be “low,” placing it into the “latch” mode where it will maintain its present output state at the next clock pulse.
Since the first (LSB) flip-flop needs to toggle at every clock pulse, its J and K inputs are connected to Vcc or Vdd, where they will be “high” all the time.
The next flip-flop need only “recognize” that the first flip-flop’s Q output is high to be made ready to toggle, so no AND gate is needed.
However, the remaining flip-flops should be made ready to toggle only when all lower-order output bits are “high,” thus the need for AND gates.

**Procedure**

/* write all the steps invloved */
 1. Type the program in Quartus software.
 2. Compile and run the program.
 3. Generate the RTL schematic and save the logic diagram.
 4. Create nodes for inputs and outputs to generate the timing diagram.
 5. For different input combinations generate the timing diagram

**PROGRAM**

/* Program for flipflops and verify its truth table in quartus using Verilog programming. 

Developed by: RegisterNumber: 25018843
*/
module ex11(out,clk,rst);
input clk,rst;
output reg [3:0]out;
always @ (posedge clk)
begin
   if(rst)
     out<=0;
   else 
     out <= out+1;
end
endmodule

**RTL LOGIC UP COUNTER**


<img width="1920" height="1080" alt="Screenshot (43)" src="https://github.com/user-attachments/assets/93d86be3-717d-4f3a-bb36-22d2f0b7ab81" />




**TIMING DIAGRAM FOR IP COUNTER**



<img width="757" height="502" alt="Screenshot (42)" src="https://github.com/user-attachments/assets/ac6ef107-d86e-49c9-af35-9d37c6f31415" />

**TRUTH TABLE**




<img width="609" height="411" alt="Screenshot 2025-10-08 115408" src="https://github.com/user-attachments/assets/2c1b507d-cd3c-4efd-8999-07582312f679" />


**RESULTS**  Thus the truth table of logic gates in Quartus II using Verilog programming is studied
 and verified successfully
