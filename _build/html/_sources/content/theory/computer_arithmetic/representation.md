# *b*-adic representation of numbers

## Number systems

Any algorithm in Scientific Computing, at its core, relies on the representation
of numbers on a computing device and then understanding how arithmetic and/or
algebraic operations are impacted by the specific representation.

Mathematically, numbers are elements of any of the following sets: 
$\mathbb{N} \subset \mathbb{Z} \subset \mathbb{Q} \subset \mathbb{R} \subset \mathbb{C}$.

These sets usually have some algebraic structure imposed on them in the form of
binary operations and certain axiomatic properties.
In this context, numbers are then represented using variables, for example, $x
\in \mathbb{R}$.
However, computing devices usually cannot interpret these symbolic
representation and the operations that can be performed on these numbers.

Numbers may also be represented via number systems.
Number systems are writing systems used to express numbers of a given set
using digits and/or mathematical notation.

```{topic} Definition
A *number system* is a mathematical writing system for expressing numbers.
It may be represented as a set which consists of a finite quantity of unique
symbols (called *numerals*), which should be able to
* represent a given set of numbers fully,
* represent each number in the set of numbers uniquely, and
* reflect any algebraic or arithmetic structure imposed on the set.
```

Some number systems (e.g., Egyptian, Mayan) use pictures to represent numerals,
while others (e.g., Roman, Japanese) use alphabet letters to represent numerals.
The most commonly used numerals $0,1,2,3,4,5,6,7,8,9$ are called *Arabic
numerals*, which originally developed from the Hindu-Arabic numeral system.

```{topic} Example
  The Roman numerals represent natural numbers as a combination of letters from
  the Latin alphabet:
  \begin{equation*}
    \begin{array}{c c c c c c c}
      \text{I} & \text{V} & \text{X} & \text{L} & \text{C} & \text{M} \\
      1 & 5 & 10 & 50 & 100 & 1000
    \end{array}
  \end{equation*}
  The first five natural numbers $1,2,3,4,5$ would be represented as I, II, III,
  IV, V.
```

```{topic} Definition
  A *base-$b$* number system consists of a set of $b$ numerals
  $\{d_1,d_2,\dotsc,d_b\}$ called *digits*.
```

```{note}
The term *digit* is borrowed from the Latin word *digitus*, referring to a
"finger, toe, or finger's breadth as a unit of measure", with fingers or
toes being one of humanity's first counting aides.
```

The *radix* $r$ is the number of unique digits, including zero, that number
system uses to represent numbers.
If we have a negative base, that is, $b < 0$, then we let $r = \lvert b\rvert$.

Usually, in an Arabic numeral based system, the digits $\{d_1, d_2, \dotsc,
d_b\}$ correspond to $0$ and the first $b-1$ natural numbers, that is,
$\{0,1,2,\dotsc,b-1\}$. 

```{topic} Example
Some well-known examples of Arabic numeral based number systems are:
* The *decimal number system* is a base-$10$ numeral system with
  base symbols $\mathbb{D} \equiv \{0,1,2,3,4,5,6,7,8,9\}$.
* The base-$2$ number system consisting of the numerals $\mathbb{B} \equiv
  \{0,1\}$ is called the *binary number system*.
* The base-$16$ number system $\mathbb{H}$ consisting of the numerals
  $\{0,1,2,3,4,5,6,7,8,9,A,B,C,D,E,F\}$
  is called the *hexadecimal number system*.
* The base-$8$ number system $\mathbb{O}$ with $\{0,1,2,3,4,5,6,7\}$
  as its base symbols is called the *octal number system*.
```

```{note}
  If the numbers we want to represent obey some type of ordering, then the
  numerals of the number system must also respect the same ordering, which is
  implied by the correspondence between the numerals of the number system to
  the natural numbers.
```

An example of a symbolic number system is the set $\{\lambda, \mu, \phi\}$, with
the correspondence
\begin{equation*}
\lambda  \to 0, \quad \mu \to 1, \quad \phi \to 2,
\end{equation*}
which implies $\lambda < \mu < \phi$.


## Positional notation

From our last example, with the number system $\{\lambda, \mu, \phi\}$,  we see
that we can represent the numbers $0$, $1$, and $2$ uniquely (as required per
definition).

But what if we want to represent $3$, $4$, $5$, etc?

Generally, only the first $b - 1$ natural numbers and zero may be represented
using the numerals in a base-$b$ number system.
The problem then is to represent numbers larger (or smaller in the sense of
fractions or negative numbers) than those that may be representated by the base
numerals.

We would either have to 
* introduce more symbols, which could lead to an infinite
  number of symbols since the natural numbers $\mathbb{N}$ is an infinite set
  (which contradicts our definition of a number system), or
* find a different notational representation of numbers using a finite set of
  numerals in a meaningful manner.

The most well-known method of representation is the so-called *positional
notation*, where significance is attached to a numeral depending on where it
appears in relation to other numerals.

