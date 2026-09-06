# Number Systems & Data Representation

Computers store and represent information using numbers.

* **Decimal (Base-10):** The number system humans normally use (0–9).
* **Binary (Base-2):** Used by computers and only contains `0` and `1`.
* **Hexadecimal (Base-16):** Uses `0–9` and `A–F`. One hexadecimal digit represents **4 bits**.
* **Octal (Base-8):** Uses `0–7`. One octal digit represents **3 bits**. It is less commonly used.

### Bits & Bytes

* **Bit:** A binary digit that can be `0` or `1`.
* **Byte:** 8 bits. Also called an **octet**.

### Hexadecimal & Colours

Colours can be represented using **RGB (Red, Green, Blue)**.

Each colour channel can use 1 byte, giving **3 bytes / 24 bits** per colour. This allows more than **16 million possible colours**.

### Key Things to Remember

* `1 byte = 8 bits`
* `1 hexadecimal digit = 4 bits`
* Binary uses `0` and `1`
* Hexadecimal uses `0–9` and `A–F`
* Computers ultimately store data as bits


# ASCII

**ASCII (American Standard Code for Information Interchange)** is a character encoding standard that gives characters a numeric value so computers can store and display text.

* Original ASCII uses **7 bits**.
* It can represent **128 values (0–127)**.
* It represents English letters, numbers, punctuation and control characters.
* Each character has its own numeric/hexadecimal code.

### Examples

| Character | Decimal |  Hex |
| --------- | ------: | ---: |
| `0`       |      48 | `30` |
| `A`       |      65 | `41` |
| `B`       |      66 | `42` |
| `a`       |      97 | `61` |
| `b`       |      98 | `62` |

Letters are assigned codes in order, so if I know the code for `A`, I can work out the codes for the other uppercase letters.

### Example: "TryHackMe"

Using ASCII, the text `TryHackMe` can be represented in hexadecimal as:

`54 72 79 48 61 63 6B 4D 65`

The computer stores the characters as bits, but hexadecimal is easier for humans to read.

### Important

ASCII mainly supports **English characters**. It does not have enough characters to represent all languages, which led to other character encodings such as the **ISO-8859** series and eventually **Unicode**.

If text is saved using one encoding but opened using another incompatible encoding, characters can appear as **gibberish**.

**Key takeaway:** ASCII is essentially a mapping between characters and numbers that allows computers to store and display text.


## Unicode

ASCII was mainly designed for English, so it could not represent characters from all languages.

**Unicode** is a universal character standard that assigns a unique **code point** to characters from different languages, symbols and emojis.

Examples:

* `U+0041` = `A`
* `U+03A9` = `Ω`
* `U+3042` = `あ`
* `U+1F525` = 🔥

Unicode allows different languages and emojis to be used in the same document or message.

### UTF-8, UTF-16 & UTF-32

These are different ways of **encoding Unicode characters into bytes**.

* **UTF-8:** Uses **1–4 bytes**. Very common on the modern web. ASCII characters use 1 byte.
* **UTF-16:** Uses **2 or 4 bytes**.
* **UTF-32:** Always uses **4 bytes** per Unicode code point, making it simple but less space-efficient.

### Encoding Problems

The sender and recipient need to interpret data using compatible encoding. If the wrong encoding is used, characters can appear as **gibberish or incorrect symbols**.

### Key Takeaways

* **ASCII** → mainly English, 128 characters.
* **Unicode** → supports characters from languages around the world, plus symbols and emojis.
* **Code point** → the unique number assigned to a Unicode character.
* **UTF-8/16/32** → different ways of storing Unicode characters as bytes.
* **UTF-8** is the most important one to recognise because it is widely used on the web.
