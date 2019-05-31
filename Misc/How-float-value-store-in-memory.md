
# How floating value stored in memory?

- `float` type has size 4 Byte (32 bits)

Lets take a value 13.37 and check how it gets stored in memory.

## First we will convert 13.37 into binary.

### Calculate binary for 13:

	  | 13	| 
------+-----+-----
	2 | 6	| 1			A
------+-----+-----		|
	2 | 3	| 0			|
------+-----+-----		|
	2 | 1	| 1			|
------+-----+-----		|
	2 | 0	| 1			|
------+-----+-----

So ans is: 1101 from down to up.


### Calculate binary for 0.37:

  0.37 * 2 |  0.74	| 0   |  
-----------+--------+-----+
  0.74 * 2 |  1.48	| 1   | 
-----------+--------+-----+
  0.48 * 2 |  0.96	| 0   | 
-----------+--------+-----+
  0.96 * 2 |  1.92	| 1   | 
-----------+--------+-----+
  0.92 * 2 |  1.84	| 1   | 
-----------+--------+-----+
  0.84 * 2 |  1.68	| 1   | 
-----------+--------+-----+
  0.68 * 2 |  1.36	| 1   | 
-----------+--------+-----+
  0.36 * 2 |  0.72	| 0   | 
-----------+--------+-----+
  0.72 * 2 |  1.44	| 1   | 
-----------+--------+-----+
  0.44 * 2 |  0.88	| 0   | 
-----------+--------+-----+
  0.88 * 2 |  1.76	| 1   | 
-----------+--------+-----+
  0.76 * 2 |  1.52	| 1   | 
-----------+--------+-----+
  0.52 * 2 |  1.04	| 1   | 
-----------+--------+-----+
  0.04 * 2 |  0.08	| 0   | 
-----------+--------+-----+
  0.08 * 2 |  0.16	| 0   | 
-----------+--------+-----+
  0.16 * 2 |  0.32	| 0   | 
-----------+--------+-----+
  0.32 * 2 |  0.64	| 0   | 
-----------+--------+-----+
  0.64 * 2 |  1.28	| 1   | 
-----------+--------+-----+
  0.28 * 2 |  0.56	| 0   | 
-----------+--------+-----+
  0.56 * 2 |  1.12	| 1   | 
-----------+--------+-----+


we keep it up to here, as it can continue until we found repeating pattern or 0s.

So ans is: 01011110101110000101 from up to down.


## Converted decimal value to binary value So, 13.37 become 1101.01011110101110000101

## Convert binary value to scientific notation. In which we have to shift the decimal point ('.') to left side untill the last digit.

every time we shift we have to increase the power of 2.

so 1101.01011110101110000101 becomes 1.10101011110101110000101

and we shift 3 times so the "1.10101011110101110000101" becomes 1.10101011110101110000101 X 2^3.

Here,	3 is called exponent,
		.10101011110101110000101 is called significand


## Now, floating points stores as:

1 bit for Signed bit 	(1 for -ve and 0 for +ve)
8 bits	for Exponents
23 bits	for significand

## As per IEEE 754 standard if the exponent is +ve then should be added with 127 and if -ve then should me subtract from 127.

And our exponent is +ve (3) so it should be added in 127 so it become 130.

## Find binary of 130 with same approach as above.

	bin(130) = 10000010

## So our modified exponent will be 10000010. 

## Lets put all togather.

 0		10000010		10101011110101110000101
-----+-------------+-------------------------------------+
Sbit 	Exponent 		Significand

And final number will be 
01000001010101011110101110000101

## Lets Confirm it through program

```
#include <stdio.h>

void main()
{
        float f; 
        f = 13.37;
        printf("address of f : %p\n", &f);
}

```

### In GDB

```
address of f : 0x7fffffffdda4
...
pwndbg> x/xw 0x7fffffffdda4
0x7fffffffdda4:	0x4155eb85

```

### Check binary of 0x4155eb85 in python

```
>>> bin(0x4155eb85)
'0b1000001010101011110101110000101'
```

