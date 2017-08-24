--- 
title: Floating-point cheat sheet for PHP
description: Tips for using floating-point and decimal numbers in PHP
--- 

Floating-Point Types
--------
PHP is dynamically typed and will often convert implicitly between strings and floating-point numbers (which are platform-dependant, but typically IEEE 64 bit values). To force a value to floating-point, evaluate it in a numerical context:

		$foo = 0 + "10.5"; 


Decimal Types
-------------
The BC Math extension implements [arbitrary-precision](/formats/exact/) decimal math:

		$a = '0.1';
		$b = '0.2';
		echo bcadd($a, $b);     // prints 0.3

How to Round
------------
Rounding can be done with the `number_format()` function:

		$number = 4.123;
		echo number_format($number, 2); // prints 4.12


Resources 
---------
* [PHP manual](http://www.php.net/manual/en/index.php)
   * [Floating point types](http://www.php.net/manual/en/language.types.float.php)
   * [BC Math extension](http://php.net/manual/en/ref.bc.php)
   * [number_format()](http://php.net/manual/en/function.number-format.php)

