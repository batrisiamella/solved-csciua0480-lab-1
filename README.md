Download Link: https://assignmentchef.com/product/solved-csciua0480-lab-1
<br>
In this lab you will implement a method for solving a group of linear equations using MPI.

<strong>What will your program do? </strong>

Given a set of n equations with n unknowns (x<sub>1</sub> to x<sub>n</sub>), your program will calculate the values of x<sub>1</sub> to x<sub>n</sub> within an error margin of e%. The format of the file is:

<ul>

 <li>line1: #unknowns</li>

 <li>line2: absolute relative error</li>

 <li>Initial values for each unknown</li>

 <li>line 3 till end: the coefficients for each equation. Each equation on a line. On the same line and after all the coefficients you will find the constant of the corresponding equation.</li>

</ul>

For example, if we want to solve a system of 3 linear equations, you can have a file like this one: 3

0.01

2 3 4

5 1 3 6

3 7 2 8

3 6 9 6




The above file corresponds to the following set of equation:

5X1 +    X2  + 3X3 = 6

3X1 + 7X2  + 2X3 = 8

3X1 + 6X2  + 9X3 = 6

The third line in the file tells us that the initial values for X<sub>1 </sub>is 2, for X<sub>2 </sub>is 3, and for X<sub>3</sub> is 4. Those values may not be the solution, or are very far from the solution that must be within 1% of the real values (as given by the 0.01 in line 2).

<strong>How will your program do that? </strong>




You will use Gaussian-Seidel method. OK, I think you don’t know it, do you? Let me be nice and tell you about it.

We start with a set of n equations and n unknowns, like this:

You are given all a<sub>ij </sub>and b<sub>1 </sub> to b<sub>n</sub>. You need to calculate all Xs.

Here are the steps:

<ol>

 <li>Rewrite each equation such has the left-hand-side is one of the unknowns.</li>

</ol>




Note: The Cs above refer to the constants, which are the b<sub>1 </sub> to b<sub>n. </sub>

In general:                    <em>n</em>

<em>c</em><em>i </em><em>a</em><em>ij x</em><em>j </em>        <em>jj</em><sub></sub>1<em>i </em><sub>     </sub><em>x</em><em><sub>i </sub></em>       <em>a</em><em>ii   </em>,<em>i </em>1,2,K,<em>n</em>.




<ol start="2">

 <li>Remember that you were also given some initial values for the Xs in the input file. The absolute relative error is:</li>

</ol>

100




Therefore, our goal is to reduce absolute relative error for each unknown to make it  less or equal to relative error given in the input file (2nd line). Note: You need to multiply the error given in the file by 100 to match it with the above equation, or to not multiply the above equation by 100.

<ol start="3">

 <li>Substitute the initial values in the equation of X<sub>1 </sub>to get new value for X Use that new value as well as the other initial values for X<sub>2 </sub>to X<sub>n </sub>to get new value for X<sub>2</sub>. Then use the new values for X<sub>1 </sub>and X<sub>2 </sub>and the rest of the initial values to get X<sub>3, </sub>and so on.</li>

 <li>Now we have a new set of Xs.</li>

 <li>Calculate the absolute relative errors for each X.</li>

 <li>If all errors are equal or less the given number (2nd line in the file) then you are done.</li>

 <li>Otherwise go back to step 3 with the set of new Xs as X<sub>old</sub>.</li>

</ol>




<strong>What is the input to your program? </strong>




The input to your program is a text file named xxxx.eq where xxxx can be any name. We already discussed the file format.




<strong>What is the output of your program? </strong>




Your program must output to stdout (the screen) the value of each unknown. The output must look like:

2

3

4

Where 2 correspond to the value of X<sub>1</sub>, 3 corresponds to X<sub>2, </sub>and 4 corresponds to X<sub>3, </sub>… . In the last line of the output show the number of iterations as: <em>total number of iterations: 5</em>




<strong>What do I do after I finish my program? </strong>




We have provided you with a reference program <em>gsref </em>so you can check the correctness of your code. We will test your submission against this reference.




After you finish the parallel version of your program, compile it with:

<em>mpicc -o gs gs.c </em>

Where gs.c is your code. We provide a skeleton file to help you start.




After you compile your program and check its correctness do the following:

<ul>

 <li>Measure the time of your program (using <em>time </em>command) for 1, 2, 4, 8, 16, 32, and 64 processes. You may need to measure the time few times (~ 5) for each and take the average. Do the following with small.txt, medium.txt, and large.txt.</li>

 <li>Draw a graph where the x-axis is the number of processes and the y-axis is the time. There must be 3 curves on the same graph.</li>

 <li>What are your conclusions?</li>

 <li>Draw another graph that shows the speedup (again 3 curves are expected).</li>

 <li>What are your conclusions?</li>

 <li>Include the two graphs and your conclusions in a single pdf file that has your name and titled <em>lab1 submission</em></li>

</ul>