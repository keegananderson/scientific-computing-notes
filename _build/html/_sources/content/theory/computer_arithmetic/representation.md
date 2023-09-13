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
A *number system* is a set which consists of a finite quantity of unique
symbols.
A symbol of a number system is called a *numeral*.
A number system should
* be able to represent a given set of numbers fully,
* represent each number in the set of numbers uniquely, and
* reflect any algebraic or arithmetic structure imposed on the set.
```

```{topic} Definition
Let $b \in \mathbb{N}$.
A *base-$b$* number system consists of $b$ numerals which correspond to
$0$ and the first $b-1$ natural numbers, that is, $\{0,1,2,\dotsc,b-1\}$.
The number $b$ is called the *radix* of the number system.
```

Some well-known examples of number systems are:
* The *decimal number system* is a base-$10$ numeral system with
  base symbols $\mathbb{D} \equiv \{0,1,2,3,4,5,6,7,8,9\}$.
* The base-$2$ number system consisting of the numerals $\mathbb{B} \equiv
  \{0,1\}$ is called the *binary number system*.
* The base-$16$ number system $\mathbb{H}$ consisting of the numerals
  $\{0,1,2,3,4,5,6,7,8,9,A,B,C,D,E,F\}$
  is called the *hexadecimal number system*.
* The base-$8$ number system $\mathbb{O}$ with $\{0,1,2,3,4,5,6,7\}$
  as its base symbols is called the *octal number system*.

```{note}
  Our numerals must respect some type of ordering, which is
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
:label: eqn-positional-representation
  x = c_mb^m + c_{m-1}b^{m-1} + \dotsb + c_2b^2 + c_1b^1 + c_0b^0,
```
where $c_j \in \{0, 1, \dotsc, b-1\}$ with $j \in \{0,1,2,\dotsc,m\}$, $c_m \neq
0$ and $b^0 = 1$.
```{note}
  The coefficients $c_j$ are called *digits*.
  It is borrowd from the Latin word *digitus*, referring to a "finger,
  toe, or finger's breadth as a unit of measure", with fingers or
  toes being one of humanity's first counting aides.
```
The representation {eq}`eqn-positional-representation` may be shortened to the
notation
```{math}
:label: eqn-positional-notation
  n = c_mc_{m-1}\cdots c_2c_1c_0
```
which is the most common notation when we represent numbers.

The representation {eq}`eqn-positional-notation` is read right-to-left, starting
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
\eqref{eqn:positional-notation}, whereas the sums in
\eqref{eqn:positional-representation} are commutative and could have been
equivalently written as
\[
  n = c_0 + c_1b^1 + \dotsb + c_{m-1}b^{m-1} + c_mb^m.
\]
The strictness of the order of the numerals in \eqref{eqn:positional-notation}
becomes important when implementing number representations on the computer.

```{topic} Example
  The number $456$, in the decimal number system, may be written as
  $$
    456 = 4 \times 10^2 + 5 \times 10^1 + 6 \times 10^0.
  $$
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
subscript after the representation, that is, $n_b$ where $n$ is the number and
$b$ is the base of the specific number system.
Thus, in the last example, we could write $23_{10} = 10111_{2}$ which clarifies
that $10111$ is the binary representation of the number $23$ in the decimal
number system, and not the number $10111$ in the decimal number system.
Since the decimal number system is the most widely used, the subscript is often
not written for decimal numbers.

\section{Base conversions}
Conversion from decimal to any of the other important number systems (binary,
hexadecimal, octal) are done via repeated integer division.
Recall that any positive integer $n$ may be represented as $n = q \times b + r$
where $q$ is a positive integer called the \emph{quotient} and $r$ is a positive
integer called the \emph{remainder}.
The algorithm is as follows:
\begin{enumerate}[noitemsep, label=(\roman*), ref=\roman*, align=right]
  \item divide the decimal number successively by $b$,
  \item the remainders of the division are the coefficients of $b^0,\ b^1,\
    b^2,\ \dotsc$ (in that order).
\end{enumerate}
Conversion from a number system (binary, hexadecimal, octal) to decimal is done
by writing the number in positional representation
\eqref{eqn:positional-representation} and evaluating accordingly.

```{topic} Example
  Consider $456_{10}$.
  Then
  \[
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
  \]
  %\begin{align*}
  %  456/2 &= 228,  &\mbox{remainder} &= 0, & & \mbox{coefficient of}\ 2^0 = 0
  %  \\
  %  228/2 &= 114,  &\mbox{remainder} &= 0, & & \mbox{coefficient of}\ 2^1 = 0
  %  \\
  %  114/2 &= 57,  &\mbox{remainder} &= 0, & & \mbox{coefficient of}\ 2^2 = 0 \\
  %  57/2 &= 28, &\mbox{remainder} &= 1, & & \mbox{coefficient of}\ 2^3 = 1 \\
  %  28/2 &= 14, &\mbox{remainder} &= 0, & & \mbox{coefficient of}\ 2^4 = 0 \\
  %  14/2 &= 7, &\mbox{remainder} &= 0, & & \mbox{coefficient of}\ 2^5 = 0 \\
  %  7/2 &= 3, &\mbox{remainder} &= 1, & & \mbox{coefficient of}\ 2^6 = 1 \\
  %  3/2 &= 1, &\mbox{remainder} &= 1, & & \mbox{coefficient of}\ 2^7 = 1 \\
  %  1/2 &= 0, &\mbox{remainder} &= 1, & & \mbox{coefficient of}\ 2^8 = 1 \\
  %\end{align*}
  Therefore, $456_{10} = 111001000_{2}$.
```

```{topic} Example
  Consider $456_{10}$.
  Then
  \[
    \begin{array}{c|c|c|c|c}
      j\ \mbox{(step)} & n\ \mbox{(number)} & q\ \mbox{(quotient)} & r\
      \mbox{(remainder)} & c_j\ \mbox{(coefficient of}\ 16^j) \\
      \hline
      0 & 456 & 28 & 8 & 8 \\
      1 & 28 & 1 & 12 & C \\
      2 & 1 & 0 & 1 & 1
    \end{array}
  \]
  Therefore, $456_{10} = 1C8_{16}$.
```

```{topic} Example
  Consider $456_{10}$.
  Then
  \[
    \begin{array}{c|c|c|c|c}
      j\ \mbox{(step)} & n\ \mbox{(number)} & q\ \mbox{(quotient)} & r\
      \mbox{(remainder)} & c_j\ \mbox{(coefficient of}\ 8^j) \\
      \hline
      0 & 456 & 57 & 0 & 0 \\
      1 & 57 & 7 & 1 & 1 \\
      2 & 7 & 0 & 7 & 7
    \end{array}
  \]
  Therefore, $456_{10} = 710_{8}$.
```

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

