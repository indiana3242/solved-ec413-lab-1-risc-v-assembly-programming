Download Link: https://assignmentchef.com/product/solved-ec413-lab-1-risc-v-assembly-programming
<br>
This lab will introduce you to the RISC-V ISA. For this lab, you will write RISC-V RV32I assembly code and simulate it on the BRISC-V Simulator to show that it works.

1.1     RISC-V Assembly Code

For this lab we will only be using the 32-bit base RISC-V ISA (RV32I). This base ISA only supports simple integer operations with a handful of load, store, branch and jump instructions. Instructions for floating point and integer multiply are not included in RV32I. See the RISC-V Specification Document and the RISC-V Instruction Sheet in the class reading list (<a href="http://ascslab.org/courses/ec413/reading.html">http://ascslab.org/courses/ </a><a href="http://ascslab.org/courses/ec413/reading.html">ec413/reading.html</a>) to see which instructions are available in the RV32I base instruction set. Note that the instruction sheet and RISC-V spec both include instructions for extensions in addition to the base RV32I instructions. Do not use instructions from any extensions, they will not be supported by the simulator (or our hardware).

An example program (function_template.c), it’s assembly (function_template.s) and it’s disassembled binary (function_template.dump) have been included to show you how to follow the calling conventions used by RISC-V. These files are here for your reference. You will not need function_template.c to complete any of the problems. The function_template.s and function_template.dump files are only needed in Problem 1.

Pay attention to three things in the function_template.s file:

<ul>

 <li>How the stack pointer is managed</li>

 <li>How the frame pointer (s0) is managed</li>

 <li>How are function arguments and return values passed</li>

</ul>

<h1>1        Problems</h1>

Note that some problems ask you to test your function with only a single constant value, the TAs will test them with several. You should test your code with more than one input/constant value.

3.1     Problem 1

What real instructions are used to replace the “call” psudo-instruction. Describe all of them in detail. What are the register contents of the system before and after each instruction used in the call psudo-instruction. You only have to describe the state of registers that change. Submit a .txt or .PDF file for this problem.

3.2     Problem 2

<ul>

 <li>Write a function named “int_multiply” in RISC-V assembly to multiply two integers and return the result. The function must follow the calling conventions discussed in lecture and discussion sessions (see function_template.s). Your function must use the assembly equivalent of a for loop. Remember, there is no multiply instruction in RV32I.</li>

</ul>

The listing below shows equivalent C code (your output must be the same):

<table width="588">

 <tbody>

  <tr>

   <td width="159">int int_multiply ( return a*b;}</td>

   <td width="61">int a ,</td>

   <td width="367">int b) {</td>

  </tr>

 </tbody>

</table>

<ul>

 <li>Call your multiply function in a main function. Pass arguments of -2 and 2 to the function. Your main function must return the result of the multiplication. Your code must follow the calling conventions discussed in lecture and discussion sessions (see function_template.s).</li>

</ul>

The listing below shows equivalent C code (your output must be the same):

<table width="588">

 <tbody>

  <tr>

   <td width="220">int         int_multiply (            int a ,</td>

   <td width="367">int b) {</td>

  </tr>

  <tr>

   <td width="220">return a*b;}int main() { return            int_multiply ( -2 , }</td>

   <td width="367">2);</td>

  </tr>

 </tbody>

</table>

3.3     Problem 3

<ul>

 <li>Write a function to compute the factorial of a number using the assembly equivalent of a while loop. The function must be named “factorial”. This function must call your multiply function. Your code must follow the calling conventions discussed in lecture and discussion sessions (see function_template.s).</li>

</ul>

The listing below shows equivalent C code (your output must be the same):

<table width="588">

 <tbody>

  <tr>

   <td width="588">int int_multiply (           int a ,    int b) { return a*b;}int            factorial ( int n) {int product = 1; while (n&gt;0) { product = int_multiply ( product , n );n – -;} return product ;}</td>

  </tr>

 </tbody>

</table>

<ul>

 <li>Call your factorial function in a main function. Pass an argument of 8 to the function. The main function should return the result of the calculation. Your code must follow the calling conventions discussed in lecture and discussion sessions (see function_template.s).</li>

</ul>

The listing below shows equivalent C code (your output must be the same):

<table width="588">

 <tbody>

  <tr>

   <td width="588">int int_multiply (           int a ,    int b) { return a*b;}int            factorial ( int n) {int product = 1; while (n&gt;0) { product = int_multiply ( product , n );n – -;} return product ;}int main() { return factorial (8); }</td>

  </tr>

 </tbody>

</table>

3.4     Problem 4

<ul>

 <li>Implement a non-recursive function to compute the n’th number in the Fibonacci sequence. The function must take in a single integer and return a single integer. The function must be named “fib_nr” (nr for non-recursive) Your code must follow the calling conventions discussed in lecture and discussion sessions (see function_template.s).</li>

</ul>

The listing below shows equivalent C code (your output must be the same):

<table width="588">

 <tbody>

  <tr>

   <td width="255">unsigned        int          fib_nr ( unsignedunsigned int term1 = 0; unsigned int term2 = 1; unsigned int nextTerm ; unsigned int i ;for ( i = 1; i &lt;= n; ++i ) { nextTerm = term1+term2 ; term1 = term2 ;term2 = nextTerm ;} return term1 ;}</td>

   <td width="332">int n) {</td>

  </tr>

 </tbody>

</table>

<ul>

 <li>Call your fib_nr function in main with the following inputs: 1, 3, 8, 17. Place the return values of each function call in registers s2-s5. Your code must follow the calling conventions discussed in lecture and discussion sessions (see function_template.s).</li>

</ul>

The listing below shows (roughly) equivalent C code:

<table width="588">

 <tbody>

  <tr>

   <td colspan="2" width="255">unsigned        int            fib_nr ( unsigned</td>

   <td colspan="3" width="113">int n) {</td>

   <td width="219"></td>

  </tr>

  <tr>

   <td colspan="3" width="289">unsigned int term1 = 0; unsigned int term2 = 1; unsigned int nextTerm ; unsigned int i ;for ( i = 1; i &lt;= n; ++i ) { nextTerm = term1+term2 ; term1 = term2 ;term2 = nextTerm ;} return term1 ;}int main( void ) {// You must make sure the value</td>

   <td width="35">in</td>

   <td width="44">these</td>

   <td width="219">variables           is     stored</td>

  </tr>

  <tr>

   <td colspan="3" width="289">// in the register associated // main returns . unsigned int s2 , s3 , s4 , s5 ;s2 = fib_nr (1); s3 = fib_nr (3); s4 = fib_nr (8); s5 = fib_nr (17);</td>

   <td colspan="2" width="79">with the</td>

   <td width="219">variable name when</td>

  </tr>

  <tr>

   <td width="81">return }</td>

   <td colspan="5" width="507">0;</td>

  </tr>

  <tr>

   <td width="81"></td>

   <td width="175"></td>

   <td width="34"></td>

   <td width="35"></td>

   <td width="44"></td>

   <td width="219"></td>

  </tr>

 </tbody>

</table>

3.5     Problem 5

<ul>

 <li>Implement a recursive function to compute the n’th number in the Fibonacci sequence. The function must take in a single integer and return a single integer. The function must be named “fib_r” (r for recursive) Your code must follow the calling conventions discussed in lecture and discussion sessions (see function_template.s).</li>

</ul>

The listing below shows equivalent C code (your output must be the same):

<table width="588">

 <tbody>

  <tr>

   <td width="588">unsigned        int       fib_r ( unsigned            int n) {i f (n &lt;= 1) { return n;} else {return      fib_r (n-1)+ fib_r (n -2); }}</td>

  </tr>

 </tbody>

</table>

<ul>

 <li>Call your fib_r function in main with the following inputs: 1, 3, 8, 17. Place the return values of each function call in registers s2-s5. Your code must follow the calling conventions discussed in lecture and discussion sessions (see function_template.s).</li>

</ul>

The listing below shows (roughly) equivalent C code:

<table width="588">

 <tbody>

  <tr>

   <td width="289">unsigned        int       fib_r ( unsigned            int n) {i f (n &lt;= 1) { return n;} else {return fib_r (n-1)+ fib_r (n -2); }}int main( void ) {// You must make sure the value</td>

   <td width="79">in         these</td>

   <td width="219">variables           is     stored</td>

  </tr>

  <tr>

   <td width="289">// in the register associated // main returns . unsigned int s2 , s3 , s4 , s5 ; s2 = fib_r (1); s3 = fib_r (3); s4 = fib_r (8); s5 = fib_r (17);return     0;}</td>

   <td width="79">with the</td>

   <td width="219">variable name when</td>

  </tr>

 </tbody>

</table>

3.6     Problem 6

Answer the following performance analysis questions about the recursive and non-recursive Fibonacci functions implemented in problems 4 and 5. Place your answers in a .txt or .pdf file.

<ul>

 <li>How many instructions are in each function?</li>

 <li>What are the total number of executed instructions for each function with an input of 3.</li>

 <li>Which function uses the most registers?</li>

 <li>Which function uses the most memory (number of loads and stores)?</li>

 <li>Which function executes in the fewest number of cycles? Assume each instruction executes in 1 cycle.</li>

</ul>