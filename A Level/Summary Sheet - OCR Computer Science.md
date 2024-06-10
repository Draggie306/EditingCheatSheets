
# Computer Science Summary Sheet
This is a Summary Sheet, a relatively much more condensed version of my Cheat Sheets. There is much less additional information, and it focuses solely on the content needed.

For a more comprehensive guide, you could check out the full Cheat Sheet and your own notes. Then, come back here and see how much you can remember!

Anyway, let's drop the waffle. Let's get started from the top of the spec down:

# Paper 1: Computer systems

At the highest level, Paper 1 is about:
- The characteristics of contemporary processors, input, output and storage devices
- Software and software development
- Exchanging data
- Data types, data structures and algorithms
- Legal, moral, cultural and ethical issues


```sql
SELECT * 
FROM OCR_SPECIFICATION
ORDER BY Topic DESC 
```

## 1.1.1: CPU

### Registers and the FDE Cycle

Registers are small amounts of high-speed memory used to transfer or temporarily store data for immediate CPU processing.

The contents of these registers are used by the Arithmetic and Logic Unit, in addition to the Control Unit, to execute instructions.

The Fetch-Decode-Execute cycle is responsible for executing instructions on the computer.

#### FETCH
Firstly, the Program Counter (PC) stores the current memory location to be fetched. This is copied into the Memory Address Register (MAR). Using control signals on the system bus, the data from this address memory is fetched, and copied into the Memory Data Register (MDR), and the PC is incremented. Then, the opcode and operand is written to the Current Instruction Register (CIR). 

#### DECODE
The CIR instruction is split into opcode and operand. If the operand holds the memory address of data to be used, it is copied into the MAR and thus fetched and is copied into the MDR. If it is an immediate value of data (e.g. 306) then this is loaded into the accumulator, storing this data temporarily.

#### EXECUTE
Executes the decoded instruction on some decoded data. If the opcode in the CIR is something like "MLT", "ADD", "SUB", the value in the accumulator will be used to preform the operation. Then, when the calculation is complete, it is stored back in the accumulator, where it can be used by another calculation, or written to a memory address.

After this instruction is executed, the cycle is repeated and the PC's incremented address is fetched, decoded and executed.

#### INTERRUPT check?
If an interrupt signal is set to 1, the interrupt service routine will push the values on registers onto a stack, and the PC set to the ISR value. When the interrupt is complete, the values are popped frrom the stack back into the registers. Higher priorities can push lower priority interrupts back to the stack, e.g. a power button press will always be very high priority, keyboard presses are lower priority, and printer needing paper might be lower priority still.

#### Buses
A series of wires with a given width that moves data around the system.
The control bus sends control signals from the control unit **to AND from** I/O devices.
The address bus sends addresses of memory **from** the CPU to other system components.
- Control signals include bus read, bus grant, memory read, memory write, interrupts, and the clock.
The data bus transfers the actual data **to AND from** memory or I/O devices.

### CPU Performance
- Core count: Each core may have its own control unit which can fetch, decode and execute its own set of data. Can only be done if program supports this
- Clock speed: A faster speed means more cycles can be executed per second, at the cost of heat.
- Cache: The 3 levels of cache are in a hierarchy that allows the CPU to store frequently used data from on-CPU temp storage vs slower memory

### Pipelining
Pipelining improves CPU efficiency by allowing the CPU to fetch and decode the next instruction's instructions and values whilst executing the current instruction. This allows multiple instructions to be processed in parallel in a single processor.

### Architectures

#### von Neumann
von Neumann architecture unifies both program instructions and their data in main memory.

#### Harvard architecture
Harvard includes two sections of memory where one is for programs' instructions and the other for program data. There is a separate system bus connecting the two.

- von Neumann simplifies system design, in an era where memory is cheap, and can be applied to a range of systems
- Harvard removes the bottleneck of one system bus if instructions and data are both required
- Harvard is used in more specialised areas

## Processor Types

### Instruction sets

#### CISC
Complex instruction set computer
- Has many more assembly language instructions - e.g. MULT, that perform the operation as multiple other instructions
- This is difficult for pipelining and scheduling as different instructions may take different times to execute
- Easier to write code for as memory/register addresses do not have to be referenced for a relatively basic instruction 

#### RISC
Reduced instruction set computer

- Has only a small number of instructions 
- Each instruction executes over a predictable clock cycles
- More difficult to write code for, but not a concern now due to compilation and translation
- More efficient and optimised than CISC with less overhead  


