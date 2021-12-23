C code for a Low Tech Programmer Calculator

Description: Designing of Low Tech Programmer Calculator which takes an user input with the help of input knobs and output
will be represented via LEDs as each LED will represent a bit of signed 8bits.

Part A
Your manager needs you to write a C program for a new low-tech programmer calculator the company is
developing.
The calculator hardware looks like the following: 
To guide the development of the C program your manager provides the following requirements.
The result LEDs should display the calculated result of the User Input Knobs positions
The result LEDs should display the result's value as a signed 8bit number with each LED representing a bit 
When the result is out of range of a signed 8bit number, or can't be calculated for some reason:
the error LED should be turned ON
the result LEDs should show a value of 0
Your manager has also provided some example test cases:

Part A  –  4
Addition Case
Inputs:
- Left Operand Knob = 2,
- Operator Knob = "+",
- Right Operand Knob = 3
Outputs:
- Result LEDs should display 5 in binary as the result, error LED should be
OFF
Multiplication Case
Inputs:
- Left Operand Knob = 3
- Operator Knob = "x"
- Right Operand Knob = 3
Outputs:
- Result LEDs should display 9 in binary as the result, error LED should be
OFF
Another developer has provided two functions (listed below) that can be used to interact with the hardware of the
calculator.
Provided functions
// Input: Pointer to store value(s) upon successful read.
// Format will be:
// - bits 0 to 3, Left Operand value in binary
// - bit 4, Addition Operator selected
// - bit 5, Multiplication Operator selected
// - bit 6, Subtraction Operator selected
// - bit 7, Division Operator selected
// - bits 8 to 11, Right Operand value in binary
// Output: true if read was successful, false otherwise
extern bool readKnobInputs(unsigned *dataPtr);
// Input: Value to write to display LEDs.
// Each bit set will turn an LED ON, each bit clear will turn an LED OFF.
// Format will be:
// - bit 0: Result LED Error
// - bit 1: Result LED Bit 0 (LSB)
// - bit 2: Result LED Bit 1
// - bit 3: Result LED Bit 2
// - bit 4: Result LED Bit 3
// - bit 5: Result LED Bit 4
// - bit 6: Result LED Bit 5
// - bit 7: Result LED Bit 6
// - bit 8: Result LED Bit 7 (MSB)
// Output: N/A
extern void writeLedOutput(unsigned data);
Software: Team  –  Embedded C Screening Test - Low Tech Programmer Calculator
Part A  –  5
A main.c template is provided to you to start your programming. Fill in the rest of the program to get the calculator
functioning.
Provided main.c template
extern bool readKnobInputs(unsigned *dataPtr);
extern void writeLedOutput(unsigned data);
int main(void)
{
 while(1)
 {

 }
}


Part B
It turns out that the developer who was working on the two hardware functions has been reassigned to another
project.
Your manager asks you to implement the functions instead and gives you documentation about the hardware
interface.
Left & Right Operand Knobs
User Input Register 1 Address = 0xA0000000
- 32bit Read-Only Register
- bit 31, If set Left Operand Knob at position F
- bit 30, If set Left Operand Knob at position E
- bit 29, If set Left Operand Knob at position D
- bit 28, If set Left Operand Knob at position C
- bit 27, If set Left Operand Knob at position B
- bit 26, If set Left Operand Knob at position A
- bit 25, If set Left Operand Knob at position 9
- bit 24, If set Left Operand Knob at position 8
- bit 23, If set Left Operand Knob at position 7
- bit 22, If set Left Operand Knob at position 6
- bit 21, If set Left Operand Knob at position 5
- bit 20, If set Left Operand Knob at position 4
- bit 19, If set Left Operand Knob at position 3
- bit 18, If set Left Operand Knob at position 2
- bit 17, If set Left Operand Knob at position 1
- bit 16, If set Left Operand Knob at position 0
- bit 15, If set Right Operand Knob at position F
- bit 14, If set Right Operand Knob at position E
- bit 13, If set Right Operand Knob at position D
- bit 12, If set Right Operand Knob at position C
- bit 11, If set Right Operand Knob at position B
- bit 10, If set Right Operand Knob at position A
- bit 9, If set Right Operand Knob at position 9
- bit 8, If set Right Operand Knob at position 8
- bit 7, If set Right Operand Knob at position 7
- bit 6, If set Right Operand Knob at position 6
- bit 5, If set Right Operand Knob at position 5
- bit 4, If set Right Operand Knob at position 4
- bit 3, If set Right Operand Knob at position 3
- bit 2, If set Right Operand Knob at position 2
- bit 1, If set Right Operand Knob at position 1
- bit 0, If set Right Operand Knob at position 0

Part B  –  7
Operator Knob
User Input Register 2 Address = 0xA0000004
- 32bit Read Only Register
- bits 31-4 unused
- bit 3, If set Operator Knob at position '÷'
- bit 2, If set Operator Knob at position 'x'
- bit 1, If set Operator Knob at position '-'
- bit 0, If set Operator Knob at position '+'
Result Display
User Output Register 1 Address = 0xA0000008
- 32Bit Read & Write Register
- bits 31-9 unused
- bit 8, If set turns ON Result LED 7 (MSB), turns OFF if clear
- bit 7, If set turns ON Result LED 6, turns OFF if clear
- bit 6, If set turns ON Result LED 5, turns OFF if clear
- bit 5, If set turns ON Result LED 4, turns OFF if clear
- bit 4, If set turns ON Result LED 3, turns OFF if clear
- bit 3, If set turns ON Result LED 2, turns OFF if clear
- bit 2, If set turns ON Result LED 1, turns OFF if clear
- bit 1, If set turns ON Result LED 0 (LSB), turns OFF if clear
- bit 0, If set turns ON Error LED, turns OFF if clear
Using the above documentation fill in the body of the two hardware functions.

Part B  –  8
Hardware functions to complete
// Input: Pointer to store value(s) upon successful read.
// Format will be:
// - bits 0 to 3, Left Operand value in binary
// - bit 4, Addition Operator selected
// - bit 5, Multiplication Operator selected
// - bit 6, Subtraction Operator selected
// - bit 7, Division Operator selected
// - bits 8 to 11, Right Operand value in binary
// Output: true if read was successful, false otherwise
bool readKnobInputs(unsigned *dataPtr)
{
 //Fill in function
}
// Input: Value to write to display LEDs.
// Each bit set will turn an LED ON, each bit clear will turn an LED OFF.
// Format will be:
// - bit 0: Result LED Error
// - bit 1: Result LED Bit 0 (LSB)
// - bit 2: Result LED Bit 1
// - bit 3: Result LED Bit 2
// - bit 4: Result LED Bit 3
// - bit 5: Result LED Bit 4
// - bit 6: Result LED Bit 5
// - bit 7: Result LED Bit 6
// - bit 8: Result LED Bit 7 (MSB)
// Output: N/A
void writeLedOutput(unsigned data)
{
 //Fill in function
}


Part C
After completing the software your manager wants more re-assurance that the software works as intended.
He wants you to provide additional test cases beyond the initial set that can be provided to another team to verify
the functionality. 
Add more test cases that would be useful for this design.
Addition Case
Inputs:
- Left Operand Knob = 2,
- Operator Knob = "+",
- Right Operand Knob = 3
Outputs:
- Result LEDs should display 5 in binary as the result, error LED should be
OFF
Multiplication Case
Inputs:
- Left Operand Knob = 3
- Operator Knob = "x"
- Right Operand Knob = 3
Outputs:
- Result LEDs should display 9 in binary as the result, error LED should be
OFF
Add more test cases here...
