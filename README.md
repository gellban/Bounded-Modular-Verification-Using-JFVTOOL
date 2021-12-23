# Bounded-Modular-Verification-Using-JFVTOOL

**Introduction:**
JFVTool is a bounded modular verification tool that formally checks whether or not the program’s methods have been implemented according to their specifications. This tool automatically checks the code for all possible cases (within some bounds), and verifies that it meets the specifications. 
The purpose of this experiment is to evaluate if users find JFVTool effective and useful while they are programming. In this session, you will implement two methods of two classes, and will use JFVTool to help in creating correct implementations. 
JFVTool has some limitations, which are: 
It is not compatible with Java 8; it works with Java 5, 6, or 7. 
It does not support recursion. To cope this limitation, you must use iteration as you implement the methods. 
It does not support the “java.io” package and several other packages. Therefore, you cannot use any I/O method, such as “System.out.println” in your implementation. 
The output of JFVTool will not be exactly one-to-one with your source code, but it should be similar enough to help the user to get an idea about the reason behind the potential uncovered bugs.

**Steps:**
The instructions for implementing the two methods in a Linux platform as follows: 
Installing JFVTool in your machine:
Copy “JFVTool.zip” from the flash drive which will be provided to you, to your working computer. 
Unzip the file using the following command: 
unzip JFVTool.zip -d .
Change your directory, as follows:
cd JFVTool

**Implementing the first method of array data structure: **

Open the file "ArrayImp.java" in a text editor. In this file is a partial implementation of a data structure using an unsorted array to hold positive nonzero integer ID keys; this array is already defined in the superclass, and you must not initialize it in your implementation. Any empty element has a zero value and can be anywhere in the array. Read all comments in this file which include a description of the data structure and specifications of the add method.
In the file is a method "add" that has only a return statement in order to be compiled without any syntax error. For this task, you must properly implement the method, and use JFVTool to check your implementation. 
Before implementing the method, compile the existing code and run JFVTool on it, as:
javac -classpath lib/annotations.jar:./ ArrayImp.java
mv ArrayImp.class BPkg/
java -jar JFVTool.jar BPkg ArrayImp lib/ superclass No 3 1 3

You should see a "NotPass" condition for the "add" method; you see other methods “Pass”, but just ignore those. See item 1 of the attachment at the last page of this document for more explanations.
Now, run the tool with “Yes” parameter to show some detailing why it did not pass, as follows:
javac -classpath lib/annotations.jar:./ ArrayImp.java
mv ArrayImp.class BPkg/
java -jar JFVTool.jar BPkg ArrayImp lib/ superclass Yes 3 1 3
You should see a "NotPass" condition for the "add" method, along with complete program trace. The first 12 lines of this trace present the pre-state of the parameter and array variable before the method evaluates. In the initial state, “I1=2” represents iD=2. The line, that begins with int[].elems = [[int[]0, 0, 0]], shows the key array’s elements; it has three values: [name of the array (i.e. int[]0), index=0, value of the element=0], which might be more elements when you implement the method. The last 3 lines shows the final state including the return value of the method which is -1 “add_return = -1”. The element of the array does not show in the final state because the array does not change. See the item 2 in the attachment for more details.
Now remove the return statement, implement the add method according to its specifications, compiling and then running JFVTool as above, as often as you wish. You should try to use the output with trace (i.e. item b/2) of JFVTool to help you complete a correct implementation of "add".
If you were able to create an immediately correct implementation of "add" (i.e., the first time you ran JFVTool after programming the method, you obtained a "Pass" result), then add a small bug to your implementation and see if JFVTool detects it (it should!). For example, you could create an off-by-one error fairly easily.

**Implementing the second method:**

Open the file "BinarySearchImp.java " in a text editor. In this file is a partial implementation of a data structure using an unbalanced binary search tree to hold positive nonzero integer keys; this data structure is already defined in the superclass (i.e. Node and root). Read all comments in this file which include a description of the data structure and specifications of the add node method.
In the file is a method "addNode" that has only a return statement in order to be compiled without any syntax error. For this task you must properly implement the method, and use JFVTool to check your implementation. Before implementing the method, compile the existing code and run the JFVTool on it, as:
javac -classpath lib/annotations.jar:./ BinarySearchImp.java
mv BinarySearchImp.class BPkg/
java -jar JFVTool.jar BPkg BinarySearchImp lib/ superclass Yes
You should see a "NotPass" condition for the "addNode" method, along with some output detailing why it did not pass. You see other methods “Pass” as shown in item 3 of the attachment. You can also re-run JFVTool with “No” parameter.
Now remove the return statement, implement the add node method, compiling and then running JFVTool as above, as often as you wish. You should try to use the output of JFVTool to help you complete a correct implementation of "addNode".
If you were able to create an immediately correct implementation of "addNode" (i.e., the first time you ran JFVTool after programming the method, you obtained a "Pass" result), then add a small bug to your implementation and see if JFVTool detects it (it should!). For example, you could create an off-by-one error fairly easily.
Finally, re-run JFVTool to fully verify (analyze) that ArrayImp has been implemented the “addNode” of array abstract class correctly:
          java -jar JFVTool.jar BPkg BinarySearchImp lib/ superclass Yes 4 4 4
Submitting your Java files:
Create a subdirectory in this flash memory and copy your two files “ArrayImp.java” and “BinarySearchImp.java” to this subdirectory.
Return this flash memory to the coordinator of this session.

**Attachment**

The output of analyzing ArrayImp Java program without a trace option:
METHOD	                                 		Result
================================	======
add                                      			Not Pass
delete                                   			Pass
findIndexOfID                            			Pass
Some output results of analyzing ArrayImp Java program with a trace option:
METHOD	                                 		Result
================================	======
add                                      			Not Pass

initial state:
  this = BPkg.ArrayImp0
  l1 = 2
  …
  int[].elems = [[int[]0, 0, 0]]
  …
final state:
  add_return = -1
  add_throw = null

delete                                   			Pass
findIndexOfID                            			Pass
The output of analyzing BinarySearchImp Java program with a trace option:
METHOD	                                 		Result
================================         	======
find                                     			Pass
delNode                                  			Pass
addNode                                  			Not Pass
a counter example trace:
initial state:
  this = BPkg.BinarySearchImp0
  l1 = AbstractPkg.BSTAbstract$Node0
  key = [[AbstractPkg.BSTAbstract$Node0, 2]]
  left = [[AbstractPkg.BSTAbstract$Node0, null]]
  right = [[AbstractPkg.BSTAbstract$Node0, null]]
  root = [[BPkg.BinarySearchImp0, null]]
final state:
  addNode_return = -1
  addNode_throw = null

