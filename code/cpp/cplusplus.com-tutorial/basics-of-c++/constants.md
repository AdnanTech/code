# Constants

## Constants

Constants are expressions with a fixed value. The way I understand constants to be, are assigned values from variables, so the relationship can be worded as identifer and constant rather than variable and parameter.

### Literals

Literal constants can be classified into: integer, floating-point, characters, strings, Boolean, pointers, and user-defined literals. some examples include

* `a = 5` \(5 is the literal constant\)
* `75` \(Decimal\)
* `0113` \(Octal\)
* `0x4b` \(Hexadecimal\)

### Suffixes

Suffixes can also be added to the end of literals to define the type of their specfic data type. For example

```cpp
75         // int
75u        // unsigned int
75l        // long
75ul       // unsigned long 
75lu       // unsigned long
75ll       // long long
```

Where the 'u' or 'l' can be capitalised, as well as long has the ability to be appended to an unsigned literal. 

### Long & Double

Long \(decimal\) numbers and doubles can be represented like so:

```cpp
3.14159L   // long double
6.02e23f   // float


3.14159    // 3.14159
6.02e23    // 6.02 x 10^23
1.6e-19    // 1.6 x 10^-19
3.0        // 3.0 
```

### **Character & String**

There are single character literals as well as string literals, which can be represented like so:

* `'z', 'p'`
* `"Hello world", "How do you do?"`

The quotation marks are vital to tell the machine that the expression is NOT an identifier, and is a \(character\) string literal instead.

### Escape Codes

![](../../../../.gitbook/assets/image%20%281%29.png)

### String Concatenation

Several string literals can be concatenated to form a single string literal simply by separating them by one or more blank spaces, including tabs, newlines, and other valid blank characters. For example:

```cpp
"this forms" "a single"     " string "
"of characters"

// is the same as

"this formsa single string of characters"
```

### Line Continuation

Line continuations in C++ can be performed with backslash, for example:

```cpp
x = "string expressed in \
two lines"

// is the same as

x = "string expressed in two lines"
```

### Character Types

Characters and strings are made of up the data type char. This means that in C++, they can have special prefixes

![](../../../../.gitbook/assets/image%20%282%29.png)

The table above shows 16 bit characters, 32 bit characters and wide characters.

### String types

On top of the character type prefixes, there are a couple string prefixes, that can have character prefixes appended onto the them:

![](../../../../.gitbook/assets/image%20%283%29.png)

So for a raw string:

```cpp
R"(string with \backslash)"
R"&%$(string with \backslash)&%$"

// both produce the output "string with \\backslash"
```

### Consant expressions

These are essentially global, constant variables, it is bad practice to add any, but they can be represented like so:

```cpp
const double pi = 3.1415926;
const char tab = '\t';
```

### define

We can also declare preprocessor definitions, the general form is: `#define identifier replacement`  
, they are usually typed in all upper case, a couple examples:

```cpp
#define PI 3.14159
#define NEWLINE '\n'
```

