# Overview

An example of a compiler written in Python3 which will compile a predefined extended BNF into java bytecode.
This project was undertaken as an asignment item for COSC261. Template code was pre provided, however the asignment required
for the adaptation and modification of certain aspects of code.


# Extended BNF
Program = Statements
Statements = Statement (; Statement)*
Statement = If | While | Assignment  | Read | Write


If = if Comparison then Statements \[else Statements] end
While = while Comparison do Statements end
Assignment = identifier := Expression
Read =  read identifier

Write = write Expression

Comparison = Expression Relation Expression
Relation = = | != | < | <= | > | >=

Expression = Term ((+ | -) Term)*
Term = Factor ((* | /) Factor)*
Factor = (Expression) | number | identifier



# Using the compiler

**The following is an excerpt taken from the assesment guidelines:**

Your compiler is run using Python 3 with the program passed via standard input. The Java assembly is expected via standard output. Assuming your compiler is in the file compiler.py, the program is in the file program, and the Java assembly goes to the file Program.j, this amounts to calling

## Step 1:
python3 compiler.py < program > Program.j
An error at this stage is indicated by
Error in compiling

## Step 2:
If stage 1 was successful, the Java assembly is translated to a Java class file using the Jasmin assembler, see http://jasmin.sourceforge.net/. Jasmin is in the file jasmin.jar. The call is

java -Xmx100m -jar jasmin.jar Program.j
This generates the class file Program.class. An error at this stage is indicated by
Error in assembling Java byte code

## Step 3
If stage 2 was successful, the Java class file is run using Java with the test passed via standard input. The result is expected via standard output. Assuming the test is in the file test_input, and the result goes to the file test_output, this amounts to calling

java -Xmx100m Program < test_input > test_output
An error at this stage is indicated by

Error in running Java byte code for subtest X
X is the sequential number of the run for the test program.

## Step 4
If stage 3 was successful, the result is compared with the expected output. A difference is indicated by

Wrong output for subtest X
If there is no difference, you pass this test.

