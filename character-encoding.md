# Character encoding

## ASCII vs Unicode

Character sets defining a universal and standardized set of characters and assigns each character a unique code point, which is a numerical value that represents that character. ASCII represents primarily English characters, whicl Unicode includes characters from virtually all writing systems used around the world, mathematical symbols, emoji, and more.


| Characteristic         | ASCII                                  | Unicode                                |
|------------------------|----------------------------------------|----------------------------------------|
| Character Range        | Primarily English characters and symbols| Characters from all writing systems globally  |
| Multilingual Support   | Limited to English language            | Supports characters from all major writing systems |
| Character Representation| 7-bit (128 characters) or 8-bit (256 characters) code per character      | Variable number of bits per character (usually 16 or 32 bits) |
| Compatibility          | Compatible with older systems and software expecting 7-bit or 8-bit encodings | Modern standard widely adopted in contemporary software |

## Unicode vs UTF-8

### Unicode

1. **Character Set**: Unicode is not an encoding but rather a character set. It defines a universal and standardized set of characters and assigns each character a unique code point, which is a numerical value that represents that character. Unicode includes characters from virtually all writing systems used around the world, mathematical symbols, emoji, and more.

2. **Character Encoding**: Unicode itself doesn't specify how characters are encoded into binary data. It's a character mapping standard. Unicode can be encoded in various ways, such as UTF-8, UTF-16, and UTF-32, each with its own encoding rules.

3. **Fixed-Size Encoding**: Unicode encoding schemes like UTF-16 and UTF-32 use fixed-size code units (16 bits and 32 bits, respectively) to represent characters. This means that all characters are encoded using the same number of bytes, which can lead to inefficiency when representing characters that could be encoded more compactly.

4. **Multilingual Support**: Unicode is designed to support characters from all major writing systems globally, making it suitable for internationalization and multilingual applications.

### UTF-8

1. **Character Encoding**: UTF-8 (Unicode Transformation Format - 8-bit) is one of the encoding schemes used to represent Unicode characters in binary form. It is a variable-length encoding, which means that it uses a variable number of bytes (8 bits each) to represent characters. Commonly used characters, including ASCII characters, are represented using a single byte (8 bits) in UTF-8. Characters outside the ASCII range may require multiple bytes.

2. **Efficiency**: UTF-8 is efficient for representing text data because it uses fewer bytes for commonly used characters in Western languages. This makes it an effective encoding for web content and text files where English text is prevalent.

3. **Backward Compatibility**: UTF-8 is backward compatible with ASCII, meaning that ASCII-encoded text can be seamlessly included in UTF-8-encoded documents.

4. **Web and File Formats**: UTF-8 has become the dominant encoding for web content and is widely used in file formats like HTML, XML, JSON, and more. It's the default encoding for many modern web technologies.


## UTF-8 encoding for web sites

UTF-8 is the most widely used character encoding scheme for representing text on the web. Character encoding can be managed by either the client (browser) or server.

### Web Servers (Server-Side Encoding)

Servers set the character encoding in the HTTP response headers, indicating how the content should be interpreted by the browser.

* **Content-Type Header**: Include a `Content-Type` HTTP header in the response, specifying the character encoding to be used.

* **Server Configuration**: Web server configurations can be set to specify the default character encoding for responses. For example, Apache HTTP Server can be configured to set the default character encoding for all responses.

### Browsers (Client-Side Decoding)

Browsers use encoding information sent by the server to decode and display the content correctly.

* **Content-Type Header**: When a browser receives an HTTP response, it checks the Content-Type header to determine the character encoding specified by the server.

* **Meta Tags**: A `<meta>` tag can be included within the HTML's `<head>` section to specify a page's character encoding.

	```
	<meta charset="UTF-8">
	```
