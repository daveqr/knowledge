
# Bitwise Operations

## Bitwise AND (&) Operation

The bitwise AND (&) operation is used to determine whether both corresponding bits of two operands are set to 1. It returns 1 if both bits are 1, otherwise, it returns 0.

### Simple Comparison Example

(2 & 3)

Binary Representation:

	2 - 0010
	3 - 0011

Bitwise AND results:

	0 & 0 results in 0
	0 & 0 results in 0
	1 & 1 results in 1
	0 & 1 results in 0

Therefore, (2 & 3) equals 0010 in binary representation, which is equivalent to 2 in decimal notation.

### Use Cases for Bitwise AND (`&`)

1. **Masking Bits:** Bitwise AND is commonly used to mask (retain) specific bits of a value while setting others to zero. This is useful when you want to extract or isolate certain information from a bit pattern. For example, you can use bitwise AND to extract the red component of a color value in RGB format.

2. **Setting and Clearing Individual Flags:** In many programming scenarios, you might use a combination of bitwise AND and OR to set, check, or clear individual flags within a set of flags. This is often seen in system status or configuration flags.

3. **Accessing Hardware Registers:** When working with embedded systems or hardware programming, bitwise AND is frequently used to manipulate and query specific bits within hardware registers to control hardware functionality.

4. **IP Address Subnetting:** In networking, the bitwise AND operation is used to determine whether an IP address belongs to a particular subnet. By applying a subnet mask to an IP address using bitwise AND, you can determine the network portion of the address.

5. **Data Compression:** Bitwise operations are used in data compression algorithms to efficiently represent data. For instance, the Run-Length Encoding (RLE) algorithm uses bitwise operations to encode runs of repeated data.

6. **Bitwise Hashing:** Cryptographic hash functions often use bitwise operations to mix and manipulate bits in a way that provides a high degree of security and collision resistance.

7. **Access Control:** Bitwise operations are sometimes used in access control systems where permissions are represented as bit flags. You can use bitwise AND to check if a user has specific permissions.

8. **Optimizing Code:** In low-level programming, bitwise operations can be used to optimize code by replacing expensive operations like multiplication and division with bit shifts.


### Determining Even and Odd Numbers

To determine whether a number is even or odd, compare it to 1 using the bitwise AND operation. Because the binary representaiton of 1 is 0001, you are effectively just comparing the LSBs (the lest significant bit, ie the number to the utmost right.) Odd numbers end in 1 and even numbers end in 0.

	boolean isEven = (num & 1) == 0

#### Even Example

(2 & 1)

	2 - 0010
	1 - 0001

Bitwise AND results:

	0 & 0 results in 0
	0 & 0 results in 0
	1 & 0 results in 0
	0 & 1 results in 0

So, (2 & 1) equals 0000 in binary representation, which is equivalent to 0 in decimal notation, and 0 is even.

#### Odd Example

(5 & 1)

	5 - 0101
	1 - 0001

Bitwise AND results:

	* 0 & 0 results in 0.
	* 1 & 0 results in 0.
	* 0 & 0 results in 0.
	* 1 & 1 results in 1.

So, (5 & 1) equals 0001 in binary representation, which is equivalent to 1 in decimal notation, and 1 is odd.

