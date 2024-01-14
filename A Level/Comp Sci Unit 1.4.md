
# [tbd] 1.4 Data types, data structures and algorithms

This section is about how data is represented and stored within different structures, and how different algorithms can be applied to these structures.

## Primitive data types, binary and hexidecimal

Primitive data types are those which have adecimal

Primitive data types are those which are provided by a programming language. They are then stored by the computer in binary. They include:
- integers (whole numbers, both negative and positive)
- strings (anything represented as text, typically through "quotation marks")
- Boolean values (`True` or  `False` values)
- floating points (or reals, which are numbers with a fraction/decimal)
- characters (singular characters in a character set, which may be letters, numbers or special symbols)

To then represent these data types, varying number bases are used. Ultimately, computers must store the data in binary (a base 2 system), whilst strings such as colours can be represented in hexadecimal for simplicity, which is a base 16 number system. To show these number bases, subscripts are used. They look like this: 
- 53~10~ - denary (base 10) value of 53
- 1001~2~ - binary (base 2) value for 9
- 23~16~ - hexadecimal (base 16) value for 35

### Converting between denary and binary

Converting between these bases is simple. Write out a table with 8 columns (bits) for a number up to 255. Then, label each column from left to right, doubling in value, starting at 1 and ending at 128. You will need to continue into the second byte if the number is 256 or greater.

| 128 | 64 | 32 | 16 |8  | 4 | 2 | 1  
|--|--|--|--|--|--|--|--|
| 1 | 0 | 1 | 0 | 0 | 0 | 1 | 1 | 

> This value is **unsigned**. Remember that for later.

Now, to calculate the number in denary, add up each column where the value is 1. For example here you would add 128, 32, 2 and 1 for a total of **163** in denary.

To go the other way, simply draw out this table again, and start from the most significant bit (left) side. Take your number and if it is greater or equal to the value of the column, add a `1` to the column and then subtract the value from your number, and move to the next least significant bit. Continue until your number is zero, where the remaining columns will be filled in with `0`. 

### Hexadecimal conversions

Hexadecimal is slightly more tricky. The values of this base system are the same up until the denary value of 9 (`1001`), but anything above this will involve **letters**. The value of `1111` (15) in hex is *F*. 

To convert from binary to hex, split the binary into nibbles (groups of 4 bits). From this, simply write the hex conversion table and write each character (0-9, A-F) for each nibble. 
To convert the other way, do this in reverse. To do this mentally, remember that *F* is `1111` and 9 is `1001`: it is relatively easy to calculate each hex value from these two points.

Converting hexadecimal to denary is also easy. If there are 2 (or more) hex digits, remember that the most significant bit row represents the number of 16s (in denary) that go into that number. As such, if the hex value is *CF*, then remember that *C* is the denary value of 12. However, this must be multiplied by 16, as this column represents the number of 16s due to the number base, so 16x12 is 192. Then, add the value of *F*, which is 15, to give the value of 207.

Finally, converting denary to hexadecimal can be more tricky. A quick way to do this is to **DIV**ide the denary number by 16 for the most significant bit column, and get the remainder (**MOD**) for the lesser significant bit.
For example, to work out the hex of 175, you would do: 
- 175 DIV 16 = 10
- 175 MOD 16 = 15

10 in hex is *A* (`1010`) 
15 in hex is *F* (`1111`)
The answer would be *AF*

## Binary arithmetic

When adding or subtractiing binary numbers, go from the least to most significant bit. Always remember that:
- 0 + 0 = 0
- 1 + 0 = 1
- 1 + 1 = 0 (and carry 1)
- 1 + 1 + 1 = 1 (and carry 1)

## Negative binary and two's complement

### Sign and magnitude

To represent negative numbers, the most common method used is to use the most significant bit as the sign bit. When this leftmost bit is `0`, represents a positive number, and when `1` represents a negative number. This is known as the sign and magnitude representation method.

The positive binary value of `00010001` (19) can be used to work out the negative value `10010001`.
However, when performing arithmetic operations on this, it doesn't really work. Therefore, we use [two's complement](#Two%27s-complement) instead of sign and magnitude.

### Two's complement representation

Two's complement is a way to represent both positive and negative numbers in a way to easily facilitate arithmetic operations on them, by making the most significant bit a sign bit which denotes whether the binary value is positive or negative.

> Where the most significant bit is the sign bit, the value is one which is **signed**. 

To calculate two's complement, firstly invert all bits that represent a binary number. This means making all `0`s `1`s, and vice versa. The result is a value known as **one's complement**. Then, add the binary value `1` to one's complement. The resulting value is the negative (or positive, depending on the chosen number) equivalent of the number inputted.

Here is an example of how to convert negative denary to binary for an 8-bit system:

- 19
= 0001 0011
= 1110 1100 (one's complement)
= **1110 1101** (two's complement)

Similarly, to convert a negative two's complement binary value to denary:

1011 0000
= 0100 1111 (one's complement)
= 0101 0000 (two's complement - we are adding `1` in binary, so carries apply)
= 64+16 = 80
= **-80** (the original value's sign bit was 1, so this final value is also negative)

When subtracting, we can also use this:

1. **27 - 8 (this is equivalent to 27 + (-8))**
	 - 27 is `0001 1011`
	 - 8 is `0000 1000`
2. **Now, calculate two's complement of 8:**
	 - `1111 0111`
	 - `1111 1000`
3.  **Now, time to add the values:**
	 - `0001 1011`
	 - `1111 1000`
	 - `(1) 0001 0011`
	
Therefore, the final value is `0001 0011`, which is 16 + 2 + 1 = **19**. This is indeed 27-8. The overflow digit is ignored: if it wasn't, the value would be negative 19.

## Arithmetic operations with decimals

Of course, when representing numbers, decimals and fractions also are part of the overall equation.

When using decimals on a traditional binary number line, we can extend this to the right below the value of 1. From left to right, the value of the number line halves each time, and this is continued with values below 1. To show these, we insert a **binary decimal point** and the values to the right of it will represent 0.5, 0.25, 0.125, 0.0625 and so on.

For fixed-point binary numbers, there is a given number of bits before and after the decimal point.

![enter image description here](https://c-for-dummies.com/blog/wp-content/uploads/2016/07/0723_powers-of-2-2.png)

When representing fractional/decimal denary values in binary, it's as easy as the conversion of denary to binary earlier, with an added bit for fractions. For example:

Number: 25.875
- 25 in binary: `0001 1001`
- 0.875 in binary: `0.111`
- Answer = `00011001.111`
	-   This can be simplified to `1100 1.111` for 8 bits. The leading zeroes can be truncated



> Some numbers with decimals will never be accurately stored. An infinite level of precision will be required to represent numbers, using inverse powers of 2, such as 0.1 and 0.2. For example, 2/3 would be 0.1010101010...

### Floating point arithmetic
Floating point binary numbers allow the 



## Data structures


<!--stackedit_data:
eyJoaXN0b3J5IjpbMTIxNDkxMDc2NiwtMjAxODIyMTY2MF19
-->