### GPUs (coprocessors)
Graphics processing units - large amounts of parallel data for concurrent processing, not sequential (like CPU)

Idea is that the CPU can offload 10% of the task to these coprocessors, but that would require 90% of the processing time - making it more efficient

Graphics makes good use of this - vector calculations for millions of pixels many times a second.

Also useful for:
- weather forecasting (large surface area and interactions of water/temperatures challenging)
- cryptocurrency mining (lots of mathematical calculations to prove a hash)
- AI? (lots of vectors and interactions on large volumes of data)


### Multicore and Parallel

Multicore systems are those that have multiple processor cores, with each one able to perform separate instructions in parallel. This allows for greater theoretical performance, and better multi-tasking, as a core can be given to each task. Browser tabs and having 2 apps open in split-screen are examples of when this can be useful. 

However, some applications may not be able to take advantage of this, and sequential applications simply will not benefit from this (e.g. cannot determine the result of a calculation without following the order of operations)


## I/O and storage

#### Input
- mouse
- keyboard
- barcode readers

#### Output
- monitor
- speaker
- printer


### Storage

Secondary storage is storage that contains the data on the computer that is not currently in use, like files on a hard drive. Primary storage is used to store data and instructions that ae required by running programs.

#### Magnetic storage
Includes HDDs. Magnets can be polarised/unpolarised which represents 0/1. Magnetic tape is still used for achival storage. Floppy disks are another example but very low capacity. Useful for high-capacity requirements where cost is a concern and portability is not needed. 

#### Flash storage
Modern, fast and compact. SSDs are a good example. No moving parts thus not damaged from movement, very fast speeds and portable. However, costly. SSDs used for storage of highly-accessed data such as OS files.

#### Optical storage
Based on pits and lands, uses lasers. Examples include CDs and Dvds. They have limited capacity, slowish speeds and can be damaged easily. CDs are cheap and useful for small files, e.g. music, whilst DVDs or blu-ray discs have higher capacity and speeds. 

### RAM
Random access memory, volatile primary storage that contains the OS and currently executing program instructions and data. High speeds. Must be continually powered. Relatively expensive

### ROM
Non-volatile read only memory on the motherboard written once and stores the BIOS (basic input output system) that contains the instructions to load the operating system from secondary storage (bootstrap). 

### Virtual storage
Not virtual memory. Storage on a device that is remote; physically not present, e.g. a cloud server. It can act as a local drive but must go through the Internet. Limitations thus are network speed and cost to host the virtual drive from cloud providers.  

## Systems Software

### Function and purpose of an OS
An OS is a program or set of programs that provide an interface between the user and the computer's components. 

It manages memory and files on a device, manages peripheral devices, handles interrupts and performs processor scheduling.

### Memory Management

#### Paging
Memory is divided into fixed-length physical sections that different applications can be inserted into by the OS in the memory page table. Each page is a fixed length and cannot be changed. Larger programs will occupy more pages. 

#### Segmentation
Different sized sections based on the logical divisions of a program, keeping e.g. a function together.
 
#### Virtual memory
An area of the physical disk used as an overflow from main memory when it becomes full. Unused functions or programs can be swapped in and out of memory to prioritise the ones currently executing or that the user would like to access.

### Interrupts
An interrupt is a signal that is checked for after an FDE cycle is completed, and if True, invokes an Interrupt Service Routine. The data currently stored in the CPU registers is pushed to the system stack. Interrupts have different priorities and can be interrupted by other more important interrupts. 

Interrupts may be something simple such as a peripheral needing attention (printer running out of paper), keyboard press, an I/O device ending, or a power failure. When the ISR has terminated the values from the stack are pushed back into the registers and the processor can continue. 

### Scheduling
The role of the scheduler is to ensure that the processor's throughput is maximised and hardware resources are as busy as possible, the allocation of resources is fair to all users on a multi-user system and to ensure adequate active processing time for each task.

#### Round robin
Each job is given a FIFO time slice (quantum) in which its execution must occur. If it fails to complete then the next job is processed. This happens by using an interrupt clock that pulses at regular intervals and checks if the same job is still executing. This gives fair time for execution for each job.

#### First come first served
The jobs are processed in the order that they are given to the dispatcher. It will occupy the CPU until it completes. There are no priorities so jobs e.g. from viruses can continually dispatch new, long jobs that may prevent the antivirus from allocating its own job.

