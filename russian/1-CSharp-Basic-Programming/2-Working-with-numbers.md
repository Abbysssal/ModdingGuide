### [НА ГЛАВНУЮ СТРАНИЦУ](../../README.md) ###

1. [Создание проекта в Visual Studio](./1-Creating-a-project-in-Visual-Studio.md);
2. **Работаем с числами**;
3. [Высказывания, выражения и операторы](./3-Statements-expressions-and-operators.md);
4. [Ветвление и циклы](./4-Branches-and-loops.md);

# Работаем с числами #

## Целочисленные типы ##

Тут есть 8 встроенных целочисленных типов: **`byte`, `sbyte`, `ushort`, `short`, `int`, `uint`, `long`, `ulong`**. Но только **`int`, `uint`, `long` и `ulong`** поддерживают основные арифметические операторы: **сложение (`+`), вычитание (`-`), умножение (`*`), деление (`/`) и остаток от деления (`%`)**.

Давайте напишем код ниже в `Main()`.

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

- `int a = 4;` объявляет переменную `a` со значением `4`;

- `int b = a * 12;` объявляет переменную `b` со значением `a`, умноженным на `12`;

- `Console.WriteLine(b);` выводит значение `b` в консоль;

Просто, не правда ли? Вы можете объединять несколько операторов в одной строке, если хотите.

```cs
public static void Main(/*string[] args*/)
{
    int a = 4;
    int b = a * 12;
    int c = a * b + 20 * b + 3;
    Console.WriteLine(c);
}
```

Порядок арифметических операторов такой же как и в математике: сначала умножение и деление, и потом сложение и вычитание.

```cs
int x = 10 * 3 + 20; // = (10 * 3) + 20 = 50
int y = 80 - 24 / 4; // = 80 - (24 / 4) = 72
```

Также вы можете использовать **скобки `(` `)`** для изменения порядка вычисления.

```cs
int x = 10 * (3 + 20); // = 230
int y = (80 - 24) / 4; // = 14
```

Иногда для вашего кода могут не понадобиться отрицательные целые числа. В таких случаях вы можете использовать **беззнаковые целочисленные типы: `byte`, `ushort`, `uint`, `ulong`**.

```cs
uint a = 1280;
byte b = -10; // Ошибка компиляции!
```

Для обозначения типа целого числа, используйте **суффиксы: `u`/`U` для `uint`, `l`/`L` для `long` и `ul`/`uL`/`Ul`/`UL`/`lu`/`lU`/`Lu`/`LU` для `ulong`**

```cs
uint a = 650u;
long b = 100200300L;
ulong c = 197777666UL;
```

***Примечание: не используйте строчную `l` в суффиксах. Её легко перепутать с цифрой `1` в текстовом редакторе. Вместо неё используйте заглавную `L`.***

Для лучшей читаемости вы можете использовать **нижнее подчёркивание `_` в качестве разделителя цифр** как для целочисленных типов, так и для типов с плавающей запятой.

```cs
int a = 19_122_872;
ulong b = 155_421__654___555____UL;

double c = 133.524_e-7_d;
```

Вы можете объявить целочисленный тип по его **двоичной или шестнадцатиричной записи** используя префиксы **`0b`/`0B` и `0x`/`0X`**.

```cs
byte a = 0B_0101_1100;
int b = 0b_0010_0100_1101;

int c = 0x_A5_4C_52;
ulong d = 0x_52_2D_FF_6AUL;
```

Возможно вы уже заметили, что **целочисленное деление возвращает только целую часть** от деления, а то есть возвращаемое значение остаётся целочисленным, `int`. Если вам нужно получить остаток от деления, используйте **оператор `%` (остаток от деления)**.

```cs
int quotient = 19 / 3; // возвращает 6 вместо 6.333...
int remainder = 19 % 3; // возвращает 1, остаток от деления
```

Если вам всё-таки нужна дробная часть, то вы должны использовать численные типы с плавающей запятой: **`float`, `double`, `decimal`**.

## Численные типы с плавающей запятой ##

При использовании типов с плавающей запятой, помните, что такой код: `double a = 19;` - берёт целое число `19` и присваивает его значение переменной `a` (неявно преобразуется из `int` в `double`).

В примере ниже видно, как целое число `19` делится на целое число `3`. Результатом деления будет целое число `6` (так как оба операнда - целые числа), поэтому переменной `a` будет присвоено значение `6.0`.

```cs
double a = 19 / 3;
```

Чтобы исправить это, используйте **десятичную точку `.`**. По умолчанию, типом будет `double`, но вы можете определить его с помощью **суффиксов: `f`/`F` для `float`, `d`/`D` для `double` и `m`/`M` для `decimal`**.

```cs
double a = 19.0 / 3.0; // без суффиксов

float c = 19.00f / 3F;

double b = 19.0d / 3D;

decimal d = 19m / 3.0M;
```

Если один из операндов - число с плавающей запятой, то результатом тоже будет число с плавающей запятой. *Но всё-таки стоит определять оба операнда как числа с плавающей запятой, чтобы избежать лишних приведений и сделать код более читаемым.*

```cs
double a = 19d / 3;
// эквивалентно
double a = 19d / (double)3;
```

Также вы можете использовать **экспоненциальное представление чисел**. Экспонента **`e`/`E`** пишется сразу после дробной части числа, но перед суффиксом.

```cs
float a = 1.32E-2f;
double b = 1.932e+6d;
decimal c = 1.9982e5m;
```

## Диапазоны численных типов ##

**Целочисленные типы**

| Ключевое слово C# | Диапазон                      | Размер            |
|:-----------|:-------------------------------------|------------------:|
| `byte`     | 0 — 255                              | 1 byte (8 bits)   |
| `sbyte`    | -128 — 127                           | 1 byte (8 bits)   |
| `ushort`   | 0 — 65 535                           | 2 bytes (16 bits) |
| `short`    | -32 768 — 32 767                     | 2 bytes (16 bits) |
| `uint`     | 0 — 4 294 967 295                    | 4 bytes (32 bits) |
| `int`      | -2 147 483 648 — 2 147 483 647       | 4 bytes (32 bits) |
| `ulong`    | 0 — 18 446 744 073 709 551 615       | 8 bytes (64 bits) |
| `long`     | -9 223 372 036 854 775 808 —<br/>— 9 223 372 036 854 775 807 | 8 bytes (64 bits) |

**Типы с плавающей запятой**

| Ключевое слово C# | Примерный диапазон | Точность      | Размер              |
|:-----------|:--------------------------|:--------------|--------------------:|
| `float`    | ±1.5×10⁻⁴⁵ — ±3.4×10³⁸    | ≈6–8 digits   | 4 bytes (32 bits)   |
| `double`   | ±5.0×10⁻³²⁴ — ±1.7×10³⁰⁸  | ≈15–17 digits | 8 bytes (64 bits)   |
| `decimal`  | ±1.0×10⁻²⁸ — ±7.9228×10²⁸ | 28–29 digits  | 16 bytes (128 bits) |

Вы можете получить минимальное и максимальное значения чисел с помощью констант их типов **`MinValue`, `MaxValue`**.

```cs
int min = int.MinValue; // = -2 147 483 648
int max - int.MaxValue; // =  2 147 483 647  

double min2 = double.MinValue; // ≈ -1.7×10³⁰⁸
double max2 = double.MaxValue; // ≈ +1.7×10³⁰⁸
```

## Следующее: 3. [Высказывания, выражения и операторы](./3-Statements-expressions-and-operators.md) ##