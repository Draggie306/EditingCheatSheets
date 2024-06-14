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


### Thinking ahead
There is a need to think ahead to calculate the steps involved in creating a solution. The inputs, processes and outputs should be worked out before the algorithm to calculate the outputs based on the inputs is written! 

Inputs to a problem are information relevant, devised from the abstract model, to the problem. The output is therefore the solution to the problem, returned by the algorithm.

The algorithm *must* *always* be correct and be efficient.

Inputs and outputs should be documented, either in the source code file (e.g. in Python you can use `(numberOne: int)`or a documentation file. This is a **precondition**. Preconditions reduce ambiguity and allow the programmer or user to know what inputs must be inputted. When no preconditions are present in the documentation then it can be assumed that the algorithm will take into account al types of values so that there will be no errors, e.g. checking if a list has a length of over 1 before reading the value at index 0. It is also much easier to re-use algorithms if they have clear inputs and outputs in their documentation.

#### Caching
Caching is a way for the computer system to save (idle) time. Caching is heavily used in time-sensitive applications and networking. The principle of caching is that data which has been recently accessed, or when a pattern of data access is detected, this data should be available for faster access when next requested by the user. An example of this can be seen in the FDE cycle: instead of data computed in the ALU moving to memory for storage, it is moved to the accumulator; likewise, frequently-fetched instructions may be stored in the hierarchy of **cache** memory on the CPU. 
A more noticable example of this is on webpages. Frequently when browsing a website the stylesheet and scripts likely remain the same across pages, so when loading a new webpage on the same website, requesting the (slower) server across the internet will be much slower than storing the stylesheet in, for example, system RAM. Likewise the history function and back button may have the HTML file of the previous page in memory.   


/






<!--stackedit_data:
eyJoaXN0b3J5IjpbLTQyOTczODE1MSwxNDIyNTcwNzI5XX0=
-->