#### Shortest remaining time
The job with the estimated shortest remaining time to execute is processed next. Shorter jobs can take over from the running process. This reduces the queue of jobs to process but may not be useful for larger, more important jobs such as a large calculation. The user may also have to specify the length of each job or it may become inaccurate. 

#### Shortest job first.
The job with the shortest estimated total time is always executed first, but requires the user to estimate each job and may not favour longer and more important jobs

#### Multi-level feedback queues
Multiple priority queues are created with different priority levels themselves, and can dynamically allocate processor time depending on the job. Jobs that use too much time or are determined to be starving other jobs from CPU time can be demoted to lower queues, whilst long-awaiting jobs are increased in priority. This is more intelligent, and also jobs that are I/O bound or require the processor more urgently are given preference too.


### Types of OS


#### Distributed
Distributed OS coordinate the processing of a job, or multiple jobs, across multiple computers. This is useful for supercomputers or when I/O or data from one computer is required by any other computer. The management of resources is abstracted from the user. It aims to ensure that the load is distributed across each node connected to improve and ensure all tasks are completed quickly.

#### Embedded 
Embedded operating systems have minimal or one specific function and may be held in ROM, and with limited RAM - often only the amount that was determined during manufacturing. It may have a very basic UI and have specialised input/output devices, e.g. sensors, and there are no permanent secondary storage devices.

#### Multi-tasking
Multi-tasking systems are those that perform more than one task simultaneously through the use of processor scheduling. This is most major OSes now. Music can be listened to, whilst working on a document, whilst browsing a website. 

#### Multi-user 
A multi-user operating system is one where a single, powerful computer with one large or multiple CPUs that devices are connected to, and all users receive a slice of processing time.


#### Realtime
Realtime OSes take in many simultaneous inputs and make immediate decisions for what the output must be in a guaranteed time. They are often in safety-critical environments such as aircraft. It may have multiple failsafes and hardware redundancy that is automatically switched to in case e.g. one CPU fails. 


### BIOS
Loads from ROM at start-up and initialises and tests hardware. If all good then load the OS from secondary storage into RAM and then pass control over to it.

### Device drivers
Programs that provides a software interface between an OS or application and a hardware device. This allows the OS to control the devices attached to a system such as speakers or a GPU. This allows the OS to communicate with a hardware device through a driver routine without needing to know the specifics of the manufacturer or its capabilities. 
 
### Virtual machines
Used to emulate another machine. The software that runs for the target machine is translated by the virtual machine to emulate and execute on the host machine. 

Intermediate code such as Java bytecode can execute on the virtual machine. This improves portability as the source code can be translated into machine-independent bytecode which is a "halfway-house" between the source and machine code. The stages of compilation have already been completed so the host system just needs the Java virtual machine to translate into machine-dependent object/machine code. Bytecode interpreters.


## Applications generation

### Nature of applications 
Systems software includes the OS, utilities, libraries and translators. 


### Utilities
Optimises the performance of a computer. These include defragmenters, automatic backups and updaters, irus scanners, firewalls, compression software, encryption software and more.

Defraggers reorganises the layout of where files are physically stored on mechanical drives to be in a more contiguous/sequential manner, improving times.

Applications software includes general purpose and special purpose. 


### Open vs closed source
Open source software is when the source code that has been used to write the program is freely accessible and modifiable. Many users may contribute to ensure that it is bug or vulnerability free, and is the fastest it can be. Support forums can be made and feedback or troubleshooting can be made more easily. New programs can be made under the condition that they too are open source. 

Closed source/proprietary does not have the source code visible. There may be restrictions on how they are used, and it may be licensed under copyright. It may be illegal to modify or distribute it without a prior agreement or paying the copyright owner/creator. The person or company behind the software is responsible to ensure it is exploit free and also may have people paid to give support to users.

### Translators
Programming languages must be translated into low-level machine dependent machine code for it to be executed by the CPU. 

#### Assemblers
It is difficult to code in, time consuming and today it is not worth it. Assembly language is 1:1 representative mnemonics of machine code instructions but are easier to remember and to code in. An assembler translates the mnemonics as written in assembly code into machine code. This is needed as different instruction sets are used by different CPUs and thus different machine code will be produced even for the same mnemonic.