%We either have to introduce more symbols or we have combine the symbols of the
%number system in some meaningful way to represent these larger numbers.
%The most well-known method of combination is the so-called positional
%notation---where significance is attached to a symbol depending on where it
%appears in relation to other symbols
%The most used method to combine the symbols in a meaningful way results in
%positional notation---where significance is attached to a symbol depending on
%where it appears in relation to other symbols.

Suppose that $x$ is a natural number, that is, $x \in \mathbb{N}_0$.
It can be shown, via induction, that each number $n$ may be represented in
a base-$b$ number system as
```{math}
:label: eqn:positional-representation
  x = c_mb^m + c_{m-1}b^{m-1} + \dotsb + c_2b^2 + c_1b^1 + c_0b^0,
```
where $c_j \in \{0, 1, \dotsc, b-1\}$ with $j \in \{0,1,2,\dotsc,m\}$, $c_m \neq
0$ and $b^0 = 1$.

The representation {eq}`eqn:positional-representation` may be shortened to the
notation
```{math}
:label: eqn:positional-notation
  n = c_mc_{m-1}\dotsm c_2c_1c_0
```
which is the most common notation when we represent numbers.

```{note}
The shortened positional representation $c_mc_{m-1}\dotsm c_2c_1c_0$ represents
the sequence of digits, not multiplication.
```

The representation {eq}`eqn:positional-notation` is read right-to-left, starting
from $c_0$ (called the *least-significant digit*) and ending with $c_m$
(called the *most-significant digit*).

```{note}
  Numbers in positional notation are read from right to left in most Western
  cultures and societies (while regular text is read from left to right)
  However, there are cultures and societies which do not follow this convention.
  For example, some Asian cultures use a writing system that writes text
  vertically, from top to bottom, and from right to left.
```
Note that numbers are always read from right to left in the notation
{eq}`eqn:positional-notation`, whereas the sums in
{eq}`eqn:positional-representation` are commutative and could have been
equivalently written as
\begin{equation*}
  n = c_0 + c_1b^1 + \dotsb + c_{m-1}b^{m-1} + c_mb^m.
\end{equation*}
The strictness of the order of the numerals in {eq}`eqn:positional-notation`
becomes important when implementing number representations on the computer.

```{topic} Example
  The number $456$, in the decimal number system, may be written as
  $456 = 4 \times 10^2 + 5 \times 10^1 + 6 \times 10^0$.
```
```{topic} Example
  The number $23$ (in decimal) has the binary representation $10111$, since
  \begin{align*}
    10111 &= 1 \times 2^4 + 0 \times 2^3 + 1 \times 2^2 + 1 \times 2^1 + 1
    \times 2^0 \\
    &= 1 \times 16 + 0 \times 8 + 1 \times 4 + 1 \times 2 + 1 \times 1 \\
    &= 16 + 4 + 2 + 1 \\
    &= 23
  \end{align*}
```
As this previous example has shown, confusion might arise in reading number
representations. The representation $10111$ is the number $23$ in binary, but
also the number $10111$ in the decimal number system.
We distinguish the representation of the number by writing the base as a
subscript after the representation, that is, 
\begin{equation*}
  n_b = (c_mc_{m-1}\dotsm c_2c_1c_0)_b,
\end{equation*}
where $n$ is the number, $c_j$ ($j \in \{1,2,\dotsc,m\}$) are the digits, and
$b$ is the base of the specific number system.

Thus, in the last example, we could write $23_{10} = 10111_{2}$ which clarifies
that $10111$ is the binary representation of the number $23$ in the decimal
number system, and not the number $10111$ in the decimal number system.
Since the decimal number system is the most widely used, the subscript is often
not written for decimal numbers.


## Base conversions
Conversion from decimal to any of the other important number systems (binary,
hexadecimal, octal) are done via repeated integer division.
Recall that any natural number $n$ may be represented as $n = q \times b + r$
where $q$ is a natural number called the *quotient* and $r$ is a natural number 
called the *remainder*.
The algorithm is as follows:
* divide the decimal number successively by $b$,
* the remainders of the division are the coefficients of $b^0,\ b^1,\ b^2,\ \dotsc$ (in that order).

```{topic} Example
  Consider $456_{10}$.
  Then
  \begin{equation*}
    \begin{array}{c|c|c|c|c}
      j\ \mbox{(step)} & n\ \mbox{(number)} & q\ \mbox{(quotient)} & r\
      \mbox{(remainder)} & c_j\ \mbox{(coefficient of}\ 2^j) \\
      \hline
      0 & 456 & 228 & 0 & 0 \\
      1 & 228 & 114 & 0 & 0 \\
      2 & 114 & 57 & 0 & 0 \\
      3 & 57 & 28 & 1 & 1 \\
      4 & 28 & 14 & 0 & 0 \\
      5 & 14 & 7 & 0 & 0 \\
      6 & 7 & 3 & 1 & 1 \\
      7 & 3 & 1 & 1 & 1 \\
      8 & 1 & 0 & 1 & 1
    \end{array}
  \end{equation*}
  Therefore, $456_{10} = 111001000_{2}$.
```

