--- 
title: Floating-point cheat sheet for Perl
description: Tips for using floating-point and decimal numbers in Perl
--- 

Floating-Point Types
--------
Perl supports platform-native floating-point as scalar values; in practice this usually means [IEEE 754](/formats/fp/) double precision.

Exact Types
-------------
Perl can also store decimal numbers as strings, but the builtin arithmetic operators will convert them to integer or floating-point values to perform the operation.

The <code>Math::BigFloat</code> extension provides an arbitrary-precision [decimal type](/formats/exact/):

		use Math::BigFloat ':constant'
		my $f = 0.1 + 0.2; # returns exactly 0.3
		
The <code>Number::Fraction</code> extension provides a fraction type that overloads the arithmetic operators with [symbolic](/formats/exact/) fraction arithmetic:

		use Number::Fraction ':constants';
		my $f = '1/2' - '1/3'; # returns 1/6
		
The <code>Math::BigRat</code> extension provides similar functionality. Its advantage is compatibility with the
<code>Math::BigInt</code> and <code>Math::BigFloat</code> extensions, but it does not seem to support fraction literals.

How to Round
------------
To get a string:

		$result = sprintf("%.2f", 1.2345); # returns 1.23 
		
To format output:

		printf("%.2f", 1.2); # prints 1.20
		
Note that this implicitly uses [round-to-even](/errors/rounding/). The variable <code>$#</code> contains the default format for printing numbers, but its use is considered deprecated.

The <code>Math::Round</code> extension provides various functions for rounding floating-point values:

		use Math::Round qw(:all);
		$result = nearest(.1, 4.567) # prints 4.6
		$result = nearest(.01, 4.567) # prints 4.57
		
The <code>Math::BigFloat</code> extension also supports various [rounding modes](/errors/rounding/):

		use Math::BigFloat;
		my $n = Math::BigFloat->new(123.455);
		my $f1 = $n->round('','-2','common'); # returns 123.46
		my $f2 = $n->round('','-2','zero'); # returns 123.45

Resources 
---------
* [Semantics of numbers and numeric operations in Perl](http://perldoc.perl.org/perlnumber.html)
* [sprintf function](http://perldoc.perl.org/functions/sprintf.html)
* [Math::Round extension](http://search.cpan.org/dist/Math-Round/Round.pm)
* [Number::Fraction extension](http://search.cpan.org/~davecross/Number-Fraction-1.13/lib/Number/Fraction.pm)
* [Math::BigRat extension](http://search.cpan.org/~flora/Math-BigRat-0.26/lib/Math/BigRat.pm)
* [Math::BigFloat extension](http://search.cpan.org/~flora/Math-BigInt-1.95/lib/Math/BigFloat.pm)

