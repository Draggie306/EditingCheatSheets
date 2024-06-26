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

Thinking procedurally is used in conjunction with thinking ahead so that the sub-procedures process the inputs as part of the overall program to create a desired, correct and predictable output.

## Thinking logically 
Logical thinking is about determining when decisions in program logic/flow have to be made. In practice this may be `if` statements (conditional selection/branching) and is where a decision is made. The conditions that affect this will be evaluated depending on logical conditions, such as Boolean operators. "`if X < Y then do Z`" (a decision) will evaluate to True and do Z if a condition, if X is lower than Y, is True.

The flow of the program can be said to be adjusted depending on the logical condition. This is the basis for all programs and software: there is no point of using a computer if the result is already known to be the same for all inputs. 

## Thinking concurrently
Concurrent thinking is about the parts of a program that can be tackled at the same time. It would be pointless to have an intrusion detection system monitor the back door if the front door is not being monitored at the same time too. 

Parallel computing is the use of multiple processors running different instructions at the same time. The GPU can be processing the positions of objects in a game whilst the CPU is decoding the instructions for a character's movement. This speeds up processing but is not possible on just one processor.
+ more intensive tasks can be offloaded to specialised parts of the computer system such as the GPU
+ processing can be sped up significantly when repetitive calculations (e.g. vector positioning in 3D rendering) need to be calculated
	+ this is also why AI uses GPUs just like games, they both use vectorisation for various tasks	
