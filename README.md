Download Link : https://programming.engineering/product/this-assignment-is-designed-to-give-you-a-better-understanding-of-logic-gates-and-circuits/

# CS-211
This assignment is designed to give you a better understanding of logic gates and circuits
Introduction

This assignment is designed to give you a better understanding of logic gates and circuits. The programs have to run on iLab machines.

Note that your program must follow the input-output guidelines listed in each section exactly, with no additional or missing output.

No cheating or copying will be tolerated in this class. Your assignments will be automatically checked with plagiarism detection tools that are pretty powerful. Hence, you should not look at your friend’s code. See CS department’s academic integrity policy at: http://nbacademicintegrity.rutgers.edu/

Circuit Description

One of the inputs to your program will be a circuit description le that will describe a circuit using various directives. We will now describe the various directives.

The input variables used in the circuit are provided using the INPUTVAR directive. The INPUTVAR directive is followed by the number of input variables and the names of the input variables. All the input variables will be named with capitalized identi ers. An identi er consists of at least one character (A-Z) followed by a series of zero or many characters (A-Z) or digits (0-9). For example, some identi ers are IN1 and IN2. An example speci cation of the inputs for a circuit with two input variables: IN1, IN2 is as follows:

INPUTVAR 2 IN1 IN2

The outputs produced by the circuit is speci ed using the OUTPUTVAR directive. The OUTPUTVAR di-rective is followed by the number of outputs and the names of the outputs. An example speci cation of the circuit with two outputs OUT1 and OUT2 is as follows:

OUTPUTVAR 2 OUT1 OUT2

The output values produced by the circuit is speci ed using the OUTPUTVAL directive. The OUTPUTVAL directive describes the output values of the circuit each on its own subsequent line. Each line begins

with the name of the OUTPUTVAR directive followed by the values f0, 1g of the variable for each permutation of the input. OUTPUTVAL will be followed by exactly the same number of lines as there are variables as described in OUTPUTVAR and they will be described in the same order.

An example speci cation for the OUTPUTVAL directive with the OUTPUTVAR described above is as follows:

OUTPUTVAL

OUT10001

OUT21010

In this example, we can deduce that there are 2 inputs. As the input is binary, there are 4 permutations of these inputs f0, 0g, f0, 1g, f1, 0g, and f1, 1g. For these permutations, OUT1 has the values 0, 0, 0, 1 and OUT2 has the values 1, 0, 1, 0, respectively. The order of these permutations will be detailed later.

Logic gates are the basic building blocks of digital systems and circuits. A circuit is one or more logic gates creating a logical relationship between the input and output. The circuits used in this as-signment will be using the following building blocks: OR, AND, XOR, NOT, DECODER, and MULTIPLEXER. The speci cations of each building block is as follows:

    OR: This directive represents the or gate in logic design. The directive is followed by the names of the two inputs and the name of the output. An example circuit for an OR gate (OUT1 = IN1 + IN2) is as follows:

OR IN1 IN2 OUT1

    AND: This directive represents the and gate in logic design. The directive is followed by the names of the two inputs and the name of the output. An example circuit for an AND gate (OUT1 = IN1.IN2) is as follows:

AND IN1 IN2 OUT1

    XOR: This directive represents the xor gate in logic design. The directive is followed by the names of the two inputs and the name of the output. An example circuit for an XOR gate (OUT1 = IN1 IN2) is as follows:

XOR IN1 IN2 OUT1

    NOT: This directive represents the not gate in logic design. The directive is followed by the name of the input and the name of the output. An example circuit for a NOT gate (OUT1 = IN1) is as follows:

NOT IN1 OUT1

    DECODER: This directive represents the decoder in logic design. The directive is followed by the number of inputs, names of the inputs, and the names of the outputs. An example decoder with two inputs IN1 and IN2 is speci ed as follows:

DECODER 2 IN1 IN2 OUT1 OUT2 OUT3 OUT4