#### Interpreters
Interpreters go over source code line-by-line and translate it into machine code that is then executed. If there is a syntax error, then the code will stop executing at that line, whilst the code before has executed. Therefore errors may be present in code that is running, but may not have been checked in as much rigour as a compiler. JavaScript is an example of this. It allows the file size to be reduced (as the interpreted code must be the source code) providing that an appropriate interpreter is installed on the client machine. Each browser has its own interpreter that is installed; the JS code written may be compressed but is otherwise the same as source and can be opened. However, each iteration will have to be interpreted every time so is slower.

#### Compilers
Compilers translate a high level language such as Python directly into the final object code which is executed. The stages of compilation are gone through to ensure that the source code meets the syntax and the requirements of the language so that there are no critical errors in the final machine dependent code. Different compilers are needed for different CPU architectures. 

### Stages of compilation

#### Lexical analysis
All formatting and unnecessary spaces, comments etc are removed. Tokenisation occurs, replacing each keyword and identifier with tokens that represent their function. The lexer creates a symbol table and this can keep track of memory addresses of each token. Some simple error checking also occurs here, such as an illegal character to the wrong data type.

#### Syntax analysis
The string of tokens is split into phrases and then parsed - or checked vs the language rules to determine if it violates any requirements, e.g. assigning multiple values to a constant, or the "=" operator being used after not before an identifier.

Semantic analysis also occurs here. This is like the grammar. It may syntactically be okay but the program may not be valid, such as the wrong data type associated with a specific variable.

#### Code generation
The machine code is generated.

This may be done over several passes to optimise the code - remove unreachable branches, remove redundancy and replace the code that achieves the same goal but more efficiently.

### Linkers, loaders and libraries
Libraries are pre-compiled, pre-written programs that can be interacted with, typically written by smart people with more expertise, or that is the known fastest way to solve a problem, e.g. mathematical operations or random numbers or even providing the interface for a GUI. There is little point in rewriting the same code as has already been written. They are tested, reduce the need to re-code tasks and save space. 

The linker can replace the memory address within a compiled program to the one of the library function. The loaders copies the program and the linked libary subroutines into main memory - it must relocate the memory locations though.

Linking may be dynamic or static. Sometimes the executable program may have libraries imported in it and be very sizeable. However dynamic linking may not include the linked functions and assume that the host device will have matching libraries to reference and call.



## Software development

- Analysis
	- Defining the problem and how it may be solved. What software may be needed, what kinds of data as defined by the end user.
- Design
	- Decomposing the problem into a series of individually solvable modules and algorithms.
	- How these components function, are interlinked, and any extra precautions e.g. input validation to prevent hacks.
- Implementation
	- Divided into programming, testing (to inform development) and documentation.
	- The code for modules as designed earlier is written.
	- Unit testing involves testing individual components during development with valid, erroneous and boundary testing
	- Integration testing involves testing the interrelationship and whether the individual modules work together as intended
	- Black and white box testing that check the entirety of the final program (black) or the sequence of modules during development (white) to ensure every code path and all functions are functional.
	- Alpha and beta testing provide developmental/end user feedback to the programmer with issues 
	- Acceptance testing for the end user combines all of the above testing with live data and compares to the needs of the user as identified in the analysis stage.
- Evaluation
	- Allows the end user to identify any issues and must solve the problem given.
- Maintenance
	- Post-development changes e.g. bug fixes or new features can be developed and made to the program whilst in operation
	- Corrective, adaptive and perfective maintenance
	- Changes should also follow the methodology of the dev model being used.


### Methodologies

#### Waterfall
The stages of development are completed sequentially. The order must be followed. The end user only has an input in the analysis and no other stages. Each stage must be completed to a high standard before moving to the next stage. Not good for long-term projects - programs are only produced late in the cycle, and all requirements must not be ambiguous or have any possibility to be interpreted differently.

#### Spiral
Creates complete iterations/prototypes of the software that goes through each of the dev stages. This allows iterative development and gradual improvement. This can allow for new requests to be implemented over time, making the product more flexible, many iterations may be required for it to solve the problem completely. The end user may be able to choose from the iterations what is the best, or revert to a previous iteration. Better for long-term projects. 

#### Agile
There is no set order of the dev stages. This means that the program can be developed in the most efficient way depending on the needs - e.g. prioritisation of end-user feedback. Prototypes similar to the spiral model are made frequently, and changes can be made to some parts of the project (implementation) without having to go through the preceding ones. Changes can be made late into the dev cycle. However, this may deprioritise design and adequate documentation.

