Python, in the simplest sense, allows for both *integers* and *floating-point* numbers, each to an infinite size, and floating-points to an infinitely deep precision point (or at least as deep as CPU memory will allow).  It's worth noting that floating-point numbers are those with fractional parts, generally called *floats* in programming languages for short.  Python also supports integers in **octal**, **hexidecimal**, and **binary literal***, which allows for some complex numbers.

##Integer and Floating-Point Literals##

Integers are written as strings of decimal digits, while floats have a decimal point and an optional exponent introduced by an `e` or `E`, and an optional sign.  Any number written literally with a decimal or exponent will be treated in Python as a float, not an integer.

##2.6 vs 3.0 - Normal and Long##

In Python 2.6, integers are either considered *normal* (32 bits) or long (unlimited precision).  To force a long type, an integer may end in `l` or `L` should its length fall below 32 bits.  If it is longer, it is automatically converted to long.

 Conversely, in Python 3 the normal and long format are merged.  There is only one integer, which automatically supports unlimited precision.  Because of this, integers can no longer be coded with a trailing `l` or `L`.

##Hexidecimal, Octal, and Binary##

Integers may be coded in *decimal* (base 10), *hexidecimal* (base 16), *octal* (base 8), or *binary* (base 2).

Hexidecimal literals start with the characters `0x` or `0X`, and are written with any character `0-9` and `A-F` afterward.  They may also be written in uppercase or lowercase.

Octal literals start with a leading `0o` or `0O`, and are written with any character `0-7`.

Binary literals start with a leading `0b` or `0B`, and are written written with either a `0` or a `1`.

Each of these is a different syntax for writing the same value in programmatic terms.  Using the built-in functions `hex(I)`, `oct(I)`, and `bin(I)` will convert the integer `I` to the indicated syntactical format.  To convert a string to an integer in a given base, you would use the built-in function `int(str, base)`.