Here, OUT1 represents the IN1:IN2 output of the decoder, OUT2 represents the IN1:IN2 output of the decoder, OUT3 represents the IN1:IN2 output of the decoder, OUT4 represents the IN1.IN2 output of the decoder. Note that the outputs of the decoder (i.e., OUT1, OUT2, OUT3, and OUT4) are based on unsigned binary value. They will be in gray code sequence beginning in the second part of this assignment.

    Multiplexer: This directive represents the multiplexer in logic design. The directive is followed by the number of inputs, names of the inputs, names of the selectors, and the name of the output. An example of a 4:1 multiplexer is speci ed as follows:

MULTIPLEXER 4 0 0 1 0 IN1 IN2 OUT1

The above description states that there are 4 inputs to the multiplexer. The four inputs to the multiplexer are 0 0 1 0 respectively. The two selector input signals are IN1 and IN2. The name of the output is OUT1.

Describing Circuits Using These Directives

It is possible to describe any combinational circuit using the above set of directives. For example, the circuit OUT1 = IN1.IN2 + IN1.IN3 can be described as follows:

INPUTVAR 3 IN1 IN2 IN3

OUTPUTVAR 1 OUT1

OUTPUTVAL

OUT100000111

AND IN1 IN2 temp1

AND IN1 IN3 temp2

OR temp1 temp2 OUT1

Note that OUT1 is the output variable. IN1, IN2, and IN3 are input variables. Here, temp1 and temp2 are temporary variables. In the assignment, some gates will be described as unknown or variable gates. They will always be named in the format Gn m x1; x2; :::; xm where n and m are both integers. n will always be the number of the variable gate in which it appears in the input i.e. starting at 1 and incrementing by 1 per variable gate. Here, m will be the number of variables, including inputs and outputs, for the gate. Lastly x1; x2; :::xm will be the name of the variables of the gate. Here is an example of this:

INPUTVAR 2 IN1 IN2

OUTPUTVAR 1 OUT1

OUTPUTVAL

OUT10011

G1 2 IN1 temp1

AND IN1 IN2 temp2

MULTIPLEXER 4 1 1 0 0 temp2 temp1 OUT1

G1 OR

G2 NOT

Figure 1: Visualization of a circuit with unknown gates G1 and G2.

Figure 1: Visualization of a circuit with two unknown gates, G1 and G2

As seen above, a circuit description is a sequence of directives. G1 is an unknown gate which

seemingly takes one input IN1 and output temp1. If every temporary variable occurs as an output

5variableSecond:inthesequenceCircuitbeforeCompleteroccurringasan– inputGrayvariable,Codewe (10saythatpoints)thecircuit description is sorted. You can assume that the circuit description les will all be sorted.

For this section, you will have to write a program that will complete a circuit by choosing the gates Note: A temporary variable can occur as an output variable in at most one directive.

that fill the circuit and fulfill the constraints as in first. However, in this section input permutations

and the ordering of multiplexer and decoders will be in Gray Code. We will use Reflective Gray CodePart oI:createCircuitthepermutationsCompleter.You(30mustpoints)stillusethe DFS methodology for choosing gates as

in first.

You will have to write a program that will complete a circuit by choosing the gates that ll the An example of a multiplexer utilizing grey code ordering is visualized in figure 2.

circuit and ful ll the constraints. In this section, input permutations and the ordering for decoders and multiplexers will be in standard binary order. In this section, we will choose gates based on a DFS strategy where each gate will be temporarily designated as a logic gate, chosen in the order of the gates (OR, AND, XOR, NOT, DECODER, MULTIPLEXER). Using this strategy, circuits with multiple solutions should still return one solution with the gates chosen in the DFS fashion.

For example, say that the circuit description le contains the following:

INPUTVAR 3 IN1 IN2 IN3 OUTPUTVAR 1 Out1 OUTPUTVAL

Out1 0 1 1 1 0 1 0 0 AND IN1 IN2 temp1 G1 3 IN3 IN2 temp2

