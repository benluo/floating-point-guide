--- 
title: What Every Programmer Should Know About Floating-Point Arithmetic
description: Aims to provide both short and simple answers to the common recurring questions of novice programmers about floating-point numbers not 'adding up' correctly, and more in-depth information about how IEEE 754 floats work, when and how to use them correctly, and what to use instead when they are not appropriate.
verification: SoYmbsJEmSz2s1LmZk_cku4pKwhRsU6m0ZOTgGdnTL0
---

or
--

Why don't my numbers add up?
============================

So you've written some absurdly simple code, say for example:

		0.1 + 0.2

and got a really unexpected result:

		0.30000000000000004

Maybe you asked for help on some forum and got pointed to a [long article with lots of formulas](http://download.oracle.com/docs/cd/E19957-01/806-3568/ncg_goldberg.html) that didn't seem to help with your problem.

Well, this site is here to:

* Explain concisely why you get that unexpected result
* Tell you how to deal with this problem
* If you're interested, provide in-depth explanations of why floating-point numbers have to work like that and what other problems can arise

You should look at the [Basic Answers](/basic/) first - but don't stop there!