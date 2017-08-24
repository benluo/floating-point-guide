--- 
title: Binary Fractions
description: In-depth explanation of how binary fractions work, what problems the cause and why they are used anyway
---

How they work
-------------
As a programmer, you should be familiar with the concept of binary integers, i.e.
the representation of integer numbers as a series of bits:

<table>
<tr><th colspan="9">Decimal (<span class="num_base">base 10</span>)</th><th> </th><th colspan="17">Binary (<span class="num_base">base 2</span>)</th></tr>
<tr class="base_example">
<td class="digit">1</td><td>&sdot;</td><td class="num_base">10<sup>1</sup></td><td>+</td>
<td class="digit">3</td><td>&sdot;</td><td class="num_base">10<sup>0</sup></td><td>=</td>
<td class="digit">13<sub class="num_base">10</sub></td><td class="separator">=</td>
<td class="digit">1101<sub class="num_base">2</sub></td><td>=</td>
<td class="digit">1</td><td>&sdot;</td><td class="num_base">2<sup>3</sup></td><td>+</td>
<td class="digit">1</td><td>&sdot;</td><td class="num_base">2<sup>2</sup></td><td>+</td>
<td class="digit">0</td><td>&sdot;</td><td class="num_base">2<sup>1</sup></td><td>+</td>
<td class="digit">1</td><td>&sdot;</td><td class="num_base">2<sup>0</sup></td>
</tr><tr class="base_example">
<td class="digit">1</td><td>&sdot;</td><td>10</td><td>+</td>
<td class="digit">3</td><td>&sdot;</td><td>1 </td><td>=</td>
<td class="digit">13<sub class="num_base">10</sub></td><td class="separator">=</td>
<td class="digit">1101<sub class="num_base">2</sub></td><td>=</td>
<td class="digit">1</td><td>&sdot;</td><td>8</td><td>+</td>
<td class="digit">1</td><td>&sdot;</td><td>4</td><td>+</td>
<td class="digit">0</td><td>&sdot;</td><td>2</td><td>+</td>
<td class="digit">1</td><td>&sdot;</td><td>1</td>
</tr></table>

This is how computers store integer numbers internally. And for fractional numbers in [positional notation](http://en.wikipedia.org/wiki/Positional_notation), they do the same thing:

<table>
<tr><th colspan="13">Decimal (<span class="num_base">base 10</span>)</th><th> </th><th colspan="13">Binary (<span class="num_base">base 2</span>)</th></tr>
<tr class="base_example">
<td class="digit">6</td><td>&sdot;</td><td class="num_base">10<sup>-1</sup></td><td>+</td>
<td class="digit">2</td><td>&sdot;</td><td class="num_base">10<sup>-2</sup></td><td>+</td>
<td class="digit">5</td><td>&sdot;</td><td class="num_base">10<sup>-3</sup></td><td>=</td>
<td class="digit">0.625<sub class="num_base">10</sub></td><td class="separator">=</td>
<td class="digit">0.101<sub class="num_base">2</sub></td><td>=</td>
<td class="digit">1</td><td>&sdot;</td><td class="num_base">2<sup>-1</sup></td><td>+</td>
<td class="digit">0</td><td>&sdot;</td><td class="num_base">2<sup>-2</sup></td><td>+</td>
<td class="digit">1</td><td>&sdot;</td><td class="num_base">2<sup>-3</sup></td>
</tr><tr class="base_example">
<td class="digit">6</td><td>&sdot;</td><td>1/10</td><td>+</td>
<td class="digit">2</td><td>&sdot;</td><td>1/100</td><td>+</td>
<td class="digit">5</td><td>&sdot;</td><td>1/1000</td><td>=</td>
<td class="digit">0.625<sub class="num_base">10</sub></td><td class="separator">=</td>
<td class="digit">0.101<sub class="num_base">2</sub></td><td>=</td>
<td class="digit">1</td><td>&sdot;</td><td>1/2</td><td>+</td>
<td class="digit">0</td><td>&sdot;</td><td>1/4</td><td>+</td>
<td class="digit">1</td><td>&sdot;</td><td>1/8</td>
</tr></table>

Problems
--------
While they work the same in principle, binary fractions are different from decimal fractions in what
numbers they can accurately represent with a given number of digits, and thus also in what numbers result in [rounding errors](/errors/rounding/):

Specifically, binary can only represent those numbers as a finite fraction where the denominator
is a power of 2. Unfortunately, this does not include most of the numbers that can be 
represented as finite fraction in base 10, like 0.1.

| Fraction | Base | Positional Notation | Rounded to 4 digits| Rounded value as fraction | Rounding error |
|-|-|-|-|
| 1/10 | 10 | 0.1 | 0.1 | 1/10 | 0 |
| 1/3  | 10 | 0.<span class="over">3</span> | 0.3333 | 3333/10000 | 1/30000 |
| 1/2  | 2  | 0.1 | 0.1 | 1/2 | 0 |
| 1/10 | 2  | 0.0<span class="over">0011</span> | 0.0001 | 1/16 | 3/80 |

And this is how you already get a rounding error when you just *write down* a number like 0.1 and
run it through your interpreter or compiler. It's not as big as 3/80 and may be invisible because
computers cut off after 23 or 52 binary digits rather than 4. But the error is there and *will* cause
problems eventually if you just ignore it.


Why use Binary?
---------------
At the lowest level, computers are based on billions of electrical elements that have only two states, (usually low and high voltage). By interpreting these as 0 and 1, it's very easy to build circuits for storing binary numbers and doing calculations with them.

While it's possible to simulate the behaviour of decimal numbers with binary circuits as well, it's less efficient. If computers used decimal numbers internally, they'd have less memory and be slower at the same level of technology. 

Since the difference in behaviour between binary and decimal numbers is not important for most applications, the logical choice is to build computers based on binary numbers and live with the fact
that some extra care and effort are necessary for applications that require [decimal-like behaviour](/formats/exact/).