```{topic} Example
  Consider $456_{10}$.
  Then
  \begin{equation*}
    \begin{array}{c|c|c|c|c}
      j\ \mbox{(step)} & n\ \mbox{(number)} & q\ \mbox{(quotient)} & r\
      \mbox{(remainder)} & c_j\ \mbox{(coefficient of}\ 16^j) \\
      \hline
      0 & 456 & 28 & 8 & 8 \\
      1 & 28 & 1 & 12 & C \\
      2 & 1 & 0 & 1 & 1
    \end{array}
  \end{equation*}
  Therefore, $456_{10} = 1C8_{16}$.
```

```{topic} Example
  Consider $456_{10}$.
  Then
  \begin{equation*}
    \begin{array}{c|c|c|c|c}
      j\ \mbox{(step)} & n\ \mbox{(number)} & q\ \mbox{(quotient)} & r\
      \mbox{(remainder)} & c_j\ \mbox{(coefficient of}\ 8^j) \\
      \hline
      0 & 456 & 57 & 0 & 0 \\
      1 & 57 & 7 & 1 & 1 \\
      2 & 7 & 0 & 7 & 7
    \end{array}
  \end{equation*}
  Therefore, $456_{10} = 710_{8}$.
```

Conversion from a number system (binary, hexadecimal, octal) to decimal is done
by writing the number in positional representation
{eq}`eqn:positional-representation` and evaluating accordingly.


```{topic} Example
  Consider $10101010_2$.
  Then
  \begin{align*}
    10101010_2 &= 1 \times 2^7 + 0 \times 2^6 + 1 \times 2^5 + 0 \times 2^4 + 1
    \times 2^3 + 0 \times 2^2 + 1 \times 2^1 + 0 \times 2^0 \\
    &= 128 + 32 + 8 + 2 \\
    &= 170_{10}
  \end{align*}
```
```{topic} Example
  Consider $BC19_{16}$.
  Then
  \begin{align*}
    BC19_{16} &= B \times 16^3 + C \times 16^2 + 1 \times 16^1 + 9 \times 16^0
    \\
    &= 11 \times 4096 + 12 \times 256 + 16 + 9 \\
    &= 45056 + 3072 + 16 + 9 \\
    &= 48153_{10}
  \end{align*}
```

## Other representations

In the previous section, we saw how we could represent natural numbers using the
positional notation that we introduced, and how we could convert the
representation of such natural numbers in different bases.

The question arises:
> How do we represent other types of numbers (e.g., integer, rational, or real
> numbers) in this positional notation?

### Integer number representation

The number zero, denoted by $0$, is the unique number such that
\begin{equation*}
    n + 0 = 0 + n = n,
\end{equation*}
for all natural numbers $n \in \mathbb{N}$.
```{note}
  This is the algebraic definition of zero.
  In the algebraic context, zero is called the *additive identity*.
```

```{note}
  The number zero is not necessarily the same as the digit zero. 
  The digit zero is used to represent the "skipping" of a position in positional
  number systems.
```

The negative natural numbers may be defined as the set of numbers obtained from
the natural numbers by appending the symbol $-$ left of the most-significant
digit, that is,
\begin{equation*}
  \mathbb{N}^- = \{ n \in \mathbb{N} \mid -n\} = \{-1,-2,-3,\dotsc\}.
\end{equation*}

```{note}
  The definition of negative numbers is actually more involved, but ours will
  suffice for talking about integers.
```

To distinguish the natural numbers from the negative natural numbers even more,
we may also write the natural numbers as follows:
\begin{equation*}
  \mathbb{N}^+ = \{ n \in \mathbb{N} \mid +n\} = \{+1, +2, +3, \dotsc\}.
\end{equation*}

```{topic} Definition
  The attribute of a number being written either as $0$, or with a $+$ or $-$
  added left of the most-significant digit, is called its *sign*.
```

```{topic} Definition.
  An *integer* is a number that can either be 
  * a zero (0), 
  * a natural number $\{1,2,3,\dotsc\}$, or 
  * a negative natural number $\{-1,-2,-3,\dotsc\}$.
  The set of all integers is denoted by $\mathbb{Z}$.
```

There is an ordering of the integers given by
\begin{equation*}
    \dotsb < -3 < -2 < -1 < 0 < 1 < 2 < 3 < \dotsb.
\end{equation*}
Integers larger than zero are called *strictly positive*, and integers smaller
than zero are called *strictly negative*.

It should be easily seen that we may still use
{eq}`eqn:positional-representation` to represent integers, but with an extra
symbol of either $+$ and $-$, left of the most-significant digit, to represent
whether the integer is positive or negative.

```{note}
For positive numbers, we usually omit the $+$ symbol.
```

More abstractly, we introduce the symbol $\sigma$ which may take the value of
either $+1$ or $-1$, that is, $\sigma \in \{-1, 1\}$, which allows us to
represent $x \in \mathbb{Z}$ as
\begin{equation*}
  x = \sigma(c_mc_{m-1}\dotsm c_2c_1c_0)_b.
\end{equation*}

### Rational number representation

```{topic} Definition.
  A *rational number* is a number of the form $\frac{a}{b}$ where
  $a,b\in\mathbb{Z}$.
```
The set of all rational numbers is denoted by $\mathbb{Q}$.

### Real number representation