- most programs are serial: they may not be optimised to use other processors to perform a function, or cannot do this at all. It has only been in recent years that browsers now have the option to use the GPU for graphics intensive tasks e.g. video playback/DOM rendering
- there is an overhead of allocating and managing the coordination of different tasks being performed by different programs at the same tme
- Amdahl's law exists.
[Source: ARM: Limitations of parallel processing](https://developer.arm.com/documentation/dui0538/f/parallel-processing-concepts/limitations-of-parallel-processing)



Concurrent processing is the allocation of time (scheduling) of each process. This is required in multi-user or multi-tasking systems. As the CPU is extremely fast the illusion is therefore that two programs are being executed at the same time but in reality they are not. 
This has the effects of:
+ increased program throughput and utilisation of the CPU, allowing more tasks to be performed more quickly
+ the system does not need to wait for user input to start an instruction, the other instruction can use CPU time instead
- if the CPU is executing a large number of programs and is very busy in its utilisation then the time to complete all tasks is increased (this is why your computer may freeze if you are doing lots of processing on it)


## Programming techniques

### The 3 constructs
There are 3 main constructs to any progam: sequence, selecton and iteration.

Sequence is the order of execution. This means that one instruction is executed after another, one line before another, unless there is a branching statementor function call used (GOTO or BRP/BRZ/BRA in LMC) 

Selection is the process of evaluating a Boolean condition and selecting to execute code 


### Recursion and iteration

A recursive function is one that has three requirements:
- has a base case - and not call itself if this is met;
- must call itself for all times this base case is not met;
- must reach the base case in a finite and predictable number of steps.

Recursion is only useful if the algorithm is recursive. It may be more intuitive to call itself, especially if programs are modular in structure. Recursive functions also do not need to keep track of how many times they have iterated over some data as they only have one base case, resulting in shorter code, but often makes it harder to read and trace through. 

Execution of the invoking function is paused, and its data is pushed to the call stack in a single stack frame, during the execution of the called function. For when recursion occurs many times, or the base case was not specified correctly, the size or depth of the call stack may be so large that a stack overflow error occurs or the system runs out of memory. This is not the case for iterative routines. 

### Global and local


### Parameter passing
Passing by value creates a copy of the data with a separate memory address and data that is ony active whilst in the called subroutine and destroyed when it becomes out of scope - therefore not affecting the original variable.
Passing by reference uses the actual memory location to 


### IDE use


### OO techniques




### Knowledge of principles



### Big-O notation
Represents the complexity - in terms of the amount of passes to complete a sort/search - of an algorithm. 

- O(1): constant. The same amount of time to execute no matter the size of the dataset. This is typically the best case
	- A hash table is an example of this.
- O(log n): logarithmic. Each iteration reduces the amount of remaining items by half. Likewise each time the dataset doubles the amount of iterations required to process this increases by one.
	- Examples include binary search and merge sort.
- O(n): linear. The linear complexity increases iterations by one for each new item in the dataset. This makes it efficient for small values but as the dataset grows the time required increases too.
	- This includes simple `for` loops, iterating over an array.
- O(n^2^): polynomial. Again, the number of iterating increases significantly with the size of the input dataset. This is hopelessly inefficient for even medium sized datasets.
	- This is why a nested `for` loop is typically a bad idea for performance. 
- O(2^n^): exponential. This is the opposite to logarithmic: the time required doubles with every element added.Again, this is hopelessly inefficient and if an algorithm requires this it is likely intractible.

There is also O(n log n) which is less efficient than O(log n) but is linear to - linearithmic. This is when a linear search is performed and thus may reduce the size of the dataset by half. This includes merge sort and quick sort (although these should be categorised as logarithmic for the purposes of OCR exams). 

> O(n!) is factorial and simply should not be used.

To work out the complexity of code: 
- if there are no iterations, it is likely O(1)
- if there is halving occurring then the complexity will likely be O(log n) 
- single iterations make the complexity O(n)
- nested iterations make the complexity O(n^2^)
- recursive functions that call themselves twice or more have a O(2^n^) complexity

The most inefficient part of the code is used to determine the complexity: if there is a nested for loop but also division then the complexity will be O(n^2^) due to the priority of the most inefficient loop.

#### Space complexity and cases 
Space complexity refers to the memory usage during the operation. Linear complexities will not require any more memory to be used, however for algorithms such as merge sort the memory required increases significantly, as the implementaiton may be resursive, so may have a polynomial space complexity. While less important than time (memory is cheap) it should be considered.

The examples required are for the worst case. However it is worth noting that the best case, average and worst cases are all slightly different. For msot algorithms the best case is O(1) in case only one operation has to be performed to get to the answer, e.g. the first element in a serial search or the middle item in binary search. The average time complexity for most algorithms is the same as their worst case but can vary slightly to be a little worse. Hash functions are always O(1) - unless there is a collision in which case the worst time complexity is likely O(n).

### Standard algorithms

#### Bubble sort
This sorting algorithm is very inefficient due to its nested looping - an O(n^2^) average and worst case. It starts by initialising a Boolean value to True and while it is True it will iterate over the array and compare the current element to the element at index + 1 (and set the Bollean value to False). If the element at index + 1 is smaller than the current index, then they will be swapped (by setting index + 1 to index, and index to index + 1 with a temp variable to ensure data is not duplicated). The Boolen value will be updated to True if swapping has occurred. Then the current index is incremented, and the process will continue until the value is False, exiting the loop and signifing successful sorting.

It has a time complexity of O(n^2^) for most cases; in the case that the array is sorted it will be O(n). However, its space complexity remains O(1) as it modifies the array in-place. It should thus only be used if the array is small.

#### Insertion sort
Insertion sort has similar complexities to bubble sort. 

Starting at index 1, iterate over the array. If the item at the index is greater than the item at index 0, then increment the counter. Else, store the index in a temporary variable and perform comparisions on each preceding element to check if it is less than or equal to the temporary variable value. One it is so, move each element in indexes greater than the current position up by 1 and insert the temporary variable to the current index. Increment the original counter and repeat.

It is mostly useful for already-sorted or nearly-sorted lists/arrays and for small ones. However its space complexity remains O(1) due to in-place modification. The majority of the time, especially in reverse ordered arrays, its complexity is O(n^2^). 

#### Merge sort
Merge sort is the binary search of sorting. It recursively splits an array in half until each individual element can be compared and sub-lists created that double in size for each comparison, until the original length array is re-assembled in order.



#### Quick sort

#### Dijkstra's shortest path algorithm

#### The A* algorithm
The A* algorithm is a general purpose pathfinding algorithm that uses a heuristic function (h(x)) that qims to find a solution to the path that is "good enough" using these heuristics - but not always the most optimal solution. The real cost (g(x)) is this applied to visiting each node in addition to this heuristic function.



#### Binary search
Uses a midpoint (end - start DIV 2) and comparisons to check whether the item at the midpoint of an array is greater, equal to or less than the target. If it is equal, then return the position and found. Else, remove that half of the array and call the function again until the element is found. 
- Has O(1) best case
- For everything else, has O(log n)

Binary search trees are similar. However unweighted trees have a worst case of O(n).

Binary searches require the data to be pre-sorted. This also can increase the time required for new insertions.

#### Linear search
 Linear search simply iterates over an array, and compares it to the target, using a counter to track iterations. Its best case is O(1) but average and worst cases are O(n) and can be used (and may be the only choice to use) on unsorted arrays. Its linear time complexity requires it to be used on a small array only, else it will take too long.

Inserting items can be done as an array or linked list which is typically faster than binary searching.















<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE1ODY3MDY2NCwtNzMwNjc5NjQsNTg0Nz
c0MDA2LC0xMjAyNzkyOTQ5LDczNzY4NjY5MSwtMzY1MzMzNTY0
LC02MDAwMjk0ODIsLTExMzk1MTEzOTAsMzE1NTU2NTI2LDE0Mj
I1NzA3MjldfQ==
-->