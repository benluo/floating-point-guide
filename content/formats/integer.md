--- 
title: On Using Integers
description: Explanation why using integers to avoid floating-point problems by having them represent e.g. cents is not a good solution.
---

While integer types are usually binary and by definition do not support fractions, they are exact (no [rounding errors](/errors/rounding/) when converting from decimal integers) and can be used as a sort of "poor man's [decimal type](/formats/exact/)" by choosing an implicit fixed decimal point so that the smallest unit you work with can be represented as the integer 1. In practical terms, this is often put as: **"To handle money, store and calculate everything in cents and format only the output"**.

This works, but has a number of **severe drawbacks**:

* It's more work (and more opportunity for bugs) to get it right, especially in regard to [rounding modes](/errors/rounding/).
* Integers have complete precision, but very limited range, and when they overflow, they usually "wrap around" silently, i.e. the largest integer plus 1 becomes zero (for unsigned ints) or the negative value with the largest magnitude (for signed). This is just about the worst possible behaviour when dealing with money, for obvious reasons.
* The implicit decimal point is hard to change and extremely inflexible: if you store dollars as cents, it's simply impossible to support the [Bahraini dinar](http://en.wikipedia.org/wiki/Bahraini_dinar)(1 dinar = 1,000 Fils) at the same time. You'd have to store the position of the decimal point with the data - the first step in implementing your own (buggy, non-standard) limited-precision decimal [floating-point](/formats/fp/) format.
* The number of subunits in currencies change with time in the world. Due to inflation/deflation, some currencies stop having subunits, others add more subunits. If you store integers, you need to migrate the already stored prices to the new format. This is a total nightmare in an established system.

Summary: **using integers is not recommended.** Do this only if there really is no [better alternative](/formats/exact/) at all.