G2 2 temp1 temp3

OR temp2 IN2 temp4

Figure 2: A visualization of a 4:1 multiplexer utilizing Gray Code ordering. AND temp3 temp4 Out1

Input format: Your program will take the file name as input. The file will contain the description

The circuit described by these directives is shown visually in Figure 1. G1 will rst be designated as of a circuit using the directives described above.

an OR gate then G2 will be designated as an OR gate. If the output of the circuit matches OUTPUTVAL then the output will be two OR gates. If they do not match, then G2 will be sequentially designated as the other gates until a match is found. If no match is found then G1 will be designated as an

5

AND gate. G2 will be reset to an OR gate and the algorithm will repeat.

and the ordering of multiplexer and decoders will be in Gray Code. We will use Reflective Gray Code to create the permutations. You must still use the DFS methodology for choosing gates as in first.

An example of a multiplexer utilizing grey code ordering is visualized in figure 2.

FigureFigure2:2: AAvisualizationvisualizationofofaa4:14:1multiplexermultiplexerutilizingutilizingGrayGrayCodeCodeordering.ordering.

Input format: Your program will take the file name as input. The file will contain the description Input format: Your program will take the le name as input. The le will contain the description of a circuit using the directives described above.

of a circuit using the directives described above.

Output format: Your output will be the name of the variable gate followed by its assigned

type, listed one per line, that complete the circuit. The gates must be in the same order as they 5

were given. If no permutations of logic gates can ful ll the circuit then the program must print:

INVALID. For the example in Figure 1, the output would be:

G1 OR

G2 NOT

Part II: Circuit Completer for Gray Code Inputs (10 points)

For this section, you will have to write a program that will complete a circuit by choosing the gates that ll the circuit and ful ll the constraints as in the rst part. However, in this section input permutations and the ordering of multiplexer and decoders will be in Gray Code. We will use Re ective Gray Code to create the permutations. You must still use the DFS methodology for choosing gates as in the rst part.

An example of a multiplexer utilizing grey code ordering is visualized in Figure 2.

Input format: Your program will take the le name as input. The le will contain the description of a circuit using the directives described above.

Output format: Your output will be the name of the variable gate followed by its assigned type, listed one per line, that complete the circuit. The gates must be in the same order as they were given. If no permutations of logic gates can ful ll the circuit then the program must print:

INVALID.

Part III – Circuit Reducer (40 points)

In this part, you have to determine whether a circuit can be reduced to fewer logic gates. For example, for the solution in Figure 1, G1 is an OR gate. This implies that part of the circuit is:

IN2 OR (IN2 OR IN3)

This can be simpli ed to simply IN2 OR IN3. This is an example of the Associative Law and a basic rule of Boolean Algebra where anything ORed with itself is equal to itself. We will simplify circuits based on 2 combinations of boolean algebra laws and basic rules of boolean algebra. They are listed below.

    Associative law and OR rule: The Associativity rule states that when ORing more than two variables, the result is the same regardless of the grouping of the variables. Again, a basic rule of Boolean Algebra is that anything ORed with itself is equal to itself. Thus, a sequence of two OR gates with the same variable in both can be reduced to just one OR gate. An example of this is that the directives:

OR IN1 IN2 temp1 OR IN1 temp1 temp2

can be reduced to OR IN1 IN2 temp2

For simplicity, we will only include cases such as this example where the pair of gates to be reduced will have the output of gate as the input to the other.

    Distributivity rule: The distributivity rule is the factoring law. This states that a common variable can be factored from an expression just as in ordinary algebra. Thus, a sequence of two AND gates with the same variable in both followed by an OR gate can be reduced to just one AND and one OR gate.

An example of this is that the directives:

AND IN1 IN2 temp1 AND IN1 IN3 temp2 OR temp1 temp2 temp3

can be reduced to

OR IN2 IN3 temp2 AND IN1 temp2 temp3

