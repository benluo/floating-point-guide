--- 
title: Floating-point cheat sheet for SQL
description: Tips for using floating-point and decimal numbers in SQL
--- 

Floating-Point Types
--------
The SQL standard defines three binary floating-point types:

* `REAL` has implementation-dependant precision (usually maps to a hardware-supported type like IEEE 754 single or double precision)
* `DOUBLE PRECISION` has implementation-dependant precision which is greater than `REAL` (usually maps to IEEE 754 double precision)
* `FLOAT(N)` has at least `N` binary digits of precision, with an implementation-dependant maximum for `N`

The exponent range for all three types is implementation-dependant as well.

Decimal Types
-------------
The standard defines two fixed-point decimal types:

* `NUMERIC(M,N)` has exactly `M` total digits, `N` of them after the decimal point
* `DECIMAL(M,N)` is the same as `NUMERIC(M,N)`, except that it is allowed to have more than `M` total digits

The maximum values of `M` and `M` are implementation-dependant. Vendors often implement the two types identically.

How to Round
------------

The SQL standard defines no explicit rounding, but most vendors provide a `ROUND()` or `TRUNC()` function.

However, it usually makes little sense to round within the database, since its job is *storing* data, while rounding is an aspect of *displaying* data, and should therefore be done by the code in the presentation layer.


Resources 
---------
* [Official ISO SQL 2008 standard (non-free)](http://www.iso.org/iso/iso_catalogue/catalogue_tc/catalogue_detail.htm?csnumber=38640)  
* [SQL 92 draft (free)](http://www.contrib.andrew.cmu.edu/~shadow/sql/sql1992.txt)
* [MySQL numeric types](http://dev.mysql.com/doc/refman/5.0/en/numeric-types.html)
* [PostgreSQL Numeric Types](https://www.postgresql.org/docs/current/static/datatype-numeric.html)
* [MS SQL Server data types](http://msdn.microsoft.com/en-US/library/ms187752%28v=SQL.90%29.aspx)
