# Ajith_delay_MPMC_SA2

# To generate a 200 µs delay using Timer 0 in Mode 1 and toggle Port 0.1.


## AIM
To write and execute an assembly language program for the 8051 microcontroller to toggle the port pin P0.1 every 200 microseconds using Timer 0 in Mode 1 (16-bit timer mode).

---

## APPARATUS REQUIRED
- Personal computer with Keil software

---

## ALGORITHM
Algorithm:

1. Start the program.

2. Initialize Timer 0:

Load the Timer Mode register with #01H to set Timer 0 in Mode 1 (16-bit timer).

Clear the port pin P0.1 initially.

3. Enter the main loop:

Toggle P0.1 using the CPL P0.1 instruction.

Call the DELAY subroutine to generate a 200 µs delay.

4. DELAY subroutine:

Load TH0 and TL0 with initial values (#0FCH and #0F8H) for 200 µs delay.

Start Timer 0 by setting the TR0 bit.

Wait until Timer 0 overflow flag (TF0) becomes 1.

Stop Timer 0 and clear the overflow flag (TF0).

Return to the main program.

5. Repeat the loop:

Continue toggling P0.1 and generating a 200 µs delay indefinitely.

6. End program.


---

## FLOWCHART

![WhatsApp Image 2025-10-24 at 15 28 51_7e7044f7](https://github.com/user-attachments/assets/c02a6043-12ed-47a2-9d8c-110f8a9c5a43)

---

## PROGRAM
```asm
ORG 0000H

MAIN:
    MOV TMOD, #01H      
    CLR P0.1           

LOOP:
    CPL P0.1            
    ACALL DELAY         
    SJMP LOOP          

DELAY:
    MOV TH0, #0FCH     
    MOV TL0, #0F8H
    SETB TR0            
WAIT:
    JNB TF0, WAIT       
    CLR TR0             
    CLR TF0             
    RET

END

```
OUTPUT

<img width="800" height="600" alt="Screenshot 2025-10-24 151220" src="https://github.com/user-attachments/assets/a1f10242-6bea-40ab-a5dc-e954ee59fdb9" />

<img width="800" height="600" alt="Screenshot (269)" src="https://github.com/user-attachments/assets/15074b36-eead-45ed-a7b9-658c49830900" />


---

RESULT

The assembly program was successfully executed on the 8051 microcontroller using Keil software.

---


