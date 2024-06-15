# Computer Science Summary Sheet
This is a Summary Sheet, a relatively much more condensed version of my Cheat Sheets. There is much less additional information, and it focuses solely on the content needed.

For a more comprehensive guide, you could check out the full Cheat Sheet and your own notes. Then, come back here and see how much you can remember!

Anyway, let's drop the waffle. Let's get started from the top of the spec down:

# Paper 2: Algorithms and programming

Computational thinking is having the ability to logically think about a problem and apply techniques to solve it. This allows algorithms to be designed with the end result of efficiently solving a problem.

<!-- A good comment informs its readers, corrects authors, and offers insights in a polite, respectful and constructive manner. All other comments fall into the category of rants, bile, insults or trolling. -->

In computing, a "problem" should be defined as something that can be solved by an algorithm. (it may be just a simple subroutine)

## Thinking abstractly

### The nature and need for abstraction
Abstraction is a model of reality that has removed details which are irrelevant to the solution of the problem. A common example of this is the London Underground: only the different lines and stations need to be shown to get from one place to another, irrespective of the geography/exact distance/type of train, etc., **so information is hidden without losing meaning**.

Abstraction models are thus a representation of reality so that a solution can be found whilst only taking into account what is required and nothing else - facilitating computational and algorithmic approaches 

Abstraction is needed so that a problem can be solved in a simple way, thereby speeding up the time it takes to create and execute a solution without overloading the user with information. For example, the user can just be told to copy and paste a file from one document to another, without needing to know the details of how the program that runs the document software works, how the OS is allocating memory to the program, and how the file of the document itself is being read to and written into secondary storage with the physical fipping of bits or electrons being trapped.

A model for, for example, a shop and its revenue, may take into account the number of visitors, how much is spent and if there are any refunds. This does not take into account the process of welcoming people into a shop, how long people spend inside, the items people are going to buy, as this is largely unnecesary for the specifc task: to calculate revenue.


## Thinking ahead
There is a need to think ahead to calculate the steps involved in creating a solution. The inputs, processes and outputs should be worked out before the algorithm to calculate the outputs based on the inputs is written! 

Inputs to a problem are information relevant, devised from the abstract model, to the problem. The output is therefore the solution to the problem, returned by the algorithm.

The algorithm *must* *always* be correct and be efficient.

Inputs and outputs should be documented, either in the source code file (e.g. in Python you can use `(numberOne: int)`or a documentation file. This is a **precondition**. Preconditions reduce ambiguity and allow the programmer or user to know what inputs must be inputted. When no preconditions are present in the documentation then it can be assumed that the algorithm will take into account al types of values so that there will be no errors, e.g. checking if a list has a length of over 1 before reading the value at index 0. It is also much easier to re-use algorithms if they have clear inputs and outputs in their documentation.

### Caching
Caching is a way for the computer system to save (idle) time. Caching is heavily used in time-sensitive applications and networking. The principle of caching is that data which has been recently accessed, or when a pattern of data access is detected, this data should be available for faster access when next requested by the user. An example of this can be seen in the FDE cycle: instead of data computed in the ALU moving to memory for storage, it is moved to the accumulator; likewise, frequently-fetched instructions may be stored in the hierarchy of **cache** memory on the CPU. 

A more noticable example of this is on webpages. Frequently when browsing a website the stylesheet and scripts likely remain the same across pages, so when loading a new webpage on the same website, requesting the (slower) server across the internet will be much slower than storing the stylesheet in, for example, system RAM. Likewise the history function and back button may have the HTML file of the previous page in memory. On a larger scale CDNs (content delivery networks) on websites store copies of the webpage so that the "origin" server's load is reduced and therefore cost is saved and user access time is reduced. 

However, there are some drawbacks of caching. If an OS predicts that an instruction will be loaded next, and it is not required, then this fetch-decode-execute cycle has effectively been wasted. This can add up oer time. Stale caches are another example: websites may show old versions of their content - not good if concert-goers are constantly refreshing to buy a ticket - although the load is reduced for the origin webserver it needs to display this new content/availability!

### Reusable program components
Well-defined, documented algorithms are more likely to be error-free and can be used in many different programs. There is little point in recreating a complex function from scratch when a library that contains the desired inputs and outputs already exists, such as inside a Windows Dynamic Link Library (DLL) file. These algorithms must be predictable and easily understandable for other programmers.

For large projects or for large companies with a range of projects and software, they may make their own libraries that can be shared. Abstract data types are those that can be implemented differently depending on the program but have the same overall logic, and for simplification across this large codebase, they may be (re)written to ensure that all programs share the same logic and are therefore more predictable, savng time.


## Thinking procedurally
Involves the procedural breakdown of a problem into a number of sub-problems, to accomplish the soution of an overall (larger) task. 

To create the solution to a problem, the components of it will need to be identified. So too will be the components of the solutions of the program itself. To do this, the steps needed to solve the problem will too need to be identified - this can be done through top-down design or hierarchy charts.

Thinking procedurally thus allows programs to be decomposed into a series of more distinct algorithms that have their own dedicated purpose. This is an example of structured programming - modularisation, structured code (i.e. using the 3 constructs) and recursion. Each sub-function can be tested individually and documented as its own reusable component - allowing it to be used at various points in the program. The scope of these individual sub-functions means that changes to one of them will be less likely to interfere with other parts of the program; also, different programmers can work on different sub-functions.

- "Decomposes"/breaks down program into sub-problems
- Identifies components of the program
- Identifies the components of a solution to the program
- Techniques such as hierarchy charts allow a top-down overview as to how these sub-functions can be created for the overall problem's solution


## Thinking logically 



## Programming techniques

### The 3 constructs
There are 3 main constructs to any progam: sequence, selecton and iteration.

Sequence is the order of execution. This means that one instruction is executed after another, one line before another, unless there is a branching statementor function call used (GOTO or BRP/BRZ/BRA in LMC) 

Selection is the process of evaluating a Boolean condition and selecting to execute code 


/






<!--stackedit_data:
eyJoaXN0b3J5IjpbLTM2NTMzMzU2NCwtNjAwMDI5NDgyLC0xMT
M5NTExMzkwLDMxNTU1NjUyNiwxNDIyNTcwNzI5XX0=
-->