#### Extreme
Extreme programming is based on the agile development model but made significantly faster to accommodate the needs of the end user through rapid feedback and short cycles of development.

#### Rapid application development
RAD is a type of agile development where priority is given to speed of development. Program components can be reused. Components are given a fixed time limit to make each part good enough for the general requirements identified.


## Networks

### Importance of protocols
Protocols and standards ensure that data can be communicated between devices in the same way, regardless of manufacturer or operating system.

### TCP/IP stack
The model has 4 layers:
- Application layer: this assigns protocols based on the application being used for it. For example, the HTTP protocol for web browser applications or the SSH for file transfer applications.
- Transport layer: splits into and numbers packets using the TCP or UDP protocol to establish transmission between two devices over a network. It also adds ports.
- Internet layer: adds source/destination IP addresses
- Link layer: specifies mac addresses; typically that of the router



### D-type flip flops
- Stores a 1-bit value when a signal is given.
- Has a data and clock input: when the clock input is 1 and the data input is different to the output (Q) state, then the output flips




# Paper 2

## 2.2.1 Programming techniques

### Programming Constructs
There are 3 main programming constructs:

#### Sequence 
Refers to how the code is ordered. In an imperative language like fortran the code flows sequentially so instructions written before others are always executed first.

#### Iteration 
Is looping. May be done through:
- for loop: for i in range(10) loops 10x, for value in array will go over each value in the array
- while loop: is true and iterates over the indented code block below until the condition is no longer true
- do/while: always executes at least once; after first execution is complete, checks the while condition, if it's still true then it will continue to execute. 

#### Selection 
Essentialy means `if` statements. Some parts of the code can only be "selected" to be executed if a Boolean condition is evaluated to True..

#### Branching 
Refers to the execution and sequence of execution moving from one section of the program to another. This can be done through subroutines/procedures in a procedural language, and in the LMC instruction set BRP (conditional) and BRA are branch instructions.

### Recursion
Recursion is when a function calls itself. If a function `sum` has parameters `num_one` and `num_two` these can be used within the function to call itself until a condition is met.

Recursive functions must:
- have a stopping condition (has a base case - typically an `if` statement);
- call itself when this base case is not met (is self-callling);
- reach the base case in a finite number of calls. 

When a recursive function calls itself, the execution of the calling function is paused until the results of the called function are calculated - each function call is considered separate. The amount of functions called may be very "deep" and therefore the values are pushed on a call stack in memory. 

More memory is used as each copy of the function requires its own variables and instructions in memory, however, less code is needed to be written as there is no need to create variables that keep track of the current iteration.

```c
def fact(n)
	if n == 0 then
		factorial = 1
	else
		factorial = n * fact(n - 1)
	return factorial
endfunction
```

If all of the three conditions are not met then the recursive function is either A) not recursive or B) will result in a stack overflow error as memory becomes increasingly used.

Whilst iteration is typically faster, some programs (e.g. graph/tree traversal algorithms) may not work at all with iteration, or result in a much larger time complexity so that the program is intractible without using recursion.

### Variable scoping

#### Global
Global variables can be accessed at any part of the code being executed. They are typically defined with the `global` keyword. To access them within a function you should also put `global <name>` in the function too. 

Global variables can be changed from within the subroutine. For example;

```py
global number
number = 5

procedure add_number(num1, num2)
	number = number + num1 + num2
	#// we are not going to return anything either
endprocedure

add_number(1, 2)

print(number)
```

this would print 8: even though the procedure has its own enclosing scope, the global variable being modified results in the number from outside the procedure being modified anyway.

Global variables can be used anywhere in a program.

#### Local

Local vaiables may only be defined and used in a specific part of the program, such as a function.



## Data structures

### Hash tables

Hash tables are abstract data types that have an array and an algorithm to index items. This means they have a time complexity of O(1) - constant.

The algorithm is typically [input] `MOD` [size of the array] . Folding square method is squaring the input, and keeping the middle (two) numbers and `MOD`ing them. 

Collisions are a problem. To resolve them we can do rehashing to increment the index by 1 until a space is found, or turn the array 2D and append the element to the array at given index.















<!--stackedit_data:
eyJoaXN0b3J5IjpbMTY4Mjc3MzA3MCwtMTA1MjkxNzA5MF19
-->