Another example of this is that the directives:

OR IN1 IN2 temp1

OR IN1 IN3 temp2

AND temp1 temp2 temp3

can be reduced to

AND IN2 IN3 temp2

OR IN1 temp2 temp3

As seen in the previous examples, when reducing gates, the resulting gates should output the variables used by the last-most gates. i.e. when reducing 2 gates that output temp1 and temp2 respectively, the output of the single reduced gate should be temp2. The input variables of the gates that resulted from a reduction should be sorted in lexicographical order. An example of these properties is given under the Output format section. In this section we will continue to use gray code ordering so your implementation for third should be used.

Input format: Your program will take the le name as input. The le will contain the description of a circuit using the directives described above. The directives may still contain the variables gates as in rst and second.

Output format: Your output will be the list of reduced directives that represent the solved original circuit described in the input. If no permutations of logic gates can ful ll the circuit then the program must print: INVALID. The reduced gates should take the place of the last-most gates that they replaced in the sequence. Namely, if two gates replaced three gates, the rst new gate should take the place of the second original gate and the second new gate should take the place of the third original gate in the output sequence.

For example, for the example in Figure 1 the reduced output would be:

INPUTVAR 3 IN1 IN2 IN3

OUTPUTVAR 1 Out1

OUTPUTVAL

Out1 0 1 1 1 0 1 0 0

AND IN1 IN2 temp1

NOT temp1 temp3

OR IN2 IN3 temp4

AND temp3 temp4 Out1

Structure of your submission folder

You should submit your pa5.tar to Canvas.

All les must be included in the pa5 folder. The pa5 directory in your tar le must contain 3 subdirectories, one each for each of the parts. The name of the directories should be named rst, second, and third. Each directory should contain a c source le, a header le (optional) and a Make le. To create this le, put everything that you are submitting into a directory named pa5. Then, cd into the directory containing pa5 (that is, pa5’s parent directory) and run the following command:

$tar cvf pa5.tar pa5

To check that you have correctly created the tar le, you should copy it (pa5.tar) into an empty directory and run the following command:

$tar xvf pa5.tar

This is how the folder structure should be.

    pa5

{ rst

∗ rst.c ∗ rst.h ∗ Make le

{ second

∗ second.c ∗ second.h ∗ Make le

{ third

∗ third.c ∗ third.h ∗ Make le

AutoGrader

First Mode

Testing when you are writing code with a pa5 folder.

    Let us say you have a pa5 folder with the directory structure as described in the assignment.

    Copy the folder to the directory of the autograder

    Run the autograder with the following command:

$python pa5_autograder.py

It will run the test cases and print your scores.

Second Mode

This mode is to test your nal submission (i.e., pa5.tar)

    Copy pa5.tar to the autograder directory

    Run the autograder with pa5.tar as the argument as below: $python pa5_autograder.py pa5.tar

Grading Guidelines

This is a large class so that necessarily the most signi cant part of your grade will be based on programmatic checking of your program. That is, we will build the binary using the Make le and source code that you submitted, and then test the binary for correct functionality against a set of inputs. Thus:

    You should not see or use your friend’s code either partially or fully. We will run state of the art plagiarism detectors. We will report everything caught by the tool to O ce of Student Conduct.

    You should make sure that we can build your program by just running make.

    Your compilation command with gcc should include the following ags: -Wall -Werror -fsanitize=address -std=c11

    You should test your code as thoroughly as you can. For example, programs should not crash with memory errors.

    Your program should produce the output following the example format shown in previous sections. Any variation in the output format can result in up to 100% penalty. Be especially careful to not add extra whitespace or newlines. That means you will probably not get any credit if you forgot to comment out some debugging message.

    Your folder names in the path should have not have any spaces. Autograder will not work if any of the folder names have spaces.

Be careful to follow all instructions. If something doesn’t seem right, ask on Canvas discussion forums or contact the TAs during o ce hours.

9
