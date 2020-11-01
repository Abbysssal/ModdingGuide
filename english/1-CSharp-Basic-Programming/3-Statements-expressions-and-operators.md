### [BACK TO THE MAIN PAGE](../../README.md) ###

1. [Creating a project in Visual Studio](./1-Creating-a-project-in-Visual-Studio.md);
2. [Working with numbers](./2-Working-with-numbers.md);
3. **Statements, expressions and operators**;
4. [Branches and loops](./4-Branches-and-loops.md);

# Statements, expressions and operators #

All actions that the C# code describes are written as **statements**. Statements are separated by **a semicolon `;`**. There are also **statement blocks**, they are enclosed in **`{` `}` brackets** and can contain multiple statements.

```cs
int a = 1;

{
    Console.WriteLine("Bazinga.");

    {
        int d = 2;
    }
    int e = 3;
}
```

**Expressions** are combinations of operators that return some kind of value (or sometimes they don't, when methods return `void`, aka. nothing).

**Operators** allow you to perform different kinds of operations on values.

**Literals** describe values, like numbers or strings.

```cs
int a = 524 + 300;
// "524" and "300" are numeric literals
// "+" is an operator
// "524 + 300" is an expression, that returns 824
// "int a = 524 + 300" is a statement (without the semicolon ';')

char b = '%'; // "'%'" is a character literal

string textOne, textTwo;
textTwo = textOne = "nemo nisi per amicitiam cognoscitur";
// `"nemo nisi per amicitiam cognoscitur"` is a string literal
// the second "=" is an assignment operator
// `textOne = "..."` is an expression, that returns "..."
// `textTwo = textOne = "..."` is a statement
```

Operators are usually separated into 6 categories:

- Arithmetic operators;
- Equality operators;
- Comparison operators;
- Logical operators;
- Bitwise operators;
- Assignment operators;

There is a lot more operators, than I described below, you'll find more in the next guides.

## Arithmetic operators ##

- **Addition (`+`) operator** returns the sum of its operands;
- **Subtraction (`-`) operator** subtracts the right operand from the left one and returns the result;
- **Multiplication (`*`) operator** returns the product of its operands;
- **Division (`/`) operator** divides the left operand by the right one and returns the result;
- **Remainder (`%`) operator** divides the left operand by the right one and returns the remainder of the division;<br/><br/>
- **Unary plus (`+`) operator** returns the value of the operand;
- **Unary minus (`-`) operator** negates the operand and returns the result;<br/><br/>
- **Increment (`++`) operator** increments the operand by 1 (can be used as a statement);
  - *Postfix increment operator (`i++`):* returns the operand, and then increments it by 1;
  - *Prefix increment operator (`++i`):* increments the operand by 1, and then returns it;
- **Decrement (`--`) operator** decrements its operand by 1 (can be used as a statement);
  - *Postfix decrement operator (`i--`):* returns the operand, and then decrements it by 1;
  - *Prefix decrement operator (`--i`):* decrements the operand by 1, and then returns it;

```cs
int a = (17 + 23 * 2) / (12 - 35 / 7); // = 9
int b = 31 / 7; // = 4
int c = 31 % 7; // = 3

int d = +5;  // = 5
int e = -79; // = -79

int f = 1;
int g = f; // 1
g = f++;   // 1
g = f;     // 2
g = f--;   // 2
g = f;     // 1
g = ++f;   // 2
g = f;     // 2
g = --f;   // 1
g = f;     // 1
```

## Equality operators ##

- **Equality (`==`) operator** returns `true` if the operands are equal;
- **Inequality (`!=`) operator** returns `true` if the operands are not equal;

```cs
bool a = 19 == 19; // true
bool b = 67 != 12; // true
bool c = 4.52_0d == 4.52; // true
bool d = "text" != "text"; // false
```

## Comparison operators ##

- **Less than (`<`) operator** returns `true` if the left operand is less than the right one;
- **Greater than (`>`) operator** returns `true` if the left operand is greater than the right one;
- **Less than or equal to (`<=`) operator** returns `true` if the left operand is less than or equal to the right one;
- **Greater than or equal to (`>=`) operator** returns `true` if the left operand is greater than or equal to the right one;

```cs
bool a = 15 < 16;  // true
bool b = 65 <= 14; // false
bool c = 14 > 14;  // false
bool d = 67 >= 67; // true
```

## Logical operators ##

- **Logical negation (`!`) operator** returns `true` if the operand is `false`; otherwise, returns `false`;
- **Conditional AND (`&&`) operator** returns `true` if both operands are `true` (if the left operand is `false`, does not evaluate the right one);
- **Conditional OR (`||`) operator** returns `true` if at least one operand is `true` (if the left operand is `true`, does not evaluate the right one);<br/><br/>
- **Logical AND (`&`) operator** returns `true` if both operands are `true` (evaluates **both** operands);
- **Logical OR (`|`) operator** returns `true` if at least one operand is `true` (evaluates **both** operands);
- **Logical XOR (`^`) operator** returns `true` if operands are different; for `bool`s produces the same result as the inequality (`!=`) operator;<br/><br/>
- **Conditional (`?` `:`) operator**: if the first operand evaluates to `true`, evaluates and returns the second operand; otherwise, evaluates and returns the third operand.

```cs
bool a = true;
bool b = false;
bool c = !a; // = false

bool d = a && b; // evaluates both operands, because a is true
bool e = a || b; // evaluates only the left operand, because if a is true ⊃ the result can be only true

int f = 5 < 6 ? 10 : 20; // 5 < 6 evaluates to true; f = 10
string s = "34 < 20: " + (34 < 20 ? "yes" : "no"); // "34 < 20: no"
// "(34 < 20 ? "yes" : "no")" evaluates to "no", because "34 < 20" is false
```

## Bitwise operators ##

- **Bitwise complement (`~`) operator** returns the bitwise complement of the operand; *does the logical negation (`!`) for every bit in the number*;
- **Logical AND (`&`) operator** returns the bitwise logical AND of the operands; *does the logical AND (`&`) for every bit in the number*;
- **Logical OR (`|`) operator** returns the bitwise logical OR of the operands; *does the logical OR (`|`) for every bit in the number*;
- **Logical XOR (`^`) operator** returns the bitwise logical XOR of the operands; *does the logical XOR (`^`) for every bit in the number*;<br/><br/>
- **Left shift (`<<`) operator** returns the left operand shifted left by the number of bits specified by the right operand;
- **Right shift (`>>`) operator** returns the left operand shifted right by the number of bits specified by the right operand;

```cs
uint a = 0b_0010_1101;
uint b = 0b_1011_1001;

uint c = ~a;     // 0b_11111111_11111111_11111111_1101_0010
uint d = a & b;  // 0b_0010_1001
uint e = a | b;  // 0b_1011_1101
uint f = a ^ b;  // 0b_1001_0100

uint x = a << 5; // 0b_0010_1101_00000
uint y = a >> 2; // 0b_00_0010_11
```

***Note:** using shift operators on **signed** numeric types performs an **arithmetical shift** (without moving the sign bit). If you need to perform a **logical shift** (moving all bits), explicitly cast your number to its unsigned counterpart (its binary representation will stay the same) and then use the shift operator.*

```cs
int a = -5;
uint b = (uint)a;

uint c = b >> 4;
```

## Assignment operators ##

**Assignment (`=`) operator** assigns the value of the right operand to the left operand (can be used as a statement). Returns the value of the right operand.

```cs
a = b = c = d;
// Is equivalent to
c = d;
b = c;
a = b;

bool e;
if (e = 67 < 98) ...
```

For almost every binary operator `op` there is a compound assignment operator:

```cs
a op= 10;
// Is equivalent to
a = a op 10;

a op= b op= c;
// Is equivalent to
a = a op (b = b op c);
```

```cs
int a = 50;

a += 20;
a /= 10;
a <<= 5;
a ^= 123456;
```

## The operator precendence table ##
| Operators                           | Category        |
|-------------------------------------|-----------------|
| `x.y`, `f(x)`, `a[i]`, `x?.y`, `x?[y]`, `x++`, `x--`, `x!`, `new`, `typeof`, `checked`, `unchecked`, `default`, `nameof`, `delegate`, `sizeof`, `stackalloc`, `x->y` | Primary |
| `+x`, `-x`, `!x`, `~x`, `++x`, `--x`, `^x`, `(T)x`, `await`, `&x`, `*x`, `true`, `false` | Unary |
| `x..y` | Range |
| `switch` | `switch` expression |
| `x * y`, `x / y`, `x % y` | Multiplicative |
| `x + y`, `x - y` | Additive |
| `x << y`, `x >> y` | Shift |
| `x < y`, `x > y`, `x <= y`, `x >= y`, `is`, `as` | Comparison and type-testing |
| `x == y`, `x != y` | Equality |
| `x & y` | Logical AND |
| `x ^ y` | Logical XOR |
| `x | y` | Logical OR |
| `x && y` | Conditional AND |
| `x || y` | Conditional OR |
| `x ?? y` | Null-coalescing operator |
| `c ? t : f` | Conditional operator |
| `x = y`, `x op= y`, `x => y` | Assignment and lambda |

## Next: 4. [Branches and loops](./4-Branches-and-loops.md) ##