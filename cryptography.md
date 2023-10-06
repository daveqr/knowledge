# 1. Crypotgraphy

## Hashing

* Take a fingerprint (or hash) from a string. To confirm the original string, run the same hashing process and compare the results. If they are the same, the strings are (likely) the same.
* Hashes are one-way (can't recover the original string from the hash). If you mix two shades of paint you'll get a brown, and can't determine what the original colors were from the brown.
* Hash collision is when two strings technically hash to the same value. For good hashes, no known way to generate two strings whose hashes colide. This property is called `collision resistance`.
* `MD5` and `SHA-1` are older hash functions that we used to think had collision resistance but have been proven insecure. `SHA-256` is a newer hash function that does have collision resistance.
* Dictionary attacks are when a hacker runs the hash function against words in a dictionary, comparing the resulting hash to the original hash. For passwords, can use a list of pre-generated hashes (databases known as `rainbow tables`) to compare against.

### Hashing methods

* `Hashing + Salting` protects against rainbow tables but not dictionary attacks
  1. when hashing the string, generate a short, random string (called the `salt`) and prepend it to the string.
  1. store the salt next to the hash and use it to re-generate the hash.
  1. if two inputs are the same, they will have different hashes because the salts will be different. Similarly, the hashes will be different from those in rainbow tables because they have been salted.
  1. doesn't protect against dictionary attacks because the hacker can use the salt to brute-force the attack (GPUs allow hackers to process billions of hashes per second)

* `slow hashing` - password hashing algorithms like `bcrypt`, `scrypt`, and `Argon2` provide salting but are designed to be slow. The billions of guesses per second can be dialed down to 1000s. Can choose the level of slowness desired, known as the `work factor` or `cost factor`. The work factor is exponential, so increasing the number by 1 makes the algorithm twice as slow. Usually recommended to set the work factor to about 15.


**Bcrypt Hash Example**: `$2a$15$1G7bGQYH5P2.4U.6JfFdduXmUBPoU3e0GkgIXREfUM2UMrsBfOJsu`

Breakdown of the components:

| Component           | Value                                          | Length |
|---------------------|------------------------------------------------|--------|
| **Version Identifier** | `2a`                                       | 2      |
| **Cost Factor**     | `15`                                           | 2      |
| **Salt**            | `1G7bGQYH5P2.4U.6JfFddu`                     | 22     |
| **Hashed Password** | `XmUBPoU3e0GkgIXREfUM2UMrsBfOJsu`             | 31     |

## 1.2. Advice

1. Always operate on raw bytes, never on encoded strings. Only use hex and base64 for pretty-printing.
	* Avoid performing critical operations directly on encoded strings. Instead, decode the string back into raw bytes, perform your operations on the raw bytes, and then encode the result back into the desired format if needed.

## 1.3. Hexadecimal encoding

Hexadecimal is a base-16 numeral system, with digits ranging from 0 to 15. The first ten digits correspone to decimal numbers 0 through 9, while the remaining six digits correspond to the letters A through F (or a through f) in uppercase or lowercase.

Among other uses, in computers, Hex is used for:

* Memory addresses
* Color representation, where where each pair of hexadecimal digits represents the red, green, and blue color components (eg white is #FFFFFF)
* ASCII character encoding. Each ASCII character is associated with a unique hexadecimal value.
* File encoding. Represents binary data in a human-readable form.
* Crypto hashes and keys

## 1.4. Base64

Base64 is a binary-to-text encoding scheme that is commonly used to represent binary data in a text format. It is designed to ensure that data can be reliably transmitted as text over text-only communication channels such as email or included in text-based document formats such as XML and JSON. Base64 encoding accomplishes this by representing binary data using a limited set of characters that are safe to use in text.

* **Character Set**: Base64 encoding uses a set of 64 different characters (hence the name "Base64"). These characters are typically a combination of uppercase and lowercase letters, digits, and two additional characters (often + and / or - and _).
* **Length**: The length of the encoded output is always a multiple of 4 characters.
* **Padding**: To ensure the length is correct, Base64 encoding adds padding characters (typically =) at the end of the encoded string if needed. eg "AB" = "QUI=" and "A" = "QQ=="
* **Binary Data Representation**: Each character in a Base64-encoded string represents a specific group of 6 bits of binary data. By combining these 6-bit groups, you can reconstruct the original binary data.
* **Security**: Base64 encoding is not a form of encryption or security measure. It is simply a way to represent binary data as text. It does not provide confidentiality, integrity, or authentication of the data.

### 1.4.1. Conversion

In Java, conversion between formats requires `DatatypeConverter`, which can be found in the `jaxb` api. Add this as a dependency:

```
implementation 'javax.xml.bind:jaxb-api:2.3.1'
```

#### 1.4.1.1. Convert String to hex in Java

```
final byte[] bytes = "Now is the time".getBytes();
String hexString = DatatypeConverter.printHexBinary(bytes);
```

#### 1.4.1.2. Convert hex to a Base64 String in Java

```
String hexInput = "49276d206b696c6c696e6720796f757220627261696e206c696b65206120706f69736f6e6f7573206d757368726f6f6d";
final byte[] bytes = DatatypeConverter.parseHexBinary(hexInput);
final byte[] encode = Base64.getEncoder().encode(bytes);
String base64 = new String(encode, StandardCharsets.UTF_8);
```

## 1.5. XORing hex strings

XORing hex strings means performing a bitwise XOR operation on the binary representations of two strings. XORing is a binary operation that compares each pair of corresponding bits in two binary values and produces an output where each bit in the result is set to 1 if exactly one of the corresponding bits in the input values is set to 1.

```
// input: 1c0111001f010100061a024b53535009181c
// hexKey: 686974207468652062756c6c277320657965
// output: 746865206b696420646f6e277420706c6179

public static String xorHexStrings(String input, String hexKey) {
    final byte[] inputArray = DatatypeConverter.parseHexBinary(input);
    final byte[] hexArray = DatatypeConverter.parseHexBinary(hexKey);

    byte[] resultArray = new byte[inputArray.length];
    for (int i = 0; i < inputArray.length; i++) {
        resultArray[i] = (byte) (inputArray[i] ^ hexArray[i]);
    }

    return DatatypeConverter.printHexBinary(resultArray).toLowerCase();
}
```

### 1.5.1. Uses of XORing hex strings

1. **Encryption and decryption**: By XORing data with a secret key (also represented as a hexadecimal string), you can obscure the original data. To retrieve the original data, you XOR it again with the same key. This is known as a one-time pad encryption.
2. **Checksums and Error Detection**: By XORing the data with a checksum value, you can create a checksum that can be used to verify the integrity of data during transmission or storage.
3. **Random Number Generation**: XOR operations with suitable inputs can be used to generate pseudo-random numbers.
4. **Data Comparison**: XORing two identical hexadecimal strings results in a string of all zeros, which can be used to compare two pieces of data. If the result of the XOR is all zeros, it means the data is identical.