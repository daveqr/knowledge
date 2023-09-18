# Binary Number Systems and Operations

## Aritmatic

### Addition

You can directly add both positive and negative numbers using binary addition. No need to take the two's complement first. The sign bit (leftmost bit) handles the sign for you. When adding numbers, if the result overflows, it's typically truncated to fit within the specified number of bits.

* When adding digits, if the sum is `0` or `1`, write down the sum.
* When the sum is `2`, write down `0` and carry `1` to the next position.
* When the sum is `3`, write down `1` and carry `1`.

```
   1101   (13 in binary)
 + 1010   (10 in binary)
 -------
  10111   (27 in binary)
```

### Subtraction

To perform subtraction, you can use binary addition as well. When you need to subtract a negative number, you take the two's complement of that number and then add it to the other number using binary addition. The result is adjusted to fit within the specified number of bits.

### Multiplication

* If one of the digits is 0, the product is 0.
* If both digits are 1, the product is 1.

```
    101   (5 in binary)
 x  110   (6 in binary)
 -------
  11110   (30 in binary)

```

### Division

1. **Setup**
	* Write the dividend (the number to be divided) and the divisor (the number you're dividing by).
	* Align the leftmost (most significant) bits of the dividend and divisor.
	* Determine whether the dividend is larger than or equal to the divisor. If it's smaller, the result will be 0, and the remainder will be the same as the dividend.
2. **Division**
	* Start from the leftmost bit and work your way to the right.
	* For each bit position, perform the following steps:
		* If the current portion of the dividend is greater than or equal to the divisor, subtract the divisor from the dividend and set the corresponding bit in the quotient to 1.
		* If the current portion of the dividend is smaller than the divisor, set the corresponding bit in the quotient to 0.
	* Continue this process for all bit positions.
3. **Result**
	* The bits in the quotient represent the integer part of the division result.
	* The remaining bits in the dividend (after performing the division) represent the remainder.
4. **Handling Fractions**
	* For fractional binary numbers, you can continue the division process to the desired number of binary places (bits) for the fractional part. This is similar to how you might extend the decimal division process for decimal fractions.

## Two's Complement

Two's complement is a mathematical technique used to represent signed integers (both positive and negative) in binary form.

It simplifies arithmetic operations on binary numbers and allows for the representation of negative numbers in a way that works well with hardware. When performing operations like addition or subtraction, the hardware doesn't need to distinguish between positive and negative numbers; it treats them all as binary values and produces the correct result using two's complement arithmetic.


In binary, the leftmost bit (the most significant bit) is used as the sign bit, where:

* `0` represents a positive number.
* `1` represents a negative number.

### Positive Numbers

For positive numbers, the two's complement representation is essentially the same as the regular binary representation. The leftmost bit is `0`, indicating a positive sign, and the remaining bits represent the magnitude of the number in binary form. For example, `5` in two's complement would be `0101`, which is the same as in regular binary.


### Negative Numbers

To represent negative integers, use two's complement.

1. **Take the complement**: Invert (flip) all the bits in the binary representation of the absolute value of the negative number. This means changing 0 to 1 and 1 to 0.
1. **Add 1**: After taking the complement, add 1 to the result.

For example, `-5` in two's complement:

1. Start with the binary representation of the absolute value of `5`, which is `0101`
2. Take the complement: `1010` (invert all bits)
3. Add 1 to the complement: `1011`

#### Examples

**-9**

1. binary representation of abosolute: `0000 1001`
2. complement: `0000 0110`
3. add 1: `0000 0111`


**-23**

1. binary representation of absolute: `0001 0111`
2. complement: `1110 1000`
3. add 1: `1110 1001`