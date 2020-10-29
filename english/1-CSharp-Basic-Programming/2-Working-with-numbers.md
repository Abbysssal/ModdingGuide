### [BACK TO THE MAIN PAGE](../../README.md) ###

1. [Creating a project in Visual Studio](./1-Creating-a-project-in-Visual-Studio.md);
2. **Working with numbers**;
3. [Statements, expressions and operators](./3-Statements-expressions-and-operators.md);

# Working with numbers #

## Integral numeric types ##

There are 8 built-in integral numeric types: **`byte`, `sbyte`, `ushort`, `short`, `int`, `uint`, `long`, `ulong`**. But only **`int`, `uint`, `long` and `ulong`** support basic arithmetic operators: **addition (`+`), subtraction (`-`), multiplication (`*`), division (`/`) and remainder (`%`)**.

Let's write the code below in `Main()`.

```cs
...
public static void Main(/*string[] args*/)
{
    int a = 4;
    int b = a * 12;
    Console.WriteLine(b);
}
...
```

- `int a = 4;` declares a variable `a` with a value of `4`;

- `int b = a * 12;` declares a variable `b` with a value of `a` multiplied by `12`;

- `Console.WriteLine(b);` outputs the value of `b` to the console;

Easy, right? You can combine multiple operators in a single line, if you want.

```cs
public static void Main(/*string[] args*/)
{
    int a = 4;
    int b = a * 12;
    int c = a * b + 20 * b + 3;
    Console.WriteLine(c);
}
```

The order of arithmetic operators is the same as in mathematics: first multiplication and division, and then addition and subtraction.

```cs
int x = 10 * 3 + 20; // = (10 * 3) + 20 = 50
int y = 80 - 24 / 4; // = 80 - (24 / 4) = 72
```

You can also use **parenthesis `(` `)`** to modify the evaluation order.

```cs
int x = 10 * (3 + 20); // = 230
int y = (80 - 24) / 4; // = 14
```

Sometimes your code won't require usage of negative integers. In cases like this you can use **unsigned integral numeric types: `byte`, `ushort`, `uint`, `ulong`**.

```cs
uint a = 1280;
byte b = -10; // Compiler error!
```

To specify the type of an integer number, you should use **suffixes: `u`/`U` for `uint`, `l`/`L` for `long` and `ul`/`uL`/`Ul`/`UL`/`lu`/`lU`/`Lu`/`LU` for `ulong`**.

```cs
uint a = 650u;
long b = 100200300L;
ulong c = 197777666UL;
```

***Note: don't use lowercase `l` in suffixes. It can be easily confused with a digit `1` in the text editor. Use uppercase `L` instead.***

For better readability, you can use **underscore `_` as a digit separator** for both integral and floating-point numbers.

```cs
int a = 19_122_872;
ulong b = 155_421__654___555____UL;

double c = 133.524_e-7_d;
```

You can also declare integral numeric types by their **binary and hexadecimal forms** using **`0b`/`0B` and `0x`/`0X` prefixes**.

```cs
byte a = 0B_0101_1100;
int b = 0b_0010_0100_1101;

int c = 0x_A5_4C_52;
ulong d = 0x_52_2D_FF_6AUL;
```

You might have already noticed, that **integer division returns only the integral part** of the result, so that the return value stays an integer, `int`. If you need to get a remainder of the division, use **`%` (remainder) operator**.

```cs
int quotient = 19 / 3; // returns 6 instead of 6.333...
int remainder = 19 % 3; // returns 1, remainder of the division
```

If you need the fractional part as well, then you should use floating-point numeric types: **`float`, `double`, `decimal`**.

## Floating-point numeric types ##

When using floating-point types, you should keep in mind that this code: `double a = 19;` - takes an integer `19` and assigns its value to a variable `a` (it's implicitly converted from `int` to `double`).

In an example below you can see that an integer `19` is divided by an integer `3`. The result of the division is an integer `6` (because both operands are integers), so the variable `a` will have a value of `6.0`.

```cs
double a = 19 / 3;
```

To fix this issue, use a **decimal point `.`**. By default, the type will be `double`, but you can specify it with **suffixes: `f`/`F` for `float`, `d`/`D` for `double` and `m`/`M` for `decimal`**.

```cs
double a = 19.0 / 3.0; // without suffixes

float c = 19.00f / 3F;

double b = 19.0d / 3D;

decimal d = 19m / 3.0M;
```

If one of the operands is a floating-point number, then the result will be a floating-point number too. *But you should declare both operands as floating-point anyway to avoid unnecessary cast and make the code more readable by others.*

```cs
double a = 19d / 3;
// is equivalent to
double a = 19d / (double)3;
```

You can also use **scientific notation**. Exponent **`e`/`E`** is typed after the fractional part of the number, but before the suffix.

```cs
float a = 1.32E-2f;
double b = 1.932e+6d;
decimal c = 1.9982e5m;
```

## Ranges of numeric types ##

**Integral numeric types**

| C# keyword | Range                                | Size              |
|:-----------|:-------------------------------------|------------------:|
| `byte`     | 0 — 255                              | 1 byte (8 bits)   |
| `sbyte`    | -128 — 127                           | 1 byte (8 bits)   |
| `ushort`   | 0 — 65 535                           | 2 bytes (16 bits) |
| `short`    | -32 768 — 32 767                     | 2 bytes (16 bits) |
| `uint`     | 0 — 4 294 967 295                    | 4 bytes (32 bits) |
| `int`      | -2 147 483 648 — 2 147 483 647       | 4 bytes (32 bits) |
| `ulong`    | 0 — 18 446 744 073 709 551 615       | 8 bytes (64 bits) |
| `long`     | -9 223 372 036 854 775 808 —<br/>— 9 223 372 036 854 775 807 | 8 bytes (64 bits) |

**Floating-point numeric types**

| C# keyword | Approximate range         | Precision     | Size                |
|:-----------|:--------------------------|:--------------|--------------------:|
| `float`    | ±1.5×10⁻⁴⁵ — ±3.4×10³⁸    | ≈6–8 digits   | 4 bytes (32 bits)   |
| `double`   | ±5.0×10⁻³²⁴ — ±1.7×10³⁰⁸  | ≈15–17 digits | 8 bytes (64 bits)   |
| `decimal`  | ±1.0×10⁻²⁸ — ±7.9228×10²⁸ | 28–29 digits  | 16 bytes (128 bits) |

You can get the minimum and maximum values of numeric types through their type's **`MinValue`, `MaxValue` constants**.

```cs
int min = int.MinValue; // = -2 147 483 648
int max - int.MaxValue; // =  2 147 483 647  

double min2 = double.MinValue; // ≈ -1.7×10³⁰⁸
double max2 = double.MaxValue; // ≈ +1.7×10³⁰⁸
```

## Next: 3. [Statements, expressions and operators](./3-Statements-expressions-and-operators.md) ##