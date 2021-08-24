# Comprehensive Python Cheatsheet

<sup>[Download text file](https://raw.githubusercontent.com/gto76/python-cheatsheet/master/README.md),[Buy PDF](https://transactions.sendowl.com/products/78175486/4422834F/view),[Fork me on GitHub](https://github.com/gto76/python-cheatsheet)or [Check out FAQ](https://github.com/gto76/python-cheatsheet/wiki/Frequently-Asked-Questions).</sup>

## Contents

**1. Collections:** **[`List`](#list)** **,** **[`Dictionary`](#dictionary)** **,** **[`Set`](#set)** **,** **[`Tuple`](#tuple)** **,** **[`Range`](#range)** **,** **[`Enumerate`](#enumerate)** **,** **[`Iterator`](#iterator)** **,** **[`Generator`](#generator)** **.**<br>
**2. Types:** **[`Type`](#type)** **,** **[`String`](#string)** **,** **[`Regular_Exp`](#regex)** **,** **[`Format`](#format)** **,** **[`Numbers`](#numbers-1)** **,** **[`Combinatorics`](#combinatorics)** **,** **[`Datetime`](#datetime)** **.**<br>
**3. Syntax:** **[`Args`](#arguments)** **,** **[`Inline`](#inline)** **,** **[`Closure`](#closure)** **,** **[`Decorator`](#decorator)** **,** **[`Class`](#class)** **,** **[`Duck_Type`](#duck-types)** **,** **[`Enum`](#enum)** **,** **[`Exception`](#exceptions)** **.**<br>
**4. System:** **[`Exit`](#exit)** **,** **[`Print`](#print)** **,** **[`Input`](#input)** **,** **[`Command_Line_Arguments`](#command-line-arguments)** **,** **[`Open`](#open)** **,** **[`Path`](#paths)** **,** **[`OS_Commands`](#os-commands)** **.**<br>
**5. Data:** **[`JSON`](#json)** **,** **[`Pickle`](#pickle)** **,** **[`CSV`](#csv)** **,** **[`SQLite`](#sqlite)** **,** **[`Bytes`](#bytes)** **,** **[`Struct`](#struct)** **,** **[`Array`](#array)** **,** **[`Memory_View`](#memory-view)** **,** **[`Deque`](#deque)** **.**<br>
**6. Advanced:** **[`Threading`](#threading)** **,** **[`Operator`](#operator)** **,** **[`Introspection`](#introspection)** **,** **[`Metaprograming`](#metaprograming)** **,** **[`Eval`](#eval)** **,** **[`Coroutines`](#coroutines)** **.**<br>
**7. Libraries:** **[`Progress_Bar`](#progress-bar)** **,** **[`Plot`](#plot)** **,** **[`Table`](#table)** **,** **[`Curses`](#curses)** **,** **[`Logging`](#logging)** **,** **[`Scraping`](#scraping)** **,** **[`Web`](#web)** **,** **[`Profile`](#profiling)** **,**<br>
**[`NumPy`](#numpy)** **,** **[`Image`](#image)** **,** **[`Audio`](#audio)** **,** **[`Games`](#pygame)** **,** **[`Data`](#pandas)** **.**

## Main

```python
if __name__ == '__main__':     # Runs main() if file wasn't imported.
    main()
```

## List

```python
<list> = <list>[from_inclusive : to_exclusive : ±step_size]
```

```python
<list>.append(<el>)            # Or:  += []
<list>.extend(<collection>)    # Or:  +=
```

```python
<list>.sort()
<list>.reverse()
<list> = sorted(<collection>)
<iter> = reversed(<list>)
```

```python
sum_of_elements  = sum(<collection>)
elementwise_sum  = [sum(pair) for pair in zip(list_a, list_b)]
sorted_by_second = sorted(<collection>, key=lambda el: el[1])
sorted_by_both   = sorted(<collection>, key=lambda el: (el[1], el[0]))
flatter_list     = list(itertools.chain.from_iterable(<list>))
product_of_elems = functools.reduce(lambda out, el: out * el, <collection>)
list_of_chars    = list(<str>)
```

* **Module [operator](#operator) provides functions itemgetter() and mul() that offer the same functionality as [lambda](#lambda) expressions above.*

```python
<list>.insert(<int>, <el>)     # Inserts item at index and moves the rest to the right.
<el>  = <list>.pop([<int>])    # Returns and removes item at index or from the end.
<int> = <list>.count(<el>)     # Returns number of occurrences. Also works on strings.
<int> = <list>.index(<el>)     # Returns index of the first occurrence or raises ValueError.
<list>.remove(<el>)            # Removes first occurrence of the item or raises ValueError.
<list>.clear()                 # Removes all items. Also works on dictionary and set.
```

## Dictionary

```python
<view> = <dict>.keys()                          # Coll. of keys that reflects changes.
<view> = <dict>.values()                        # Coll. of values that reflects changes.
<view> = <dict>.items()                         # Coll. of key-value tuples that reflects chgs.
```

```python
value  = <dict>.get(key, default=None)          # Returns default if key is missing.
value  = <dict>.setdefault(key, default=None)   # Returns and writes default if key is missing.
<dict> = collections.defaultdict(<type>)        # Creates a dict with default value of type.
<dict> = collections.defaultdict(lambda: 1)     # Creates a dict with default value 1.
```

```python
<dict> = dict(<collection>)                     # Creates a dict from coll. of key-value pairs.
<dict> = dict(zip(keys, values))                # Creates a dict from two collections.
<dict> = dict.fromkeys(keys [, value])          # Creates a dict from collection of keys.
```

```python
<dict>.update(<dict>)                           # Adds items. Replaces ones with matching keys.
value = <dict>.pop(key)                         # Removes item or raises KeyError.
{k for k, v in <dict>.items() if v == value}    # Returns set of keys that point to the value.
{k: v for k, v in <dict>.items() if k in keys}  # Returns a dictionary, filtered by keys.
```

### Counter

```python
>>> from collections import Counter
>>> colors = ['blue', 'blue', 'blue', 'red', 'red']
>>> counter = Counter(colors)
>>> counter['yellow'] += 1
Counter({'blue': 3, 'red': 2, 'yellow': 1})
>>> counter.most_common()[0]
('blue', 3)
```

## Set

```python
<set> = set()
```

```python
<set>.add(<el>)                                 # Or:  |= {}
<set>.update(<collection> [, ...])              # Or:  |=
```

```python
<set>  = <set>.union(<coll.>)                   # Or:  |
<set>  = <set>.intersection(<coll.>)            # Or:  &
<set>  = <set>.difference(<coll.>)              # Or:  -
<set>  = <set>.symmetric_difference(<coll.>)    # Or:  ^
<bool> = <set>.issubset(<coll.>)                # Or:  <=
<bool> = <set>.issuperset(<coll.>)              # Or:  >=
```

```python
<el> = <set>.pop()                              # Raises KeyError if empty.
<set>.remove(<el>)                              # Raises KeyError if missing.
<set>.discard(<el>)                             # Doesn't raise an error.
```

### Frozen Set

* **Is immutable and hashable.**
* **That means it can be used as a key in a dictionary or as an element in a set.*

```python
<frozenset> = frozenset(<collection>)
```

## Tuple

**Tuple is an immutable and hashable list.**

```python
<tuple> = ()
<tuple> = (<el>,)                           # Or: ,
<tuple> = (<el_1>, <el_2> [, ...])          # Or: ,  [, ...]
```

### Named Tuple

**Tuple's subclass with named elements.**

```python
>>> from collections import namedtuple
>>> Point = namedtuple('Point', 'x y')
>>> p = Point(1, y=2)
Point(x=1, y=2)
>>> p[0]
1
>>> p.x
1
>>> getattr(p, 'y')
2
>>> p._fields  # Or: Point._fields
('x', 'y')
```

## Range

```python
<range> = range(to_exclusive)
<range> = range(from_inclusive, to_exclusive)
<range> = range(from_inclusive, to_exclusive, ±step_size)
```

```python
from_inclusive = <range>.start
to_exclusive   = <range>.stop
```

## Enumerate

```python
for i, el in enumerate(<collection> [, i_start]):
    ...
```

## Iterator

```python
<iter> = iter(<collection>)                 # `iter()` returns unmodified iterator.
<iter> = iter(<function>, to_exclusive)     # A sequence of return values until 'to_exclusive'.
<el>   = next(<iter> [, default])           # Raises StopIteration or returns 'default' on end.
<list> = list(<iter>)                       # Returns a list of iterator's remaining elements.
```

### Itertools

```python
from itertools import count, repeat, cycle, chain, islice
```

```python
<iter> = count(start=0, step=1)             # Returns updated value endlessly. Accepts floats.
<iter> = repeat(<el> [, times])             # Returns element endlessly or 'times' times.
<iter> = cycle(<collection>)                # Repeats the sequence endlessly.
```

```python
<iter> = chain(<coll_1>, <coll_2> [, ...])  # Empties collections in order.
<iter> = chain.from_iterable(<collection>)  # Empties collections inside a collection in order.
```

```python
<iter> = islice(<coll>, to_exclusive)       # Only returns first 'to_exclusive' elements.
<iter> = islice(<coll>, from_inclusive, ...)  # `to_exclusive, step_size`.
```

## Generator

* **Any function that contains a yield statement returns a generator.**
* **Generators and iterators are interchangeable.*

```python
def count(start, step):
    while True:
        yield start
        start += step
```

```python
>>> counter = count(10, 2)
>>> next(counter), next(counter), next(counter)
(10, 12, 14)
```

## Type

* **Everything is an object.**
* **Every object has a type.**
* **Type and class are synonymous.*

```python
<type> = type(<el>)                          # Or: .__class__
<bool> = isinstance(<el>, <type>)            # Or: issubclass(type(), )
```

```python
>>> type('a'), 'a'.__class__, str
(<class 'str'>, <class 'str'>, <class 'str'>)
```

#### Some types do not have built-in names, so they must be imported:

```python
from types import FunctionType, MethodType, LambdaType, GeneratorType
```

### Abstract Base Classes

**Each abstract base class specifies a set of virtual subclasses. These classes are then recognized by isinstance() and issubclass() as subclasses of the ABC, although they are really not. ABC can also manually decide whether or not a specific class is its virtual subclass, usually based on which methods the class has implemented. For instance, Iterable ABC looks for method iter() while Collection ABC looks for methods iter(), contains() and len().**

```python
>>> from collections.abc import Sequence, Collection, Iterable
>>> isinstance([1, 2, 3], Iterable)
True
```

```
+------------------+------------+------------+------------+
|                  |  Sequence  | Collection |  Iterable  |
+------------------+------------+------------+------------+
| list, range, str |    yes     |    yes     |    yes     |
| dict, set        |            |    yes     |    yes     |
| iter             |            |            |    yes     |
+------------------+------------+------------+------------+
```

```python
>>> from numbers import Integral, Rational, Real, Complex, Number
>>> isinstance(123, Number)
True
```

```
+--------------------+----------+----------+----------+----------+----------+
|                    | Integral | Rational |   Real   | Complex  |  Number  |
+--------------------+----------+----------+----------+----------+----------+
| int                |   yes    |   yes    |   yes    |   yes    |   yes    |
| fractions.Fraction |          |   yes    |   yes    |   yes    |   yes    |
| float              |          |          |   yes    |   yes    |   yes    |
| complex            |          |          |          |   yes    |   yes    |
| decimal.Decimal    |          |          |          |          |   yes    |
+--------------------+----------+----------+----------+----------+----------+
```

## String

```python
<str>  = <str>.strip()                       # Strips all whitespace characters from both ends.
<str>  = <str>.strip('')              # Strips all passed characters from both ends.
```

```python
<list> = <str>.split()                       # Splits on one or more whitespace characters.
<list> = <str>.split(sep=None, maxsplit=-1)  # Splits on 'sep' str at most 'maxsplit' times.
<list> = <str>.splitlines(keepends=False)    # Splits on [\n\r\f\v\x1c\x1d\x1e\x85] and '\r\n'.
<str>  = <str>.join(<coll_of_strings>)       # Joins elements using string as a separator.
```

```python
<bool> = <sub_str> in <str>                  # Checks if string contains a substring.
<bool> = <str>.startswith(<sub_str>)         # Pass tuple of strings for multiple options.
<bool> = <str>.endswith(<sub_str>)           # Pass tuple of strings for multiple options.
<int>  = <str>.find(<sub_str>)               # Returns start index of the first match or -1.
<int>  = <str>.index(<sub_str>)              # Same but raises ValueError if missing.
```

```python
<str>  = <str>.replace(old, new [, count])   # Replaces 'old' with 'new' at most 'count' times.
<str>  = <str>.translate(<table>)            # Use `str.maketrans()` to generate table.
```

```python
<str>  = chr(<int>)                          # Converts int to Unicode char.
<int>  = ord(<str>)                          # Converts Unicode char to int.
```

* **Also: `'lstrip()'`, `'rstrip()'`.**
* **Also: `'lower()'`, `'upper()'`, `'capitalize()'` and `'title()'`.*

### Property Methods

```
+---------------+----------+----------+----------+----------+----------+
|               | [ !#$%&#x2026;] | [a-zA-Z] |  [&#xBC;&#xBD;&#xBE;]   |  [&#xB2;&#xB3;&#xB9;]   |  [0-9]   |
+---------------+----------+----------+----------+----------+----------+
| isprintable() |   yes    |   yes    |   yes    |   yes    |   yes    |
| isalnum()     |          |   yes    |   yes    |   yes    |   yes    |
| isnumeric()   |          |          |   yes    |   yes    |   yes    |
| isdigit()     |          |          |          |   yes    |   yes    |
| isdecimal()   |          |          |          |          |   yes    |
+---------------+----------+----------+----------+----------+----------+
```

* **Also: `'isspace()'` checks for `'[ \t\n\r\f\v&#x2026;]'`.*

## Regex

```python
import re
<str>   = re.sub(<regex>, new, text, count=0)  # Substitutes all occurrences with 'new'.
<list>  = re.findall(<regex>, text)            # Returns all occurrences as strings.
<list>  = re.split(<regex>, text, maxsplit=0)  # Use brackets in regex to include the matches.
<Match> = re.search(<regex>, text)             # Searches for first occurrence of the pattern.
<Match> = re.match(<regex>, text)              # Searches only at the beginning of the text.
<iter>  = re.finditer(<regex>, text)           # Returns all occurrences as match objects.
```

* **Search() and match() return None if they can't find a match.**
* **Argument `'flags=re.IGNORECASE'` can be used with all functions.**
* **Argument `'flags=re.MULTILINE'` makes `'^'` and `'$'` match the start/end of each line.**
* **Argument `'flags=re.DOTALL'` makes dot also accept the `'\n'`.**
* **Use `r'\1'` or `'\\1'` for backreference.**
* **Add `'?'` after an operator to make it non-greedy.*

### Match Object

```python
<str>   = <Match>.group()                      # Returns the whole match. Also group(0).
<str>   = <Match>.group(1)                     # Returns part in the first bracket.
<tuple> = <Match>.groups()                     # Returns all bracketed parts.
<int>   = <Match>.start()                      # Returns start index of the match.
<int>   = <Match>.end()                        # Returns exclusive end index of the match.
```

### Special Sequences

* **By default, decimal characters, alphanumerics and whitespaces from all alphabets are matched unless `'flags=re.ASCII'` argument is used.**
* **As shown below, it restricts special sequence matches to `'[\x00-\x7f]'` and prevents `'\s'` from accepting `'[\x1c\x1d\x1e\x1f]'`.**
* **Use a capital letter for negation.*

```python
'\d' == '[0-9]'                                # Matches decimal characters.
'\w' == '[a-zA-Z0-9_]'                         # Matches alphanumerics and underscore.
'\s' == '[ \t\n\r\f\v]'                        # Matches whitespaces.
```

## Format

```python
<str> = f'{<el_1>}, {<el_2>}'
 = '{}, {}'.format(<el_1>, <el_2>)
```

### Attributes

```python
>>> from collections import namedtuple
>>> Person = namedtuple('Person', 'name height')
>>> person = Person('Jean-Luc', 187)
>>> f'{person.height}'
'187'
>>> '{p.height}'.format(p=person)
'187'
```

### General Options

```python
{<el>:<10}                                     # '      '
{<el>:^10}                                     # '      '
{<el>:>10}                                     # '      '
{<el>:.<10}                                    # '......'
{<el>:0}                                       # ''
```

### Strings

**`'!r'` calls object's [repr()](#class) method, instead of [str()](#class), to get a string.**

```python
{'abcde'!r:10}                                 # "'abcde'   "
{'abcde':10.3}                                 # 'abc       '
{'abcde':.3}                                   # 'abc'
```

### Numbers

```python
{ 123456:10,}                                  # '   123,456'
{ 123456:10_}                                  # '   123_456'
{ 123456:+10}                                  # '   +123456'
{-123456:=10}                                  # '-   123456'
{ 123456: }                                    # ' 123456'
{-123456: }                                    # '-123456'
```

### Floats

```python
{1.23456:10.3}                                 # '      1.23'
{1.23456:10.3f}                                # '     1.235'
{1.23456:10.3e}                                # ' 1.235e+00'
{1.23456:10.3%}                                # '  123.456%'
```

#### Comparison of presentation types:

```
+--------------+----------------+----------------+----------------+----------------+
|              |    {<float>}   |   {<float>:f}  |   {<float>:e}  |   {<float>:%}  |
+--------------+----------------+----------------+----------------+----------------+
|  0.000056789 |   '5.6789e-05' |    '0.000057'  | '5.678900e-05' |    '0.005679%' |
|  0.00056789  |   '0.00056789' |    '0.000568'  | '5.678900e-04' |    '0.056789%' |
|  0.0056789   |   '0.0056789'  |    '0.005679'  | '5.678900e-03' |    '0.567890%' |
|  0.056789    |   '0.056789'   |    '0.056789'  | '5.678900e-02' |    '5.678900%' |
|  0.56789     |   '0.56789'    |    '0.567890'  | '5.678900e-01' |   '56.789000%' |
|  5.6789      |   '5.6789'     |    '5.678900'  | '5.678900e+00' |  '567.890000%' |
| 56.789       |  '56.789'      |   '56.789000'  | '5.678900e+01' | '5678.900000%' |
+--------------+----------------+----------------+----------------+----------------+
</float></float></float></float>
```

```
+--------------+----------------+----------------+----------------+----------------+
|              |  {<float>:.2}  |  {<float>:.2f} |  {<float>:.2e} |  {<float>:.2%} |
+--------------+----------------+----------------+----------------+----------------+
|  0.000056789 |    '5.7e-05'   |      '0.00'    |   '5.68e-05'   |      '0.01%'   |
|  0.00056789  |    '0.00057'   |      '0.00'    |   '5.68e-04'   |      '0.06%'   |
|  0.0056789   |    '0.0057'    |      '0.01'    |   '5.68e-03'   |      '0.57%'   |
|  0.056789    |    '0.057'     |      '0.06'    |   '5.68e-02'   |      '5.68%'   |
|  0.56789     |    '0.57'      |      '0.57'    |   '5.68e-01'   |     '56.79%'   |
|  5.6789      |    '5.7'       |      '5.68'    |   '5.68e+00'   |    '567.89%'   |
| 56.789       |    '5.7e+01'   |     '56.79'    |   '5.68e+01'   |   '5678.90%'   |
+--------------+----------------+----------------+----------------+----------------+
</float></float></float></float>
```

* **When both rounding up and rounding down are possible, the one that returns result with even last digit is chosen. That makes `'{6.5:.0f}'` a `'6'` and `'{7.5:.0f}'` an `'8'`.*

### Ints

```python
{90:c}                                   # 'Z'
{90:b}                                   # '1011010'
{90:X}                                   # '5A'
```

## Numbers

### Types

```python
<int>      = int(<float/str/bool>)       # Or: math.floor()
<float>    = float(<int/str/bool>)       # Or: e±
<complex>  = complex(real=0, imag=0)     # Or:  ± j
<Fraction> = fractions.Fraction(0, 1)    # Or: Fraction(numerator=0, denominator=1)
<Decimal>  = decimal.Decimal(<str/int>)  # Or: Decimal((sign, digits, exponent))
```

* **`'int(<str>)'</str>` and `'float(<str>)'</str>` raise ValueError on malformed strings.**
* **Decimal numbers can be represented exactly, unlike floats where `'1.1 + 2.2 != 3.3'`.**
* **Precision of decimal operations is set with: `'decimal.getcontext().prec = <int>'</int>`.*

### Basic Functions

```python
<num> = pow(<num>, <num>)                # Or:  **
<num> = abs(<num>)                       #  = abs()
<num> = round(<num> [, ±ndigits])        # `round(126, -1) == 130`
```

### Math

```python
from math import e, pi, inf, nan, isinf, isnan
from math import sin, cos, tan, asin, acos, atan, degrees, radians
from math import log, log10, log2
```

### Statistics

```python
from statistics import mean, median, variance, stdev, pvariance, pstdev
```

### Random

```python
from random import random, randint, choice, shuffle, gauss, seed

<float> = random()                       # A float inside [0, 1).
<int>   = randint(from_inc, to_inc)      # An int inside [from_inc, to_inc].
<el>    = choice(<list>)                 # Keeps the list intact.
```

### Bin, Hex

```python
<int> = ±0b<bin>                         # Or: ±0x
<int> = int('±', 2)                 # Or: int('±', 16)
<int> = int('±0b', 0)               # Or: int('±0x', 0)
<str> = bin(<int>)                       # Returns '[-]0b'.
```

### Bitwise Operators

```python
<int> = <int> & <int>                    # And
<int> = <int> | <int>                    # Or
<int> = <int> ^ <int>                    # Xor (0 if both bits equal)
<int> = <int> << n_bits                  # Left shift (>> for right)
<int> = ~<int>                           # Not (also: - - 1)
```

## Combinatorics

* **Every function returns an iterator.**
* **If you want to print the iterator, you need to pass it to the list() function first!*

```python
from itertools import product, combinations, combinations_with_replacement, permutations
```

```python
>>> product([0, 1], repeat=3)
[(0, 0, 0), (0, 0, 1), (0, 1, 0), (0, 1, 1), ..., (1, 1, 1)]
```

```python
>>> product('abc', 'abc')                    #   a  b  c
[('a', 'a'), ('a', 'b'), ('a', 'c'),         # a x  x  x
 ('b', 'a'), ('b', 'b'), ('b', 'c'),         # b x  x  x
 ('c', 'a'), ('c', 'b'), ('c', 'c')]         # c x  x  x
```

```python
>>> combinations('abc', 2)                   #   a  b  c
[('a', 'b'), ('a', 'c'),                     # a .  x  x
 ('b', 'c')]                                 # b .  .  x
```

```python
>>> combinations_with_replacement('abc', 2)  #   a  b  c
[('a', 'a'), ('a', 'b'), ('a', 'c'),         # a x  x  x
 ('b', 'b'), ('b', 'c'),                     # b .  x  x
 ('c', 'c')]                                 # c .  .  x
```

```python
>>> permutations('abc', 2)                   #   a  b  c
[('a', 'b'), ('a', 'c'),                     # a .  x  x
 ('b', 'a'), ('b', 'c'),                     # b x  .  x
 ('c', 'a'), ('c', 'b')]                     # c x  x  .
```

## Datetime

* **Module 'datetime' provides 'date'`<d></d>`, 'time'`<t></t>`, 'datetime'``**<dt> **`` and 'timedelta'`` classes. All are immutable and hashable.**</dt>
* **Time and datetime objects can be 'aware'``[, meaning they have defined timezone, or 'naive' `<n></n>`, meaning they don't.]()** [
* **If object is naive, it is presumed to be in the system's timezone.**]()

[

```python
from datetime import date, time, datetime, timedelta
from dateutil.tz import UTC, tzlocal, gettz, datetime_exists, resolve_imaginary
```]()

### Constructors

```python
<D>  = date(year, month, day)
<T>  = time(hour=0, minute=0, second=0, microsecond=0, tzinfo=None, fold=0)
<DT> = datetime(year, month, day, hour=0, minute=0, second=0, ...)
<TD> = timedelta(days=0, seconds=0, microseconds=0, milliseconds=0,
                 minutes=0, hours=0, weeks=0)
```

* **Use `'<d dt>.weekday()'</d>` to get the day of the week (Mon == 0).**
* **`'fold=1'` means the second pass in case of time jumping back for one hour.**
* **`'<dta> = resolve_imaginary(<dta>)'</dta></dta>` fixes DTs that fall into the missing hour.*

### Now

```python
<D/DTn>  = D/DT.today()                     # Current local date or naive datetime.
<DTn>    = DT.utcnow()                      # Naive datetime from current UTC time.
<DTa>    = DT.now(<tzinfo>)                 # Aware datetime from current tz time.
```

* **To extract time use `'<dtn>.time()'</dtn>`, `'<dta>.time()'</dta>` or `'<dta>.timetz()'</dta>`.*

### Timezone

```python
<tzinfo> = UTC                              # UTC timezone. London without DST.
<tzinfo> = tzlocal()                        # Local timezone. Also gettz().
<tzinfo> = gettz('/')      # 'Continent/City_Name' timezone or None.
<DTa>    = <DT>.astimezone(<tzinfo>)        # Datetime, converted to the passed timezone.
<Ta/DTa> = <T/DT>.replace(tzinfo=<tzinfo>)  # Unconverted object with a new timezone.
```

### Encode

```python
<D/T/DT> = D/T/DT.fromisoformat('')    # Object from ISO string. Raises ValueError.
<DT>     = DT.strptime(<str>, '')   # Datetime from str, according to format.
<D/DTn>  = D/DT.fromordinal(<int>)          # D/DTn from days since the Gregorian NYE 1.
<DTn>    = DT.fromtimestamp(<real>)         # Local time DTn from seconds since the Epoch.
<DTa>    = DT.fromtimestamp(<real>, <tz.>)  # Aware datetime from seconds since the Epoch.
```

* **ISO strings come in following forms: `'YYYY-MM-DD'`, `'HH:MM:SS.ffffff[&#xB1;<offset>]'</offset>`, or both separated by an arbitrary character. Offset is formatted as: `'HH:MM'`.**
* **Epoch on Unix systems is: `'1970-01-01 00:00 UTC'`, `'1970-01-01 01:00 CET'`, ...*

### Decode

```python
<str>    = <D/T/DT>.isoformat(sep='T')      # Also timespec='auto/hours/minutes/seconds'.
<str>    = <D/T/DT>.strftime('')    # Custom string representation.
<int>    = <D/DT>.toordinal()               # Days since Gregorian NYE 1, ignoring time and tz.
<float>  = <DTn>.timestamp()                # Seconds since the Epoch, from DTn in local tz.
<float>  = <DTa>.timestamp()                # Seconds since the Epoch, from DTa.
```

### Format

```python
>>> from datetime import datetime
>>> dt = datetime.strptime('2015-05-14 23:39:00.00 +0200', '%Y-%m-%d %H:%M:%S.%f %z')
>>> dt.strftime("%A, %dth of %B '%y, %I:%M%p %Z")
"Thursday, 14th of May '15, 11:39PM UTC+02:00"
```

* **When parsing, `'%z'` also accepts `'&#xB1;HH:MM'`.**
* **For abbreviated weekday and month use `'%a'` and `'%b'`.*

### Arithmetics

```python
<D/DT>   = <D/DT>   ± <TD>                  # Returned datetime can fall into missing hour.
<TD>     = <D/DTn>  - <D/DTn>               # Returns the difference, ignoring time jumps.
<TD>     = <DTa>    - <DTa>                 # Ignores time jumps if they share tzinfo object.
<TD>     = <DT_UTC> - <DT_UTC>              # Convert DTs to UTC to get the actual delta.
```

## Arguments

### Inside Function Call

```python
<function>(<positional_args>)                  # f(0, 0)
<function>(<keyword_args>)                     # f(x=0, y=0)
<function>(<positional_args>, <keyword_args>)  # f(0, y=0)
```

### Inside Function Definition

```python
def f(<nondefault_args>):                      # def f(x, y):
def f(<default_args>):                         # def f(x=0, y=0):
def f(<nondefault_args>, <default_args>):      # def f(x, y=0):
```

## Splat Operator

### Inside Function Call

**Splat expands a collection into positional arguments, while splatty-splat expands a dictionary into keyword arguments.**

```python
args   = (1, 2)
kwargs = {'x': 3, 'y': 4, 'z': 5}
func(*args, **kwargs)
```

#### Is the same as:

```python
func(1, 2, x=3, y=4, z=5)
```

### Inside Function Definition

**Splat combines zero or more positional arguments into a tuple, while splatty-splat combines zero or more keyword arguments into a dictionary.**

```python
def add(*a):
    return sum(a)
```

```python
>>> add(1, 2, 3)
6
```

#### Legal argument combinations:

```python
def f(x, y, z):                # f(x=1, y=2, z=3) | f(1, y=2, z=3) | f(1, 2, z=3) | f(1, 2, 3)
def f(*, x, y, z):             # f(x=1, y=2, z=3)
def f(x, *, y, z):             # f(x=1, y=2, z=3) | f(1, y=2, z=3)
def f(x, y, *, z):             # f(x=1, y=2, z=3) | f(1, y=2, z=3) | f(1, 2, z=3)
```

```python
def f(*args):                  # f(1, 2, 3)
def f(x, *args):               # f(1, 2, 3)
def f(*args, z):               # f(1, 2, z=3)
def f(x, *args, z):            # f(1, 2, z=3)
```

```python
def f(**kwargs):               # f(x=1, y=2, z=3)
def f(x, **kwargs):            # f(x=1, y=2, z=3) | f(1, y=2, z=3)
def f(*, x, **kwargs):         # f(x=1, y=2, z=3)
```

```python
def f(*args, **kwargs):        # f(x=1, y=2, z=3) | f(1, y=2, z=3) | f(1, 2, z=3) | f(1, 2, 3)
def f(x, *args, **kwargs):     # f(x=1, y=2, z=3) | f(1, y=2, z=3) | f(1, 2, z=3) | f(1, 2, 3)
def f(*args, y, **kwargs):     # f(x=1, y=2, z=3) | f(1, y=2, z=3)
def f(x, *args, z, **kwargs):  # f(x=1, y=2, z=3) | f(1, y=2, z=3) | f(1, 2, z=3)
```

### Other Uses

```python
<list> = [*<collection> [, ...]]
<set>  = {*<collection> [, ...]}
<tup.> = (*<collection>, [...])
<dict> = {**<dict> [, ...]}
```

```python
head, *body, tail = <collection>
```

## Inline

### Lambda

```python
<func> = lambda: <return_value>
<func> = lambda <arg_1>, <arg_2>: <return_value>
```

### Comprehensions

```python
<list> = [i+1 for i in range(10)]                         # [1, 2, ..., 10]
<set>  = {i for i in range(10) if i > 5}                  # {6, 7, 8, 9}
<iter> = (i+5 for i in range(10))                         # (5, 6, ..., 14)
<dict> = {i: i*2 for i in range(10)}                      # {0: 0, 1: 2, ..., 9: 18}
```

```python
>>> [l+r for l in 'abc' for r in 'abc']
['aa', 'ab', 'ac', ..., 'cc']
```

### Map, Filter, Reduce

```python
<iter> = map(lambda x: x + 1, range(10))                  # (1, 2, ..., 10)
<iter> = filter(lambda x: x > 5, range(10))               # (6, 7, 8, 9)
<obj>  = reduce(lambda out, x: out + x, range(10))        # 45
```

* **Reduce must be imported from functools module.*

### Any, All

```python
<bool> = any(<collection>)                                # False if empty.
<bool> = all(el[1] for el in <collection>)                # True if empty.
```

### Conditional Expression

```python
<obj> = <exp_if_true> if <condition> else <exp_if_false>
```

```python
>>> [a if a else 'zero' for a in (0, 1, 2, 3)]
['zero', 1, 2, 3]
```

### Namedtuple, Enum, Dataclass

```python
from collections import namedtuple
Point     = namedtuple('Point', 'x y')
point     = Point(0, 0)
```

```python
from enum import Enum
Direction = Enum('Direction', 'n e s w')
direction = Direction.n
```

```python
from dataclasses import make_dataclass
Creature  = make_dataclass('Creature', ['loc', 'dir'])
creature  = Creature(Point(0, 0), Direction.n)
```

## Closure

**We have a closure in Python when:**

* **A nested function references a value of its enclosing function and then**
* **the enclosing function returns the nested function.*

```python
def get_multiplier(a):
    def out(b):
        return a * b
    return out
```

```python
>>> multiply_by_3 = get_multiplier(3)
>>> multiply_by_3(10)
30
```

* **If multiple nested functions within enclosing function reference the same value, that value gets shared.**
* **To dynamically access function's first free variable use `'<function>.__closure__[0].cell_contents'</function>`.*

### Partial

```python
from functools import partial
<function> = partial(<function> [, <arg_1>, <arg_2>, ...])
```

```python
>>> import operator as op
>>> multiply_by_3 = partial(op.mul, 3)
>>> multiply_by_3(10)
30
```

* **Partial is also useful in cases when function needs to be passed as an argument, because it enables us to set its arguments beforehand.**
* **A few examples being: `'defaultdict(<function>)'</function>`, `'iter(<function>, to_exclusive)'</function>` and dataclass's `'field(default_factory=<function>)'</function>`.*

### Non-Local

**If variable is being assigned to anywhere in the scope, it is regarded as a local variable, unless it is declared as a 'global' or a 'nonlocal'.**

```python
def get_counter():
    i = 0
    def out():
        nonlocal i
        i += 1
        return i
    return out
```

```python
>>> counter = get_counter()
>>> counter(), counter(), counter()
(1, 2, 3)
```

## Decorator

**A decorator takes a function, adds some functionality and returns it.**

```python
@decorator_name
def function_that_gets_passed_to_decorator():
    ...
```

### Debugger Example

**Decorator that prints function's name every time it gets called.**

```python
from functools import wraps

def debug(func):
    @wraps(func)
    def out(*args, **kwargs):
        print(func.__name__)
        return func(*args, **kwargs)
    return out

@debug
def add(x, y):
    return x + y
```

* **Wraps is a helper decorator that copies the metadata of the passed function (func) to the function it is wrapping (out).**
* **Without it `'add.__name__'` would return `'out'`.*

### LRU Cache

**Decorator that caches function's return values. All function's arguments must be hashable.**

```python
from functools import lru_cache

@lru_cache(maxsize=None)
def fib(n):
    return n if n < 2 else fib(n-2) + fib(n-1)
```

* **CPython interpreter limits recursion depth to 1000 by default. To increase it use `'sys.setrecursionlimit(<depth>)'</depth>`.*

### Parametrized Decorator

**A decorator that accepts arguments and returns a normal decorator that accepts a function.**

```python
from functools import wraps

def debug(print_result=False):
    def decorator(func):
        @wraps(func)
        def out(*args, **kwargs):
            result = func(*args, **kwargs)
            print(func.__name__, result if print_result else '')
            return result
        return out
    return decorator

@debug(print_result=True)
def add(x, y):
    return x + y
```

## Class

```python
class <name>:
    def __init__(self, a):
        self.a = a
    def __repr__(self):
        class_name = self.__class__.__name__
        return f'{class_name}({self.a!r})'
    def __str__(self):
        return str(self.a)

    @classmethod
    def get_class_name(cls):
        return cls.__name__
```

* **Return value of repr() should be unambiguous and of str() readable.**
* **If only repr() is defined, it will also be used for str().*

#### Str() use cases:

```python
print(<el>)
print(f'{<el>}')
raise Exception(<el>)
loguru.logger.debug(<el>)
csv.writer(<file>).writerow([<el>])
```

#### Repr() use cases:

```python
print([<el>])
print(f'{<el>!r}')
>>> <el>
loguru.logger.exception()
Z = dataclasses.make_dataclass('Z', ['a']); print(Z(<el>))
```

### Constructor Overloading

```python
class <name>:
    def __init__(self, a=None):
        self.a = a
```

### Inheritance

```python
class Person:
    def __init__(self, name, age):
        self.name = name
        self.age  = age

class Employee(Person):
    def __init__(self, name, age, staff_num):
        super().__init__(name, age)
        self.staff_num = staff_num
```

### Multiple Inheritance

```python
class A: pass
class B: pass
class C(A, B): pass
```

**MRO determines the order in which parent classes are traversed when searching for a method:**

```python
>>> C.mro()
[<class 'C'>, <class 'A'>, <class 'B'>, object'>]
```

### Property

**Pythonic way of implementing getters and setters.**

```python
class MyClass:
    @property
    def a(self):
        return self._a

    @a.setter
    def a(self, value):
        self._a = value
```

```python
>>> el = MyClass()
>>> el.a = 123
>>> el.a
123
```

### Dataclass

**Decorator that automatically generates init(), repr() and eq() special methods.**

```python
from dataclasses import dataclass, field

@dataclass(order=False, frozen=False)
class <class_name>:
    <attr_name_1>: <type>
    <attr_name_2>: <type> = <default_value>
    <attr_name_3>: list/dict/set = field(default_factory=list/dict/set)
```

* **Objects can be made sortable with `'order=True'` and immutable with `'frozen=True'`.**
* **For object to be hashable, all attributes must be hashable and frozen must be True.**
* **Function field() is needed because `'<attr_name>: list = []'</attr_name>` would make a list that is shared among all instances.**
* **Default_factory can be any [callable](#callable).*

#### Inline:

```python
from dataclasses import make_dataclass
<class> = make_dataclass('', <coll_of_attribute_names>)
<class> = make_dataclass('', <coll_of_tuples>)
<tuple> = ('', <type> [, <default_value>])
```

### Slots

**Mechanism that restricts objects to attributes listed in 'slots' and significantly reduces their memory footprint.**

```python
class MyClassWithSlots:
    __slots__ = ['a']
    def __init__(self):
        self.a = 1
```

### Copy

```python
from copy import copy, deepcopy

<object> = copy(<object>)
<object> = deepcopy(<object>)
```

## Duck Types

**A duck type is an implicit type that prescribes a set of special methods. Any object that has those methods defined is considered a member of that duck type.**

### Comparable

* **If eq() method is not overridden, it returns `'id(self) == id(other)'`, which is the same as `'self is other'`.**
* **That means all objects compare not equal by default.**
* **Only the left side object has eq() method called, unless it returns NotImplemented, in which case the right object is consulted.*

```python
class MyComparable:
    def __init__(self, a):
        self.a = a
    def __eq__(self, other):
        if isinstance(other, type(self)):
            return self.a == other.a
        return NotImplemented
```

### Hashable

* **Hashable object needs both hash() and eq() methods and its hash value should never change.**
* **Hashable objects that compare equal must have the same hash value, meaning default hash() that returns `'id(self)'` will not do.**
* **That is why Python automatically makes classes unhashable if you only implement eq().*

```python
class MyHashable:
    def __init__(self, a):
        self._a = a
    @property
    def a(self):
        return self._a
    def __eq__(self, other):
        if isinstance(other, type(self)):
            return self.a == other.a
        return NotImplemented
    def __hash__(self):
        return hash(self.a)
```

### Sortable

* **With total_ordering decorator, you only need to provide eq() and one of lt(), gt(), le() or ge() special methods.*

```python
from functools import total_ordering

@total_ordering
class MySortable:
    def __init__(self, a):
        self.a = a
    def __eq__(self, other):
        if isinstance(other, type(self)):
            return self.a == other.a
        return NotImplemented
    def __lt__(self, other):
        if isinstance(other, type(self)):
            return self.a < other.a
        return NotImplemented
```

### Iterator

* **Any object that has methods next() and iter() is an iterator.**
* **Next() should return next item or raise StopIteration.**
* **Iter() should return 'self'.*

```python
class Counter:
    def __init__(self):
        self.i = 0
    def __next__(self):
        self.i += 1
        return self.i
    def __iter__(self):
        return self
```

```python
>>> counter = Counter()
>>> next(counter), next(counter), next(counter)
(1, 2, 3)
```

#### Python has many different iterator objects:

* **Sequence iterators returned by the [iter()](#iterator) function, such as list_iterator and set_iterator.**
* **Objects returned by the [itertools](#itertools) module, such as count, repeat and cycle.**
* **Generators returned by the [generator functions](#generator) and [generator expressions](#comprehensions).**
* **File objects returned by the [open()](#open) function, etc.*

### Callable

* **All functions and classes have a call() method, hence are callable.**
* **When this cheatsheet uses `'<function>'</function>` as an argument, it actually means `'<callable>'</callable>`.*

```python
class Counter:
    def __init__(self):
        self.i = 0
    def __call__(self):
        self.i += 1
        return self.i
```

```python
>>> counter = Counter()
>>> counter(), counter(), counter()
(1, 2, 3)
```

### Context Manager

* **Enter() should lock the resources and optionally return an object.**
* **Exit() should release the resources.**
* **Any exception that happens inside the with block is passed to the exit() method.**
* **If it wishes to suppress the exception it must return a true value.*

```python
class MyOpen:
    def __init__(self, filename):
        self.filename = filename
    def __enter__(self):
        self.file = open(self.filename)
        return self.file
    def __exit__(self, exc_type, exception, traceback):
        self.file.close()
```

```python
>>> with open('test.txt', 'w') as file:
...     file.write('Hello World!')
>>> with MyOpen('test.txt') as file:
...     print(file.read())
Hello World!
```

## Iterable Duck Types

### Iterable

* **Only required method is iter(). It should return an iterator of object's items.**
* **Contains() automatically works on any object that has iter() defined.*

```python
class MyIterable:
    def __init__(self, a):
        self.a = a
    def __iter__(self):
        return iter(self.a)
    def __contains__(self, el):
        return el in self.a
```

```python
>>> obj = MyIterable([1, 2, 3])
>>> [el for el in obj]
[1, 2, 3]
>>> 1 in obj
True
```

### Collection

* **Only required methods are iter() and len().**
* **This cheatsheet actually means `'<iterable>'</iterable>` when it uses `'<collection>'</collection>`.**
* **I chose not to use the name 'iterable' because it sounds scarier and more vague than 'collection'.*

```python
class MyCollection:
    def __init__(self, a):
        self.a = a
    def __iter__(self):
        return iter(self.a)
    def __contains__(self, el):
        return el in self.a
    def __len__(self):
        return len(self.a)
```

### Sequence

* **Only required methods are len() and getitem().**
* **Getitem() should return an item at index or raise IndexError.**
* **Iter() and contains() automatically work on any object that has getitem() defined.**
* **Reversed() automatically works on any object that has len() and getitem() defined.*

```python
class MySequence:
    def __init__(self, a):
        self.a = a
    def __iter__(self):
        return iter(self.a)
    def __contains__(self, el):
        return el in self.a
    def __len__(self):
        return len(self.a)
    def __getitem__(self, i):
        return self.a[i]
    def __reversed__(self):
        return reversed(self.a)
```

### ABC Sequence

* **It's a richer interface than the basic sequence.**
* **Extending it generates iter(), contains(), reversed(), index() and count().**
* **Unlike `'abc.Iterable'` and `'abc.Collection'`, it is not a duck type. That is why `'issubclass(MySequence, abc.Sequence)'` would return False even if MySequence had all the methods defined.*

```python
from collections import abc

class MyAbcSequence(abc.Sequence):
    def __init__(self, a):
        self.a = a
    def __len__(self):
        return len(self.a)
    def __getitem__(self, i):
        return self.a[i]
```

#### Table of required and automatically available special methods:

```
+------------+------------+------------+------------+--------------+
|            |  Iterable  | Collection |  Sequence  | abc.Sequence |
+------------+------------+------------+------------+--------------+
| iter()     |    REQ     |    REQ     |    Yes     |     Yes      |
| contains() |    Yes     |    Yes     |    Yes     |     Yes      |
| len()      |            |    REQ     |    REQ     |     REQ      |
| getitem()  |            |            |    REQ     |     REQ      |
| reversed() |            |            |    Yes     |     Yes      |
| index()    |            |            |            |     Yes      |
| count()    |            |            |            |     Yes      |
+------------+------------+------------+------------+--------------+
```

* **Other ABCs that generate missing methods are: MutableSequence, Set, MutableSet, Mapping and MutableMapping.**
* **Names of their required methods are stored in `'<abc>.__abstractmethods__'</abc>`.*

## Enum

```python
from enum import Enum, auto

class <enum_name>(Enum):
    <member_name_1> = <value_1>
    <member_name_2> = <value_2_a>, <value_2_b>
    <member_name_3> = auto()
```

* **If there are no numeric values before auto(), it returns 1.**
* **Otherwise it returns an increment of the last numeric value.*

```python
<member> = <enum>.<member_name>                 # Returns a member.
<member> = <enum>['']              # Returns a member or raises KeyError.
<member> = <enum>(<value>)                      # Returns a member or raises ValueError.
<str>    = <member>.name                        # Returns member's name.
<obj>    = <member>.value                       # Returns member's value.
```

```python
list_of_members = list(<enum>)
member_names    = [a.name for a in <enum>]
member_values   = [a.value for a in <enum>]
random_member   = random.choice(list(<enum>))
```

```python
def get_next_member(member):
    members = list(member.__class__)
    index   = (members.index(member) + 1) % len(members)
    return members[index]
```

### Inline

```python
Cutlery = Enum('Cutlery', 'fork knife spoon')
Cutlery = Enum('Cutlery', ['fork', 'knife', 'spoon'])
Cutlery = Enum('Cutlery', {'fork': 1, 'knife': 2, 'spoon': 3})
```

#### User-defined functions cannot be values, so they must be wrapped:

```python
from functools import partial
LogicOp = Enum('LogicOp', {'AND': partial(lambda l, r: l and r),
                           'OR' : partial(lambda l, r: l or r)})
```

* **Another solution in this particular case is to use functions and_() and or_() from the module [operator](#operator).*

## Exceptions

### Basic Example

```python
try:
    <code>
except <exception>:
    <code>
```

### Complex Example

```python
try:
    <code_1>
except <exception_a>:
    <code_2_a>
except <exception_b>:
    <code_2_b>
else:
    <code_2_c>
finally:
    <code_3>
```

* **Code inside the `'else'` block will only be executed if `'try'` block had no exceptions.**
* **Code inside the `'finally'` block will always be executed.*

### Catching Exceptions

```python
except <exception>:
except <exception> as <name>:
except (<exception>, [...]):
except (<exception>, [...]) as <name>:
```

* **Also catches subclasses of the exception.**
* **Use `'traceback.print_exc()'` to print the error message to stderr.**
* **Use `'print(<name>)'</name>` to print just the cause of the exception (its arguments).*

### Raising Exceptions

```python
raise <exception>
raise <exception>()
raise <exception>(<el> [, ...])
```

#### Re-raising caught exception:

```python
except <exception> as <name>:
    ...
    raise
```

### Exception Object

```python
arguments = <name>.args
exc_type  = <name>.__class__
filename  = <name>.__traceback__.tb_frame.f_code.co_filename
func_name = <name>.__traceback__.tb_frame.f_code.co_name
line      = linecache.getline(filename, <name>.__traceback__.tb_lineno)
error_msg = ''.join(traceback.format_exception(exc_type, <name>, <name>.__traceback__))
```

### Built-in Exceptions

```
BaseException
 +-- SystemExit                   # Raised by the sys.exit() function.
 +-- KeyboardInterrupt            # Raised when the user hits the interrupt key (ctrl-c).
 +-- Exception                    # User-defined exceptions should be derived from this class.
      +-- ArithmeticError         # Base class for arithmetic errors.
      |    +-- ZeroDivisionError  # Raised when dividing by zero.
      +-- AttributeError          # Raised when an attribute is missing.
      +-- EOFError                # Raised by input() when it hits end-of-file condition.
      +-- LookupError             # Raised when a look-up on a collection fails.
      |    +-- IndexError         # Raised when a sequence index is out of range.
      |    +-- KeyError           # Raised when a dictionary key or set element is not found.
      +-- NameError               # Raised when a variable name is not found.
      +-- OSError                 # Errors such as &#x201C;file not found&#x201D; or &#x201C;disk full&#x201D; (see Open).
      |    +-- FileNotFoundError  # When a file or directory is requested but doesn't exist.
      +-- RuntimeError            # Raised by errors that don't fall into other categories.
      |    +-- RecursionError     # Raised when the maximum recursion depth is exceeded.
      +-- StopIteration           # Raised by next() when run on an empty iterator.
      +-- TypeError               # Raised when an argument is of wrong type.
      +-- ValueError              # When an argument is of right type but inappropriate value.
           +-- UnicodeError       # Raised when encoding/decoding strings to/from bytes fails.
```

#### Collections and their exceptions:

```
+-----------+------------+------------+------------+
|           |    List    |    Set     |    Dict    |
+-----------+------------+------------+------------+
| getitem() | IndexError |            |  KeyError  |
| pop()     | IndexError |  KeyError  |  KeyError  |
| remove()  | ValueError |  KeyError  |            |
| index()   | ValueError |            |            |
+-----------+------------+------------+------------+
```

#### Useful built-in exceptions:

```python
raise TypeError('Argument is of wrong type!')
raise ValueError('Argument is of right type but inappropriate value!')
raise RuntimeError('None of above!')
```

### User-defined Exceptions

```python
class MyError(Exception):
    pass

class MyInputError(MyError):
    pass
```

## Exit

**Exits the interpreter by raising SystemExit exception.**

```python
import sys
sys.exit()                        # Exits with exit code 0 (success).
sys.exit(<el>)                    # Prints to stderr and exits with 1.
sys.exit(<int>)                   # Exits with passed exit code.
```

## Print

```python
print(<el_1>, ..., sep=' ', end='\n', file=sys.stdout, flush=False)
```

* **Use `'file=sys.stderr'` for messages about errors.**
* **Use `'flush=True'` to forcibly flush the stream.*

### Pretty Print

```python
from pprint import pprint
pprint(<collection>, width=80, depth=None, compact=False, sort_dicts=True)
```

* **Levels deeper than 'depth' get replaced by '...'.*

## Input

**Reads a line from user input or pipe if present.**

```python
<str> = input(prompt=None)
```

* **Trailing newline gets stripped.**
* **Prompt string is printed to the standard output before reading input.**
* **Raises EOFError when user hits EOF (ctrl-d/z) or input stream gets exhausted.*

## Command Line Arguments

```python
import sys
scripts_path = sys.argv[0]
arguments    = sys.argv[1:]
```

### Argument Parser

```python
from argparse import ArgumentParser, FileType
p = ArgumentParser(description=<str>)
p.add_argument('-', '--', action='store_true')  # Flag
p.add_argument('-', '--', type=<type>)          # Option
p.add_argument('', type=<type>, nargs=1)                    # First argument
p.add_argument('', type=<type>, nargs='+')                  # Remaining arguments
p.add_argument('', type=<type>, nargs='*')                  # Optional arguments
args  = p.parse_args()                                            # Exits on error.
value = args.<name>
```

* **Use `'help=<str>'</str>` to set argument description.**
* **Use `'default=<el>'</el>` to set the default value.**
* **Use `'type=FileType(<mode>)'</mode>` for files.*

## Open

**Opens the file and returns a corresponding file object.**

```python
<file> = open(<path>, mode='r', encoding=None, newline=None)
```

* **`'encoding=None'` means that the default encoding is used, which is platform dependent. Best practice is to use `'encoding="utf-8"'` whenever possible.**
* **`'newline=None'` means all different end of line combinations are converted to '\n' on read, while on write all '\n' characters are converted to system's default line separator.**
* **`'newline=""'` means no conversions take place, but input is still broken into chunks by readline() and readlines() on either '\n', '\r' or '\r\n'.*

### Modes

* **`'r'` - Read (default).**
* **`'w'` - Write (truncate).**
* **`'x'` - Write or fail if the file already exists.**
* **`'a'` - Append.**
* **`'w+'` - Read and write (truncate).**
* **`'r+'` - Read and write from the start.**
* **`'a+'` - Read and write from the end.**
* **`'t'` - Text mode (default).**
* **`'b'` - Binary mode.*

### Exceptions

* **`'FileNotFoundError'` can be raised when reading with `'r'` or `'r+'`.**
* **`'FileExistsError'` can be raised when writing with `'x'`.**
* **`'IsADirectoryError'` and `'PermissionError'` can be raised by any.**
* **`'OSError'` is the parent class of all listed exceptions.*

### File Object

```python
<file>.seek(0)                      # Moves to the start of the file.
<file>.seek(offset)                 # Moves 'offset' chars/bytes from the start.
<file>.seek(0, 2)                   # Moves to the end of the file.
<bin_file>.seek(±offset, <anchor>)  # Anchor: 0 start, 1 current position, 2 end.
```

```python
<str/bytes> = <file>.read(size=-1)  # Reads 'size' chars/bytes or until EOF.
<str/bytes> = <file>.readline()     # Returns a line or empty string/bytes on EOF.
<list>      = <file>.readlines()    # Returns a list of remaining lines.
<str/bytes> = next(<file>)          # Returns a line using buffer. Do not mix.
```

```python
<file>.write(<str/bytes>)           # Writes a string or bytes object.
<file>.writelines(<collection>)     # Writes a coll. of strings or bytes objects.
<file>.flush()                      # Flushes write buffer.
```

* **Methods do not add or strip trailing newlines, even writelines().*

### Read Text from File

```python
def read_file(filename):
    with open(filename, encoding='utf-8') as file:
        return file.readlines()
```

### Write Text to File

```python
def write_to_file(filename, text):
    with open(filename, 'w', encoding='utf-8') as file:
        file.write(text)
```

## Paths

```python
from os import getcwd, path, listdir
from glob import glob
```

```python
<str>  = getcwd()                   # Returns the current working directory.
<str>  = path.join(<path>, ...)     # Joins two or more pathname components.
<str>  = path.abspath(<path>)       # Returns absolute path.
```

```python
<str>  = path.basename(<path>)      # Returns final component of the path.
<str>  = path.dirname(<path>)       # Returns path without the final component.
<tup.> = path.splitext(<path>)      # Splits on last period of the final component.
```

```python
<list> = listdir(path='.')          # Returns filenames located at path.
<list> = glob('')          # Returns paths matching the wildcard pattern.
```

```python
<bool> = path.exists(<path>)        # Or: .exists()
<bool> = path.isfile(<path>)        # Or: .is_file()
<bool> = path.isdir(<path>)         # Or: .is_dir()
```

### DirEntry

**Using scandir() instead of listdir() can significantly increase the performance of code that also needs file type information.**

```python
from os import scandir
```

```python
<iter> = scandir(path='.')          # Returns DirEntry objects located at path.
<str>  = <DirEntry>.path            # Returns whole path as a string.
<str>  = <DirEntry>.name            # Returns final component as a string.
<file> = open(<DirEntry>)           # Opens the file and returns file object.
```

### Path Object

```python
from pathlib import Path
```

```python
<Path> = Path(<path> [, ...])       # Accepts strings, Paths and DirEntry objects.
<Path> = <path> / <path> [/ ...]    # One of the paths must be a Path object.
```

```python
<Path> = Path()                     # Returns relative cwd. Also Path('.').
<Path> = Path.cwd()                 # Returns absolute cwd. Also Path().resolve().
<Path> = Path.home()                # Returns user's home directory.
<Path> = Path(__file__).resolve()   # Returns script's path if cwd wasn't changed.
```

```python
<Path> = <Path>.parent              # Returns Path without final component.
<str>  = <Path>.name                # Returns final component as a string.
<str>  = <Path>.stem                # Returns final component without extension.
<str>  = <Path>.suffix              # Returns final component's extension.
<tup.> = <Path>.parts               # Returns all components as strings.
```

```python
<iter> = <Path>.iterdir()           # Returns dir contents as Path objects.
<iter> = <Path>.glob('')   # Returns Paths matching the wildcard pattern.
```

```python
<str>  = str(<Path>)                # Returns path as a string.
<file> = open(<Path>)               # Opens the file and returns file object.
```

## OS Commands

### Files and Directories

* **Paths can be either strings, Paths or DirEntry objects.**
* **Functions report OS related errors by raising either OSError or one of its [subclasses](#exceptions-1).*

```python
import os, shutil
```

```python
os.chdir(<path>)                    # Changes the current working directory.
os.mkdir(<path>, mode=0o777)        # Creates a directory. Mode is in octal.
```

```python
shutil.copy(from, to)               # Copies the file. 'to' can exist or be a dir.
shutil.copytree(from, to)           # Copies the directory. 'to' must not exist.
```

```python
os.rename(from, to)                 # Renames/moves the file or directory.
os.replace(from, to)                # Same, but overwrites 'to' if it exists.
```

```python
os.remove(<path>)                   # Deletes the file.
os.rmdir(<path>)                    # Deletes the empty directory.
shutil.rmtree(<path>)               # Deletes the directory.
```

### Shell Commands

```python
import os
<str> = os.popen('').read()
```

#### Sends '1 + 1' to the basic calculator and captures its output:

```python
>>> from subprocess import run
>>> run('bc', input='1 + 1\n', capture_output=True, encoding='utf-8')
CompletedProcess(args='bc', returncode=0, stdout='2\n', stderr='')
```

#### Sends test.in to the basic calculator running in standard mode and saves its output to test.out:

```python
>>> from shlex import split
>>> os.popen('echo 1 + 1 > test.in')
>>> run(split('bc -s'), stdin=open('test.in'), stdout=open('test.out', 'w'))
CompletedProcess(args=['bc', '-s'], returncode=0)
>>> open('test.out').read()
'2\n'
```

## JSON

**Text file format for storing collections of strings and numbers.**

```python
import json
<str>    = json.dumps(<object>, ensure_ascii=True, indent=None)
<object> = json.loads(<str>)
```

### Read Object from JSON File

```python
def read_json_file(filename):
    with open(filename, encoding='utf-8') as file:
        return json.load(file)
```

### Write Object to JSON File

```python
def write_to_json_file(filename, an_object):
    with open(filename, 'w', encoding='utf-8') as file:
        json.dump(an_object, file, ensure_ascii=False, indent=2)
```

## Pickle

**Binary file format for storing objects.**

```python
import pickle
<bytes>  = pickle.dumps(<object>)
<object> = pickle.loads(<bytes>)
```

### Read Object from File

```python
def read_pickle_file(filename):
    with open(filename, 'rb') as file:
        return pickle.load(file)
```

### Write Object to File

```python
def write_to_pickle_file(filename, an_object):
    with open(filename, 'wb') as file:
        pickle.dump(an_object, file)
```

## CSV

**Text file format for storing spreadsheets.**

```python
import csv
```

### Read

```python
<reader> = csv.reader(<file>)       # Also: `dialect='excel', delimiter=','`.
<list>   = next(<reader>)           # Returns next row as a list of strings.
<list>   = list(<reader>)           # Returns list of remaining rows.
```

* **File must be opened with a `'newline=""'` argument, or newlines embedded inside quoted fields will not be interpreted correctly!*

### Write

```python
<writer> = csv.writer(<file>)       # Also: `dialect='excel', delimiter=','`.
<writer>.writerow(<collection>)     # Encodes objects using `str()`.
<writer>.writerows(<coll_of_coll>)  # Appends multiple rows.
```

* **File must be opened with a `'newline=""'` argument, or '\r' will be added in front of every '\n' on platforms that use '\r\n' line endings!*

### Parameters

* **`'dialect'` - Master parameter that sets the default values.**
* **`'delimiter'` - A one-character string used to separate fields.**
* **`'quotechar'` - Character for quoting fields that contain special characters.**
* **`'doublequote'` - Whether quotechars inside fields get doubled or escaped.**
* **`'skipinitialspace'` - Whether whitespace after delimiter gets stripped.**
* **`'lineterminator'` - Specifies how writer terminates rows.**
* **`'quoting'` - Controls the amount of quoting: 0 - as necessary, 1 - all.**
* **`'escapechar'` - Character for escaping 'quotechar' if 'doublequote' is False.*

### Dialects

```
+------------------+--------------+--------------+--------------+
|                  |     excel    |   excel-tab  |     unix     |
+------------------+--------------+--------------+--------------+
| delimiter        |       ','    |      '\t'    |       ','    |
| quotechar        |       '"'    |       '"'    |       '"'    |
| doublequote      |      True    |      True    |      True    |
| skipinitialspace |     False    |     False    |     False    |
| lineterminator   |    '\r\n'    |    '\r\n'    |      '\n'    |
| quoting          |         0    |         0    |         1    |
| escapechar       |      None    |      None    |      None    |
+------------------+--------------+--------------+--------------+
```

### Read Rows from CSV File

```python
def read_csv_file(filename):
    with open(filename, encoding='utf-8', newline='') as file:
        return list(csv.reader(file))
```

### Write Rows to CSV File

```python
def write_to_csv_file(filename, rows):
    with open(filename, 'w', encoding='utf-8', newline='') as file:
        writer = csv.writer(file)
        writer.writerows(rows)
```

## SQLite

**Server-less database engine that stores each database into a separate file.**

### Connect

**Opens a connection to the database file. Creates a new file if path doesn't exist.**

```python
import sqlite3
<conn> = sqlite3.connect(<path>)                # Also ':memory:'.
<conn>.close()                                  # Closes the connection.
```

### Read

**Returned values can be of type str, int, float, bytes or None.**

```python
<cursor> = <conn>.execute('')            # Can raise a subclass of sqlite3.Error.
<tuple>  = <cursor>.fetchone()                  # Returns next row. Also next().
<list>   = <cursor>.fetchall()                  # Returns remaining rows. Also list().
```

### Write

```python
<conn>.execute('')                       # Can raise a subclass of sqlite3.Error.
<conn>.commit()                                 # Commits all transactions since last commit.
```

#### Or:

```python
with <conn>:
    <conn>.execute('')
```

### Placeholders

* **Passed values can be of type str, int, float, bytes, None, bool, datetime.date or datetime.datetme.**
* **Bools will be stored and returned as ints and dates as [ISO formatted strings](#encode).*

```python
<conn>.execute('', <list/tuple>)         # Replaces '?'s in query with values.
<conn>.execute('', <dict/namedtuple>)    # Replaces ':'s with values.
<conn>.executemany('', <coll_of_above>)  # Runs execute() multiple times.
```

### Example

**In this example values are not actually saved because `'conn.commit()'` is omitted!**

```python
>>> conn = sqlite3.connect('test.db')
>>> conn.execute('CREATE TABLE person (person_id INTEGER PRIMARY KEY, name, height)')
>>> conn.execute('INSERT INTO person VALUES (NULL, ?, ?)', ('Jean-Luc', 187)).lastrowid
1
>>> conn.execute('SELECT * FROM person').fetchall()
[(1, 'Jean-Luc', 187)]
```

### MySQL

**Has a very similar interface, with differences listed below.**

```python
# $ pip3 install mysql-connector
from mysql import connector
<conn>   = connector.connect(host=<str>, ...)     # `user=, password=, database=`.
<cursor> = <conn>.cursor()                      # Only cursor has execute method.
<cursor>.execute('')                     # Can raise a subclass of connector.Error.
<cursor>.execute('', <list/tuple>)       # Replaces '%s's in query with values.
<cursor>.execute('', <dict/namedtuple>)  # Replaces '%()s's with values.
```

## Bytes

**Bytes object is an immutable sequence of single bytes. Mutable version is called bytearray.**

```python
<bytes> = b''                       # Only accepts ASCII characters and \x00-\xff.
<int>   = <bytes>[<index>]               # Returns int in range from 0 to 255.
<bytes> = <bytes>[<slice>]               # Returns bytes even if it has only one element.
<bytes> = <bytes>.join(<coll_of_bytes>)  # Joins elements using bytes object as separator.
```

### Encode

```python
<bytes> = bytes(<coll_of_ints>)          # Ints must be in range from 0 to 255.
<bytes> = bytes(<str>, 'utf-8')          # Or: .encode('utf-8')
<bytes> = <int>.to_bytes(n_bytes, ...)     # `byteorder='big/little', signed=False`.
<bytes> = bytes.fromhex('')         # Hex pairs can be separated by spaces.
```

### Decode

```python
<list>  = list(<bytes>)                  # Returns ints in range from 0 to 255.
<str>   = str(<bytes>, 'utf-8')          # Or: .decode('utf-8')
<int>   = int.from_bytes(<bytes>, ...)     # `byteorder='big/little', signed=False`.
'<hex>' = <bytes>.hex()                  # Returns a string of hexadecimal pairs.
```

### Read Bytes from File

```python
def read_bytes(filename):
    with open(filename, 'rb') as file:
        return file.read()
```

### Write Bytes to File

```python
def write_bytes(filename, bytes_obj):
    with open(filename, 'wb') as file:
        file.write(bytes_obj)
```

## Struct

* **Module that performs conversions between a sequence of numbers and a bytes object.**
* **Machine's native type sizes and byte order are used by default.*

```python
from struct import pack, unpack, iter_unpack
```

```python
<bytes>  = pack('', <num_1> [, <num_2>, ...])
<tuple>  = unpack('', <bytes>)
<tuples> = iter_unpack('', <bytes>)
```

```python
>>> pack('>hhl', 1, 2, 3)
b'\x00\x01\x00\x02\x00\x00\x00\x03'
>>> unpack('>hhl', b'\x00\x01\x00\x02\x00\x00\x00\x03')
(1, 2, 3)
```

### Format

#### For standard type sizes start format string with:

* **`'='` - native byte order (usually little-endian)**
* **`'<'` - little-endian**
* **`'>'` - big-endian (also `'!'`)*

#### Integer types. Use a capital letter for unsigned type. Minimum and standard sizes are in brackets:

* **`'x'` - pad byte**
* **`'b'` - char (1/1)**
* **`'h'` - short (2/2)**
* **`'i'` - int (2/4)**
* **`'l'` - long (4/4)**
* **`'q'` - long long (8/8)*

#### Floating point types:

* **`'f'` - float (4/4)**
* **`'d'` - double (8/8)*

## Array

**List that can only hold numbers of a predefined type. Available types and their minimum sizes in bytes are listed above. Sizes and byte order are always determined by the system.**

```python
from array import array
<array> = array('', <collection>)    # Array from collection of numbers.
<array> = array('', <bytes>)         # Array from bytes object.
<array> = array('', <array>)         # Treats array as a sequence of numbers.
<bytes> = bytes(<array>)                       # Or: .tobytes()
```

## Memory View

* **A sequence object that points to the memory of another object.**
* **Each element can reference a single or multiple consecutive bytes, depending on format.**
* **Order and number of elements can be changed with slicing.*

```python
<mview> = memoryview(<bytes/bytearray/array>)  # Immutable if bytes, else mutable.
<real>  = <mview>[<index>]                     # Returns an int or a float.
<mview> = <mview>[<slice>]                     # Mview with rearranged elements.
<mview> = <mview>.cast('')           # Casts memoryview to the new format.
<mview>.release()                              # Releases the object's memory buffer.
```

### Decode

```python
<bin_file>.write(<mview>)                      # Writes mview to the binary file.
<bytes> = bytes(<mview>)                       # Creates a new bytes object.
<bytes> = <bytes>.join(<coll_of_mviews>)       # Joins mviews using bytes object as sep.
<array> = array('', <mview>)         # Treats mview as a sequence of numbers.
```

```python
<list>  = list(<mview>)                        # Returns list of ints or floats.
<str>   = str(<mview>, 'utf-8')                # Treats mview as a bytes object.
<int>   = int.from_bytes(<mview>, ...)           # `byteorder='big/little', signed=False`.
'<hex>' = <mview>.hex()                        # Treats mview as a bytes object.
```

## Deque

**A thread-safe list with efficient appends and pops from either side. Pronounced "deck".**

```python
from collections import deque
<deque> = deque(<collection>, maxlen=None)
```

```python
<deque>.appendleft(<el>)                       # Opposite element is dropped if full.
<deque>.extendleft(<collection>)               # Collection gets reversed.
<el> = <deque>.popleft()                       # Raises IndexError if empty.
<deque>.rotate(n=1)                            # Rotates elements to the right.
```

## Threading

* **CPython interpreter can only run a single thread at a time.**
* **That is why using multiple threads won't result in a faster execution, unless at least one of the threads contains an I/O operation.*

```python
from threading import Thread, RLock, Semaphore, Event, Barrier
from concurrent.futures import ThreadPoolExecutor
```

### Thread

```python
<Thread> = Thread(target=<function>)           # Use `args=` to set arguments.
<Thread>.start()                               # Starts the thread.
<bool> = <Thread>.is_alive()                   # Checks if thread has finished executing.
<Thread>.join()                                # Waits for thread to finish.
```

* **Use `'kwargs=<dict>'</dict>` to pass keyword arguments to the function.**
* **Use `'daemon=True'`, or the program will not be able to exit while the thread is alive.*

### Lock

```python
<lock> = RLock()                               # Lock that can only be released by the owner.
<lock>.acquire()                               # Waits for lock to be available.
<lock>.release()                               # Makes lock available again.
```

#### Or:

```python
lock = RLock()
with lock:
    ...
```

### Semaphore, Event, Barrier

```python
<Semaphore> = Semaphore(value=1)               # Lock that can be acquired by 'value' threads.
<Event>     = Event()                          # Method wait() blocks until set() is called.
<Barrier>   = Barrier(n_times)                 # Wait() blocks until it's called n_times.
```

### Thread Pool Executor

**Object that manages thread execution.**

```python
<Exec> = ThreadPoolExecutor(max_workers=None)  # Or: `with ThreadPoolExecutor() as : ...`
<Exec>.shutdown(wait=True)                     # Blocks until all threads finish executing.
```

```python
<iter> = <Exec>.map(<func>, <args_1>, ...)     # A multithreaded and non-lazy map().
<Futr> = <Exec>.submit(<func>, <arg_1>, ...)   # Starts a thread and returns its Future object.
<bool> = <Futr>.done()                         # Checks if the thread has finished executing.
<obj>  = <Futr>.result()                       # Waits for thread to finish and returns result.
```

### Queue

**A thread-safe FIFO queue. For LIFO queue use LifoQueue.**

```python
from queue import Queue
<Queue> = Queue(maxsize=0)
```

```python
<Queue>.put(<el>)                              # Blocks until queue stops being full.
<Queue>.put_nowait(<el>)                       # Raises queue.Full exception if full.
<el> = <Queue>.get()                           # Blocks until queue stops being empty.
<el> = <Queue>.get_nowait()                    # Raises queue.Empty exception if empty.
```

## Operator

**Module of functions that provide the functionality of operators.**

```python
from operator import add, sub, mul, truediv, floordiv, mod, pow, neg, abs
from operator import eq, ne, lt, le, gt, ge
from operator import and_, or_, xor, not_
from operator import itemgetter, attrgetter, methodcaller
```

```python
import operator as op
elementwise_sum  = map(op.add, list_a, list_b)
sorted_by_second = sorted(<collection>, key=op.itemgetter(1))
sorted_by_both   = sorted(<collection>, key=op.itemgetter(1, 0))
product_of_elems = functools.reduce(op.mul, <collection>)
union_of_sets    = functools.reduce(op.or_, <coll_of_sets>)
LogicOp          = enum.Enum('LogicOp', {'AND': op.and_, 'OR': op.or_})
last_el          = op.methodcaller('pop')(<list>)
```

## Introspection

**Inspecting code at runtime.**

### Variables

```python
<list> = dir()                             # Names of local variables (incl. functions).
<dict> = vars()                            # Dict of local variables. Also locals().
<dict> = globals()                         # Dict of global variables.
```

### Attributes

```python
def __new__(cls): return super().__new__(cls)+-------------+-------------+
|   Classes   | Metaclasses |
+-------------+-------------|
|   MyClass --> MyMetaClass |
|             |     v       |
|    object -----> type <+  |
|             |     ^ +--+  |
|     str ----------+       |
+-------------+-------------+
+-------------+-------------+
|   Classes   | Metaclasses |
+-------------+-------------|
|   MyClass   | MyMetaClass |
|      v      |     v       |
|    object <----- type     |
|      ^      |             |
|     str     |             |
+-------------+-------------+
'async''await''asyncio.run()''debug''info''success''warning''error''critical''''''''''100 MB''1 month''monday at 12:00''''''''1 week, 3 days''2 months'$ kernprof -lv test.py
Line #   Hits     Time  Per Hit   % Time  Line Contents
=======================================================
     1                                    @profile
     2                                    def main():
     3      1    955.0    955.0     43.7      a = [*range(10000)]
     4      1   1231.0   1231.0     56.3      b = {*range(10000)}
$ python3 -m memory_profiler test.py
Line #         Mem usage      Increment   Line Contents
=======================================================
     1        37.668 MiB     37.668 MiB   @profile
     2                                    def main():
     3        38.012 MiB      0.344 MiB       a = [*range(10000)]
     4        38.477 MiB      0.465 MiB       b = {*range(10000)}
[0.1, 0.6, 0.8] => [1, 2, 1]'1''L''RGB''RGBA''HSV''fill=''outline=''#rrggbb[aa]'+-----------+-------------+------+-------------+
| sampwidth |     min     | zero |     max     |
+-----------+-------------+------+-------------+
|     1     |           0 |  128 |         255 |
|     2     |      -32768 |    0 |       32767 |
|     3     |    -8388608 |    0 |     8388607 |
|     4     | -2147483648 |    0 |  2147483647 |
+-----------+-------------+------+-------------+
'aggregate()''transform()'+-------------+-------------+-------------+---------------+
|             |    'sum'    |   ['sum']   | {'s': 'sum'}  |
+-------------+-------------+-------------+---------------+
| sr.apply(...) |      3      |    sum  3   |     s  3      |
| sr.agg(...)   |             |             |               |
+-------------+-------------+-------------+---------------+
+-------------+-------------+-------------+---------------+
|             |    'rank'   |   ['rank']  | {'r': 'rank'} |
+-------------+-------------+-------------+---------------+
| sr.apply(...) |             |      rank   |               |
| sr.agg(...)   |     x  1    |   x     1   |    r  x  1    |
| sr.trans(...) |     y  2    |   y     2   |       y  2    |
+-------------+-------------+-------------+---------------+
'[key_1, key_2]'+------------------------+---------------+------------+------------+--------------------------+
|                        |    'outer'    |   'inner'  |   'left'   |       Description        |
+------------------------+---------------+------------+------------+--------------------------+
| l.merge(r, on='y',     |    x   y   z  | x   y   z  | x   y   z  | Joins/merges on column.  |
|            how=...)      | 0  1   2   .  | 3   4   5  | 1   2   .  | Also accepts left_on and |
|                        | 1  3   4   5  |            | 3   4   5  | right_on parameters.     |
|                        | 2  .   6   7  |            |            | Uses 'inner' by default. |
+------------------------+---------------+------------+------------+--------------------------+
| l.join(r, lsuffix='l', |    x yl yr  z |            | x yl yr  z | Joins/merges on row keys.|
|           rsuffix='r', | a  1  2  .  . | x yl yr  z | 1  2  .  . | Uses 'left' by default.  |
|           how=...)       | b  3  4  4  5 | 3  4  4  5 | 3  4  4  5 | If r is a series, it is  |
|                        | c  .  .  6  7 |            |            | treated as a column.     |
+------------------------+---------------+------------+------------+--------------------------+
| pd.concat([l, r],      |    x   y   z  |     y      |            | Adds rows at the bottom. |
|           axis=0,      | a  1   2   .  |     2      |            | Uses 'outer' by default. |
|           join=...)      | b  3   4   .  |     4      |            | A series is treated as a |
|                        | b  .   4   5  |     4      |            | column. Use l.append(r)  |
|                        | c  .   6   7  |     6      |            | to add a row instead.    |
+------------------------+---------------+------------+------------+--------------------------+
| pd.concat([l, r],      |    x  y  y  z |            |            | Adds columns at the      |
|           axis=1,      | a  1  2  .  . | x  y  y  z |            | right end. Uses 'outer'  |
|           join=...)      | b  3  4  4  5 | 3  4  4  5 |            | by default. A series is  |
|                        | c  .  .  6  7 |            |            | treated as a column.     |
+------------------------+---------------+------------+------------+--------------------------+
| l.combine_first(r)     |    x   y   z  |            |            | Adds missing rows and    |
|                        | a  1   2   .  |            |            | columns. Also updates    |
|                        | b  3   4   5  |            |            | items that contain NaN.  |
|                        | c  .   6   7  |            |            | R must be a DataFrame.   |
+------------------------+---------------+------------+------------+--------------------------+
'axis=1'+-------------+-------------+-------------+---------------+
|             |    'sum'    |   ['sum']   | {'x': 'sum'}  |
+-------------+-------------+-------------+---------------+
| df.apply(...) |             |       x  y  |               |
| df.agg(...)   |     x  4    |  sum  4  6  |     x  4      |
|             |     y  6    |             |               |
+-------------+-------------+-------------+---------------+
+-------------+-------------+-------------+---------------+
|             |    'rank'   |   ['rank']  | {'x': 'rank'} |
+-------------+-------------+-------------+---------------+
| df.apply(...) |      x  y   |      x    y |        x      |
| df.agg(...)   |   a  1  1   |   rank rank |     a  1      |
| df.trans(...) |   b  2  2   | a    1    1 |     b  2      |
|             |             | b    2    2 |               |
+-------------+-------------+-------------+---------------+
'[col_key_1, col_key_2][row_key]'+-------------+-------------+-------------+-------------+---------------+
|             |    'sum'    |    'rank'   |   ['rank']  | {'x': 'rank'} |
+-------------+-------------+-------------+-------------+---------------+
| gb.agg(...)   |      x   y  |      x  y   |      x    y |        x      |
|             |  z          |   a  1  1   |   rank rank |     a  1      |
|             |  3   1   2  |   b  1  1   | a    1    1 |     b  1      |
|             |  6  11  13  |   c  2  2   | b    1    1 |     c  2      |
|             |             |             | c    2    2 |               |
+-------------+-------------+-------------+-------------+---------------+
| gb.trans(...) |      x   y  |      x  y   |             |               |
|             |  a   1   2  |   a  1  1   |             |               |
|             |  b  11  13  |   b  1  1   |             |               |
|             |  c  11  13  |   c  1  1   |             |               |
+-------------+-------------+-------------+-------------+---------------+
'cdef''pyx''os.path.join(sys._MEIPASS, )''#'</code> on a <a href="https://gto76.github.io/python-cheatsheet/" rel="nofollow">webpage</a> will limit the search to the titles.</strong></li>
</ul>
	                      </article>
	                  </div>
					</div>
				</div>
					<script async src="https://pagead2.googlesyndication.com/pagead/js/adsbygoogle.js"></script>
					<ins class="adsbygoogle"
					     style="display:block"
					     data-ad-format="autorelaxed"
					     data-ad-client="ca-pub-7963911354665843"
					     data-ad-slot="9109096810"></ins>
					<script>
					     (adsbygoogle = window.adsbygoogle || []).push({});
					</script>

                 <div id="issues" class="card mt-3">
                 	  <div class="card-header"><h5>Issues</h5></div>
                      <div class="card-body">
	                  <div class="review-list">
	                     <ul>
	                        <li>
	                           <div class="d-flex">
	                              <div class="left">
	                                 <span>
	                                 <img
	                                    data-original="https://avatars.githubusercontent.com/u/9513634?v=4"
	                                    class="lazy profile-pict-img img-fluid" alt="Adjusted web page for mobile use">
	                                 </span>
	                              </div>
	                              <div class="right">
	                                 <h4>
	                                    <a href="https://github.com/gto76/python-cheatsheet/issues/23"  rel="nofollow">
	                                    Adjusted web page for mobile use
	                                    </a>
	                                 </h4>

	                                 <div class="review-description">
	                                   <article class="markdown-body text-wrap" s>
		                                   <p>Thanks for the nice cheatsheet 😃
So I saw you wanted help for <code>Better mobile experience</code> and I made some changes:</p>
<ul>
<li>added viewport meta tag for the fonts to scale properly</li>
<li>moved the <code>*.js</code> files to the end of the html document, to guarante that the document is ready before they get executed</li>
<li>changed the way links are inserted in the headings, so that there is no need for absolute positions and negativ margins and a min-width for the html document</li>
<li>changed the url for the font so it also works locally</li>
<li>h1 width and silly walks banner now  scale with the screen width</li>
</ul>
<p>I did tests it with chrome and firefox devtools.</p>

	                                    </article>
	                                 </div>
	                                 <span class="publish py-3 d-inline-block w-100">
										opened  by s-weigand <i class="fa fa-commenting" aria-hidden="true"></i> 7
									</span>
	                              </div>
	                           </div>
	                        </li>
	                        <li>
	                           <div class="d-flex">
	                              <div class="left">
	                                 <span>
	                                 <img
	                                    data-original="https://avatars.githubusercontent.com/u/10780059?v=4"
	                                    class="lazy profile-pict-img img-fluid" alt="tidy tqdm usage">
	                                 </span>
	                              </div>
	                              <div class="right">
	                                 <h4>
	                                    <a href="https://github.com/gto76/python-cheatsheet/issues/79"  rel="nofollow">
	                                    tidy tqdm usage
	                                    </a>
	                                 </h4>

	                                 <div class="review-description">
	                                   <article class="markdown-body text-wrap" s>
		                                   <ul>
<li>adds a few common options</li>
<li>also uses <code><iter></code> instead of <code>[1, 2, 3]</code>. Maybe use <code><collection></code> instead? Or just leave as <code>[1, 2, 3]</code>?</li>
</ul>

	                                    </article>
	                                 </div>
	                                 <span class="publish py-3 d-inline-block w-100">
										opened  by casperdcl <i class="fa fa-commenting" aria-hidden="true"></i> 6
									</span>
	                              </div>
	                           </div>
	                        </li>
	                        <li>
	                           <div class="d-flex">
	                              <div class="left">
	                                 <span>
	                                 <img
	                                    data-original="https://avatars.githubusercontent.com/u/1396046?v=4"
	                                    class="lazy profile-pict-img img-fluid" alt="TODO">
	                                 </span>
	                              </div>
	                              <div class="right">
	                                 <h4>
	                                    <a href="https://github.com/gto76/python-cheatsheet/issues/12"  rel="nofollow">
	                                    TODO
	                                    </a>
	                                 </h4>

	                                 <div class="review-description">
	                                   <article class="markdown-body text-wrap" s>
		                                   <h2>Cheatsheet</h2>
<ul>
<li>[x] MemoryView</li>
<li>[x] Pathlib</li>
<li>[x] Asyncio</li>
<li>[x] Datetime</li>
<li>[x] Logging</li>
<li>[x] Dataclass</li>
</ul>
<h2>Page</h2>
<ul>
<li>[x] Static page (Automatic generation of <code>index.html</code> from <code>README.md</code> at commit)</li>
<li>[x] Better mobile experience (Help needed)</li>
<li>[x] Back to top button (Help needed)</li>
</ul>

	                                    </article>
	                                 </div>
	                                 <span class="publish py-3 d-inline-block w-100">
										opened  by gto76 <i class="fa fa-commenting" aria-hidden="true"></i> 6
									</span>
	                              </div>
	                           </div>
	                        </li>
	                        <li>
	                           <div class="d-flex">
	                              <div class="left">
	                                 <span>
	                                 <img
	                                    data-original="https://avatars.githubusercontent.com/u/13444509?v=4"
	                                    class="lazy profile-pict-img img-fluid" alt="Printable PDF">
	                                 </span>
	                              </div>
	                              <div class="right">
	                                 <h4>
	                                    <a href="https://github.com/gto76/python-cheatsheet/issues/20"  rel="nofollow">
	                                    Printable PDF
	                                    </a>
	                                 </h4>

	                                 <div class="review-description">
	                                   <article class="markdown-body text-wrap" s>
		                                   <p>Would be nice to have nice printable PDF for the wall hangers enthusiasts 🥇</p>

	                                    </article>
	                                 </div>
	                                 <span class="publish py-3 d-inline-block w-100">
										opened  by toubar <i class="fa fa-commenting" aria-hidden="true"></i> 4
									</span>
	                              </div>
	                           </div>
	                        </li>
	                        <li>
	                           <div class="d-flex">
	                              <div class="left">
	                                 <span>
	                                 <img
	                                    data-original="https://avatars.githubusercontent.com/u/2019313?v=4"
	                                    class="lazy profile-pict-img img-fluid" alt="Add several points about the regex module">
	                                 </span>
	                              </div>
	                              <div class="right">
	                                 <h4>
	                                    <a href="https://github.com/gto76/python-cheatsheet/issues/17"  rel="nofollow">
	                                    Add several points about the regex module
	                                    </a>
	                                 </h4>

	                                 <div class="review-description">
	                                   <article class="markdown-body text-wrap" s>
		                                   <p>Sorry about the barrage of pull requests. I just found this Cheat Sheet, and because I think it's an awesome resource, I have this strong urge to suggest improvements.</p>
<p>This one combines three additions to the <code>Regex</code> section to keep the PR volume low. I hope that's okay; feel free to take or leave what you think is appropriate. I'll also happily split this up if you prefer. (Also, this is it from me for today. :grin:)</p>
<ul>
<li>
<p>Warn about the default matching of unicode character classes. This is a serious source of bugs.</p>
</li>
<li>
<p>Show that patterns can be pre-compiled and reused for efficiency gains.</p>
</li>
<li>
<p>Mention <code>help(re)</code>, because it's a very good resource.</p>
</li>
</ul>

	                                    </article>
	                                 </div>
	                                 <span class="publish py-3 d-inline-block w-100">
										opened  by tilboerner <i class="fa fa-commenting" aria-hidden="true"></i> 4
									</span>
	                              </div>
	                           </div>
	                        </li>
	                        <li>
	                           <div class="d-flex">
	                              <div class="left">
	                                 <span>
	                                 <img
	                                    data-original="https://avatars.githubusercontent.com/u/8981427?v=4"
	                                    class="lazy profile-pict-img img-fluid" alt="Add a table of contents">
	                                 </span>
	                              </div>
	                              <div class="right">
	                                 <h4>
	                                    <a href="https://github.com/gto76/python-cheatsheet/issues/13"  rel="nofollow">
	                                    Add a table of contents
	                                    </a>
	                                 </h4>

	                                 <div class="review-description">
	                                   <article class="markdown-body text-wrap" s>
		                                   <p>Hi, I just wanted to add a table of contents to the page, to ease navigation and discovery.
I didn't test the static website part however (style for the new table of contents).
Thank you for this great cheatsheet!</p>

	                                    </article>
	                                 </div>
	                                 <span class="publish py-3 d-inline-block w-100">
										opened  by pierrepinard-2 <i class="fa fa-commenting" aria-hidden="true"></i> 4
									</span>
	                              </div>
	                           </div>
	                        </li>
	                        <li>
	                           <div class="d-flex">
	                              <div class="left">
	                                 <span>
	                                 <img
	                                    data-original="https://avatars.githubusercontent.com/u/44527695?v=4"
	                                    class="lazy profile-pict-img img-fluid" alt="List comprehension - order of loop variables">
	                                 </span>
	                              </div>
	                              <div class="right">
	                                 <h4>
	                                    <a href="https://github.com/gto76/python-cheatsheet/issues/2"  rel="nofollow">
	                                    List comprehension - order of loop variables
	                                    </a>
	                                 </h4>

	                                 <div class="review-description">
	                                   <article class="markdown-body text-wrap" s>
		                                   <p>In this section:</p>
<hr />
<pre><code class="language-python">out = [i+j for i in range(10) for j in range(10)]
</code></pre>
<h4>Is the same as:</h4>
<pre><code class="language-python">out = []
for i in range(10):
    for j in range(10):
        out.append(i+j)
</code></pre>
<hr />
<p>The loop variables i and j should be swapped in either the first or the second part. Maybe one of the 10s could even be changed into another value to make it clearer? For instance:</p>
<pre><code class="language-python">out = [i+j for j in range(5) for i in range(10)]
</code></pre>
<h4>Is the same as:</h4>
<pre><code class="language-python">out = []
for i in range(10):
    for j in range(5):
        out.append(i+j)
</code></pre>

	                                    </article>
	                                 </div>
	                                 <span class="publish py-3 d-inline-block w-100">
										opened  by Lyoug <i class="fa fa-commenting" aria-hidden="true"></i> 3
									</span>
	                              </div>
	                           </div>
	                        </li>
	                        <li>
	                           <div class="d-flex">
	                              <div class="left">
	                                 <span>
	                                 <img
	                                    data-original="https://avatars.githubusercontent.com/u/17747722?v=4"
	                                    class="lazy profile-pict-img img-fluid" alt="I have added Selenium reference code in your cheatsheet">
	                                 </span>
	                              </div>
	                              <div class="right">
	                                 <h4>
	                                    <a href="https://github.com/gto76/python-cheatsheet/issues/30"  rel="nofollow">
	                                    I have added Selenium reference code in your cheatsheet
	                                    </a>
	                                 </h4>

	                                 <div class="review-description">
	                                   <article class="markdown-body text-wrap" s>

	                                    </article>
	                                 </div>
	                                 <span class="publish py-3 d-inline-block w-100">
										opened  by NimishVerma <i class="fa fa-commenting" aria-hidden="true"></i> 3
									</span>
	                              </div>
	                           </div>
	                        </li>
	                        <li>
	                           <div class="d-flex">
	                              <div class="left">
	                                 <span>
	                                 <img
	                                    data-original="https://avatars.githubusercontent.com/u/8845353?v=4"
	                                    class="lazy profile-pict-img img-fluid" alt="Exceptions need more details">
	                                 </span>
	                              </div>
	                              <div class="right">
	                                 <h4>
	                                    <a href="https://github.com/gto76/python-cheatsheet/issues/56"  rel="nofollow">
	                                    Exceptions need more details
	                                    </a>
	                                 </h4>

	                                 <div class="review-description">
	                                   <article class="markdown-body text-wrap" s>
		                                   <p>Firstly, nice doc.</p>
<p>For exceptions, having a comment on which is executed for what failures would be good for <strong>else</strong> and <strong>finally</strong></p>

	                                    </article>
	                                 </div>
	                                 <span class="publish py-3 d-inline-block w-100">
										opened  by ntindle <i class="fa fa-commenting" aria-hidden="true"></i> 3
									</span>
	                              </div>
	                           </div>
	                        </li>
	                        <li>
	                           <div class="d-flex">
	                              <div class="left">
	                                 <span>
	                                 <img
	                                    data-original="https://avatars.githubusercontent.com/u/45515141?v=4"
	                                    class="lazy profile-pict-img img-fluid" alt="Add a directory with hyperlinks">
	                                 </span>
	                              </div>
	                              <div class="right">
	                                 <h4>
	                                    <a href="https://github.com/gto76/python-cheatsheet/issues/67"  rel="nofollow">
	                                    Add a directory with hyperlinks
	                                    </a>
	                                 </h4>

	                                 <div class="review-description">
	                                   <article class="markdown-body text-wrap" s>
		                                   <p>Add a directory on top of the Readme to skip to desired stuff</p>

	                                    </article>
	                                 </div>
	                                 <span class="publish py-3 d-inline-block w-100">
										opened  by DanBrown47 <i class="fa fa-commenting" aria-hidden="true"></i> 3
									</span>
	                              </div>
	                           </div>
	                        </li>
	                        <li>
	                           <div class="d-flex">
	                              <div class="left">
	                                 <span>
	                                 <img
	                                    data-original="https://avatars.githubusercontent.com/u/18562080?v=4"
	                                    class="lazy profile-pict-img img-fluid" alt="Update README.md - # Synthesizer">
	                                 </span>
	                              </div>
	                              <div class="right">
	                                 <h4>
	                                    <a href="https://github.com/gto76/python-cheatsheet/issues/105"  rel="nofollow">
	                                    Update README.md - # Synthesizer
	                                    </a>
	                                 </h4>

	                                 <div class="review-description">
	                                   <article class="markdown-body text-wrap" s>
		                                   <p>Made code working</p>

	                                    </article>
	                                 </div>
	                                 <span class="publish py-3 d-inline-block w-100">
										opened  by digitalzany <i class="fa fa-commenting" aria-hidden="true"></i> 0
									</span>
	                              </div>
	                           </div>
	                        </li>
	                        <li>
	                           <div class="d-flex">
	                              <div class="left">
	                                 <span>
	                                 <img
	                                    data-original="https://avatars.githubusercontent.com/u/22245117?v=4"
	                                    class="lazy profile-pict-img img-fluid" alt="add difference_update">
	                                 </span>
	                              </div>
	                              <div class="right">
	                                 <h4>
	                                    <a href="https://github.com/gto76/python-cheatsheet/issues/103"  rel="nofollow">
	                                    add difference_update
	                                    </a>
	                                 </h4>

	                                 <div class="review-description">
	                                   <article class="markdown-body text-wrap" s>

	                                    </article>
	                                 </div>
	                                 <span class="publish py-3 d-inline-block w-100">
										opened  by malmans2 <i class="fa fa-commenting" aria-hidden="true"></i> 0
									</span>
	                              </div>
	                           </div>
	                        </li>
	                        <li>
	                           <div class="d-flex">
	                              <div class="left">
	                                 <span>
	                                 <img
	                                    data-original="https://avatars.githubusercontent.com/u/31490329?v=4"
	                                    class="lazy profile-pict-img img-fluid" alt="added cumulative sum for list">
	                                 </span>
	                              </div>
	                              <div class="right">
	                                 <h4>
	                                    <a href="https://github.com/gto76/python-cheatsheet/issues/102"  rel="nofollow">
	                                    added cumulative sum for list
	                                    </a>
	                                 </h4>

	                                 <div class="review-description">
	                                   <article class="markdown-body text-wrap" s>
		                                   <p>sometimes we need to calculate cumulative sum for a list as follows:</p>
<pre><code class="language-python">def get_cumulative_sum(num_list: List[int]) -> List[int]:
    cumulative_sum = [0] * len(num_list)
    for i, v in enumerate(num_list):
        cumulative_sum[i] = v + (0 if i == 0 else cumulative_sum[i-1])
    return cumulative_sum
</code></pre>
<p>but it can be easily done with <code>itertools.accumulate</code> as follows:</p>
<pre><code class="language-python">cumulative_sum = list(itertools.accumulate(<list>))
</code></pre>

	                                    </article>
	                                 </div>
	                                 <span class="publish py-3 d-inline-block w-100">
										opened  by reyadussalahin <i class="fa fa-commenting" aria-hidden="true"></i> 0
									</span>
	                              </div>
	                           </div>
	                        </li>
	                        <li>
	                           <div class="d-flex">
	                              <div class="left">
	                                 <span>
	                                 <img
	                                    data-original="https://avatars.githubusercontent.com/u/20532236?v=4"
	                                    class="lazy profile-pict-img img-fluid" alt="Update Readme.md">
	                                 </span>
	                              </div>
	                              <div class="right">
	                                 <h4>
	                                    <a href="https://github.com/gto76/python-cheatsheet/issues/101"  rel="nofollow">
	                                    Update Readme.md
	                                    </a>
	                                 </h4>

	                                 <div class="review-description">
	                                   <article class="markdown-body text-wrap" s>
		                                   <p>changed confising phrases for any and all functions. Fixed code explaining all function to support all values instead of just iterable elements in the collection.</p>

	                                    </article>
	                                 </div>
	                                 <span class="publish py-3 d-inline-block w-100">
										opened  by PacificG <i class="fa fa-commenting" aria-hidden="true"></i> 1
									</span>
	                              </div>
	                           </div>
	                        </li>
	                        <li>
	                           <div class="d-flex">
	                              <div class="left">
	                                 <span>
	                                 <img
	                                    data-original="https://avatars.githubusercontent.com/u/13102982?v=4"
	                                    class="lazy profile-pict-img img-fluid" alt="Definition of any()">
	                                 </span>
	                              </div>
	                              <div class="right">
	                                 <h4>
	                                    <a href="https://github.com/gto76/python-cheatsheet/issues/98"  rel="nofollow">
	                                    Definition of any()
	                                    </a>
	                                 </h4>

	                                 <div class="review-description">
	                                   <article class="markdown-body text-wrap" s>
		                                   <p>The definition of any(collection) says "False if empty", but that's not the whole story.</p>
<p>any( [ False ] ) is False even though the argument is not empty.</p>

	                                    </article>
	                                 </div>
	                                 <span class="publish py-3 d-inline-block w-100">
										opened  by lagbolt <i class="fa fa-commenting" aria-hidden="true"></i> 1
									</span>
	                              </div>
	                           </div>
	                        </li>
	                        <li>
	                           <div class="d-flex">
	                              <div class="left">
	                                 <span>
	                                 <img
	                                    data-original="https://avatars.githubusercontent.com/u/58473917?v=4"
	                                    class="lazy profile-pict-img img-fluid" alt="Created LICENSE">
	                                 </span>
	                              </div>
	                              <div class="right">
	                                 <h4>
	                                    <a href="https://github.com/gto76/python-cheatsheet/issues/97"  rel="nofollow">
	                                    Created LICENSE
	                                    </a>
	                                 </h4>

	                                 <div class="review-description">
	                                   <article class="markdown-body text-wrap" s>
		                                   <p>Created MIT License to resolve issue #59 .</p>
<p>MIT license gives users express permission to reuse code for any purpose, sometimes even if code is part of proprietary software. As long as users include the original copy of the MIT license in their distribution, they can make any changes or modifications to the code to suit their own needs.</p>

	                                    </article>
	                                 </div>
	                                 <span class="publish py-3 d-inline-block w-100">
										opened  by Joe-Sin7h <i class="fa fa-commenting" aria-hidden="true"></i> 2
									</span>
	                              </div>
	                           </div>
	                        </li>
	                        <li>
	                           <div class="d-flex">
	                              <div class="left">
	                                 <span>
	                                 <img
	                                    data-original="https://avatars.githubusercontent.com/u/38338592?v=4"
	                                    class="lazy profile-pict-img img-fluid" alt="Add Recursive Directory Creation">
	                                 </span>
	                              </div>
	                              <div class="right">
	                                 <h4>
	                                    <a href="https://github.com/gto76/python-cheatsheet/issues/96"  rel="nofollow">
	                                    Add Recursive Directory Creation
	                                    </a>
	                                 </h4>

	                                 <div class="review-description">
	                                   <article class="markdown-body text-wrap" s>
		                                   <p><code>os.makedirs</code> is a great way to create directories and sub directories recursively. Existing directories can also be ignored by setting the <code>exist_ok</code> argument to <code>True</code>.</p>

	                                    </article>
	                                 </div>
	                                 <span class="publish py-3 d-inline-block w-100">
										opened  by sukumar-varma <i class="fa fa-commenting" aria-hidden="true"></i> 1
									</span>
	                              </div>
	                           </div>
	                        </li>
	                        <li>
	                           <div class="d-flex">
	                              <div class="left">
	                                 <span>
	                                 <img
	                                    data-original="https://avatars.githubusercontent.com/u/81474805?v=4"
	                                    class="lazy profile-pict-img img-fluid" alt="Added an "index" method fot tuple">
	                                 </span>
	                              </div>
	                              <div class="right">
	                                 <h4>
	                                    <a href="https://github.com/gto76/python-cheatsheet/issues/95"  rel="nofollow">
	                                    Added an "index" method fot tuple
	                                    </a>
	                                 </h4>

	                                 <div class="review-description">
	                                   <article class="markdown-body text-wrap" s>

	                                    </article>
	                                 </div>
	                                 <span class="publish py-3 d-inline-block w-100">
										opened  by andrei-lus <i class="fa fa-commenting" aria-hidden="true"></i> 0
									</span>
	                              </div>
	                           </div>
	                        </li>
	                        <li>
	                           <div class="d-flex">
	                              <div class="left">
	                                 <span>
	                                 <img
	                                    data-original="https://avatars.githubusercontent.com/u/62749354?v=4"
	                                    class="lazy profile-pict-img img-fluid" alt="bg colors of plotly updated">
	                                 </span>
	                              </div>
	                              <div class="right">
	                                 <h4>
	                                    <a href="https://github.com/gto76/python-cheatsheet/issues/82"  rel="nofollow">
	                                    bg colors of plotly updated
	                                    </a>
	                                 </h4>

	                                 <div class="review-description">
	                                   <article class="markdown-body text-wrap" s>
		                                   <p>added more attributes to the graph (plotly)</p>

	                                    </article>
	                                 </div>
	                                 <span class="publish py-3 d-inline-block w-100">
										opened  by rajUwU <i class="fa fa-commenting" aria-hidden="true"></i> 0
									</span>
	                              </div>
	                           </div>
	                        </li>
	                        <li>
	                           <div class="d-flex">
	                              <div class="left">
	                                 <span>
	                                 <img
	                                    data-original="https://avatars.githubusercontent.com/u/46633059?v=4"
	                                    class="lazy profile-pict-img img-fluid" alt="Addition of Data Structures & algorithms libraries(with examples) ">
	                                 </span>
	                              </div>
	                              <div class="right">
	                                 <h4>
	                                    <a href="https://github.com/gto76/python-cheatsheet/issues/76"  rel="nofollow">
	                                    Addition of Data Structures & algorithms libraries(with examples)
	                                    </a>
	                                 </h4>

	                                 <div class="review-description">
	                                   <article class="markdown-body text-wrap" s>
		                                   <p>The following pull request proposes 2 additions:</p>
<ol>
<li>
<p>DAta Structures libraries like llist, binarytree to the cheatsheet</p>
</li>
<li>
<p>Addition of tty library with an example of self-made keylogger</p>
</li>
</ol>

	                                    </article>
	                                 </div>
	                                 <span class="publish py-3 d-inline-block w-100">
										opened  by Khanejo <i class="fa fa-commenting" aria-hidden="true"></i> 0
									</span>
	                              </div>
	                           </div>
	                        </li>

	                     </ul>
	                    </div>
	                </div>
               </div>

               </div>
               <div class="col-lg-3 right">

                        <div id="basic" class="tab-pane fade show active">

	                     <div class="box shadow-sm rounded bg-white mb-3">
		                     <div class="box-title border-bottom p-3">
		                        <h6 class="m-0">Owner
		                        </h6>
		                     </div>
                              <div class="d-flex align-items-center p-3 job-item-header">
                                 <div class="overflow-hidden mr-2">
                                    <h6 class="font-weight-bold  -dark mb-0 text-truncate">
										Jure Šorn
									</h6>
                                    <div class="small text-gray-500">
									</div>
                                 </div>
                                 	<img class="img-fluid ml-auto" style="border-radius: 50%;" src="https://avatars.githubusercontent.com/u/1396046?v=4&s=60" alt="Jure Šorn">

                              </div>

		                     <div class="box-body p-3">
		                         <a href="https://github.com/gto76/python-cheatsheet"  rel="nofollow" class="btn btn-lg btn-block btn-danger mb-3"><i class="fa fa-github " aria-hidden="true"></i> gto76/python-cheatsheet</a>
		                     		<a href="https://gto76.github.io/python-cheatsheet/" rel="nofollow" class="btn btn-lg btn-block btn-dark mb-3"><i class="fa fa-home " aria-hidden="true"></i> https://gto76.github.io/python-cheatsheet/</a>
		                     </div>
	                     </div>

		 						   <div class="box shadow-sm mb-3 rounded bg-white ads-box">
				                     <div class="p-3 border-bottom">
				                        <a href="/repo/sourabh-joshi-awesome-quincy-larson-emails"><h6 class="font-weight-bold text-gold ">This repository is an archive of emails that are sent by the awesome Quincy Larson every week.</h6></a>
				                        <p class="mb-0 text-muted">Awesome Quincy Larson Email Archive This repository is an archive of emails that are sent by the awesome Quincy Larson every week. If you fi</p>
				                     </div>
				                     <div class="p-2">
				                     	 <img class="lazy img-fluid mr-3" style="border-radius: 50%;max-width: 15%" data-original="https://avatars.githubusercontent.com/u/38150665?v=4&s=60" alt="Sourabh Joshi" >
				                         <i class="fa fa-star ml-3" aria-hidden="true"></i> 409 <i class="fa fa-clock-o ml-3" aria-hidden="true"></i> Aug 13, 2021
				                     </div>
				                  </div>
		 						   <div class="box shadow-sm mb-3 rounded bg-white ads-box">
				                     <div class="p-3 border-bottom">
				                        <a href="/repo/HeLsEroC-awesome-resources"><h6 class="font-weight-bold text-gold ">Participants  of Bertelsmann Technology Scholarship created an awesome list of resources and they want to share it with the world, if you find illegal resources please report to us and we will remove.</h6></a>
				                        <p class="mb-0 text-muted">Participants of Bertelsmann Technology Scholarship created an awesome list of resources and they want to share it with the world, if you find illegal </p>
				                     </div>
				                     <div class="p-2">
				                     	 <img class="lazy img-fluid mr-3" style="border-radius: 50%;max-width: 15%" data-original="https://avatars.githubusercontent.com/u/75568936?v=4&s=60" alt="Wissem Marzouki" >
				                         <i class="fa fa-star ml-3" aria-hidden="true"></i> 27 <i class="fa fa-clock-o ml-3" aria-hidden="true"></i> Aug 9, 2021
				                     </div>
				                  </div>
		 						   <div class="box shadow-sm mb-3 rounded bg-white ads-box">
				                     <div class="p-3 border-bottom">
				                        <a href="/repo/Mr-B0b-BloodCheck"><h6 class="font-weight-bold text-gold ">BloodCheck enables Red and Blue Teams to manage multiple Neo4j databases and run Cypher queries against a BloodHound dataset.</h6></a>
				                        <p class="mb-0 text-muted">BloodCheck BloodCheck enables Red and Blue Teams to manage multiple Neo4j databases and run Cypher queries against a BloodHound dataset. Installation </p>
				                     </div>
				                     <div class="p-2">
				                     	 <img class="lazy img-fluid mr-3" style="border-radius: 50%;max-width: 15%" data-original="https://avatars.githubusercontent.com/u/6248411?v=4&s=60" alt="Mr B0b" >
				                         <i class="fa fa-star ml-3" aria-hidden="true"></i> 15 <i class="fa fa-clock-o ml-3" aria-hidden="true"></i> Jul 9, 2021
				                     </div>
				                  </div>
		 						   <div class="box shadow-sm mb-3 rounded bg-white ads-box">
				                     <div class="p-3 border-bottom">
				                        <a href="/repo/Suor-funcy-python-miscellaneous"><h6 class="font-weight-bold text-gold ">A fancy and practical functional tools</h6></a>
				                        <p class="mb-0 text-muted">Funcy A collection of fancy functional tools focused on practicality. Inspired by clojure, underscore and my own abstractions. Keep reading to get an </p>
				                     </div>
				                     <div class="p-2">
				                     	 <img class="lazy img-fluid mr-3" style="border-radius: 50%;max-width: 15%" data-original="https://avatars.githubusercontent.com/u/284103?v=4&s=60" alt="Alexander Schepanovski" >
				                         <i class="fa fa-star ml-3" aria-hidden="true"></i> 2.6k <i class="fa fa-clock-o ml-3" aria-hidden="true"></i> Aug 13, 2021
				                     </div>
				                  </div>
		 						   <div class="box shadow-sm mb-3 rounded bg-white ads-box">
				                     <div class="p-3 border-bottom">
				                        <a href="/repo/ml-tooling-best-of-python"><h6 class="font-weight-bold text-gold ">🏆 A ranked list of awesome Python open-source libraries and tools. Updated weekly.</h6></a>
				                        <p class="mb-0 text-muted">Best-of Python ?? A ranked list of awesome Python open-source libraries & tools. Updated weekly. This curated list contains 230 awesome open-source pr</p>
				                     </div>
				                     <div class="p-2">
				                     	 <img class="lazy img-fluid mr-3" style="border-radius: 50%;max-width: 15%" data-original="https://avatars.githubusercontent.com/u/45942048?v=4&s=60" alt="Machine Learning Tooling" >
				                         <i class="fa fa-star ml-3" aria-hidden="true"></i> 1.7k <i class="fa fa-clock-o ml-3" aria-hidden="true"></i> Aug 23, 2021
				                     </div>
				                  </div>
		 						   <div class="box shadow-sm mb-3 rounded bg-white ads-box">
				                     <div class="p-3 border-bottom">
				                        <a href="/repo/phuselab-pyVHR-python-miscellaneous"><h6 class="font-weight-bold text-gold ">Package pyVHR is a comprehensive framework for studying methods of pulse rate estimation relying on remote photoplethysmography (rPPG)</h6></a>
				                        <p class="mb-0 text-muted">Package pyVHR (short for Python framework for Virtual Heart Rate) is a comprehensive framework for studying methods of pulse rate estimation relying on remote photoplethysmography (rPPG)</p>
				                     </div>
				                     <div class="p-2">
				                     	 <img class="lazy img-fluid mr-3" style="border-radius: 50%;max-width: 15%" data-original="https://avatars.githubusercontent.com/u/26966022?v=4&s=60" alt="PHUSE Lab" >
				                         <i class="fa fa-star ml-3" aria-hidden="true"></i> 89 <i class="fa fa-clock-o ml-3" aria-hidden="true"></i> Aug 22, 2021
				                     </div>
				                  </div>
		 						   <div class="box shadow-sm mb-3 rounded bg-white ads-box">
				                     <div class="p-3 border-bottom">
				                        <a href="/repo/okieselbach-Munki-Middleware-Azure-Storage-python-miscellaneous"><h6 class="font-weight-bold text-gold ">Generate Azure Blob Storage account authentication headers for Munki</h6></a>
				                        <p class="mb-0 text-muted">Azure Blob Storage Authentication for Munki The Azure Blob Storage Middleware allows munki clients to connect securely, and directly to a munki repo h</p>
				                     </div>
				                     <div class="p-2">
				                     	 <img class="lazy img-fluid mr-3" style="border-radius: 50%;max-width: 15%" data-original="https://avatars.githubusercontent.com/u/26136457?v=4&s=60" alt="Oliver Kieselbach" >
				                         <i class="fa fa-star ml-3" aria-hidden="true"></i> 5 <i class="fa fa-clock-o ml-3" aria-hidden="true"></i> Jul 19, 2021
				                     </div>
				                  </div>
		 						   <div class="box shadow-sm mb-3 rounded bg-white ads-box">
				                     <div class="p-3 border-bottom">
				                        <a href="/repo/nottheswimmer-pytago-python-miscellaneous"><h6 class="font-weight-bold text-gold ">Transpiles some Python into human-readable Golang.</h6></a>
				                        <p class="mb-0 text-muted">pytago Transpiles some Python into human-readable Golang. Try out the web demo Installation and usage There are two "officially" supported ways to use</p>
				                     </div>
				                     <div class="p-2">
				                     	 <img class="lazy img-fluid mr-3" style="border-radius: 50%;max-width: 15%" data-original="https://avatars.githubusercontent.com/u/29849378?v=4&s=60" alt="Michael Phelps" >
				                         <i class="fa fa-star ml-3" aria-hidden="true"></i> 129 <i class="fa fa-clock-o ml-3" aria-hidden="true"></i> Aug 18, 2021
				                     </div>
				                  </div>
		 						   <div class="box shadow-sm mb-3 rounded bg-white ads-box">
				                     <div class="p-3 border-bottom">
				                        <a href="/repo/PacktWorkshops-The-Python-Workshop-python-miscellaneous"><h6 class="font-weight-bold text-gold ">A New, Interactive Approach to Learning Python</h6></a>
				                        <p class="mb-0 text-muted">This is the repository for The Python Workshop, published by Packt. It contains all the supporting project files necessary to work through the course from start to finish.</p>
				                     </div>
				                     <div class="p-2">
				                     	 <img class="lazy img-fluid mr-3" style="border-radius: 50%;max-width: 15%" data-original="https://avatars.githubusercontent.com/u/56252176?v=4&s=60" alt="Packt Workshops" >
				                         <i class="fa fa-star ml-3" aria-hidden="true"></i> 195 <i class="fa fa-clock-o ml-3" aria-hidden="true"></i> Aug 6, 2021
				                     </div>
				                  </div>
		 						   <div class="box shadow-sm mb-3 rounded bg-white ads-box">
				                     <div class="p-3 border-bottom">
				                        <a href="/repo/datacamp-viewflow"><h6 class="font-weight-bold text-gold ">Viewflow is an Airflow-based framework that allows data scientists to create data models without writing Airflow code.</h6></a>
				                        <p class="mb-0 text-muted">Viewflow Viewflow is a framework built on the top of Airflow that enables data scientists to create materialized views. It allows data scientists to f</p>
				                     </div>
				                     <div class="p-2">
				                     	 <img class="lazy img-fluid mr-3" style="border-radius: 50%;max-width: 15%" data-original="https://avatars.githubusercontent.com/u/6276968?v=4&s=60" alt="DataCamp" >
				                         <i class="fa fa-star ml-3" aria-hidden="true"></i> 85 <i class="fa fa-clock-o ml-3" aria-hidden="true"></i> Aug 6, 2021
				                     </div>
				                  </div>
		 						   <div class="box shadow-sm mb-3 rounded bg-white ads-box">
				                     <div class="p-3 border-bottom">
				                        <a href="/repo/ipython-ipython-python-miscellaneous"><h6 class="font-weight-bold text-gold ">IPython: Productive Interactive Computing</h6></a>
				                        <p class="mb-0 text-muted">IPython: Productive Interactive Computing Overview Welcome to IPython. Our full documentation is available on ipython.readthedocs.io and contains info</p>
				                     </div>
				                     <div class="p-2">
				                     	 <img class="lazy img-fluid mr-3" style="border-radius: 50%;max-width: 15%" data-original="https://avatars.githubusercontent.com/u/230453?v=4&s=60" alt="IPython" >
				                         <i class="fa fa-star ml-3" aria-hidden="true"></i> 14.9k <i class="fa fa-clock-o ml-3" aria-hidden="true"></i> Aug 18, 2021
				                     </div>
				                  </div>
		 						   <div class="box shadow-sm mb-3 rounded bg-white ads-box">
				                     <div class="p-3 border-bottom">
				                        <a href="/repo/peter9949-Team-Curie-python-miscellaneous"><h6 class="font-weight-bold text-gold ">Team Curie is a group of people working together to achieve a common aim</h6></a>
				                        <p class="mb-0 text-muted">Team Curie is a group of people working together to achieve a common aim. We are enthusiasts!.... We are setting the pace!.... We offer encouragement and motivation....And we believe TeamWork makes the DreamWork.</p>
				                     </div>
				                     <div class="p-2">
				                     	 <img class="lazy img-fluid mr-3" style="border-radius: 50%;max-width: 15%" data-original="https://avatars.githubusercontent.com/u/83517287?v=4&s=60" alt="null" >
				                         <i class="fa fa-star ml-3" aria-hidden="true"></i> 4 <i class="fa fa-clock-o ml-3" aria-hidden="true"></i> Aug 7, 2021
				                     </div>
				                  </div>
		 						   <div class="box shadow-sm mb-3 rounded bg-white ads-box">
				                     <div class="p-3 border-bottom">
				                        <a href="/repo/geekmomprojects-PyCascades2021"><h6 class="font-weight-bold text-gold ">Materials and information for my PyCascades 2021 Presentation</h6></a>
				                        <p class="mb-0 text-muted">Materials and information for PyCascades 2021 Presentation: Sparking Creativity in LED Art with CircuitPython</p>
				                     </div>
				                     <div class="p-2">
				                     	 <img class="lazy img-fluid mr-3" style="border-radius: 50%;max-width: 15%" data-original="https://avatars.githubusercontent.com/u/10366970?v=4&s=60" alt="GeekMomProjects" >
				                         <i class="fa fa-star ml-3" aria-hidden="true"></i> 18 <i class="fa fa-clock-o ml-3" aria-hidden="true"></i> Jul 17, 2021
				                     </div>
				                  </div>
		 						   <div class="box shadow-sm mb-3 rounded bg-white ads-box">
				                     <div class="p-3 border-bottom">
				                        <a href="/repo/HackingThings-SignedUEFIShell"><h6 class="font-weight-bold text-gold ">Information about a signed UEFI Shell that can be used when Secure Boot is enabled.</h6></a>
				                        <p class="mb-0 text-muted">SignedUEFIShell During our research of the BootHole vulnerability last year, we tried to find as many signed bootloaders as we could. We searched all </p>
				                     </div>
				                     <div class="p-2">
				                     	 <img class="lazy img-fluid mr-3" style="border-radius: 50%;max-width: 15%" data-original="https://avatars.githubusercontent.com/u/1608747?v=4&s=60" alt="Mickey" >
				                         <i class="fa fa-star ml-3" aria-hidden="true"></i> 40 <i class="fa fa-clock-o ml-3" aria-hidden="true"></i> Aug 12, 2021
				                     </div>
				                  </div>
		 						   <div class="box shadow-sm mb-3 rounded bg-white ads-box">
				                     <div class="p-3 border-bottom">
				                        <a href="/repo/hsfzxjy-lambdex"><h6 class="font-weight-bold text-gold ">Write complicated anonymous functions other than lambdas in Python.</h6></a>
				                        <p class="mb-0 text-muted">lambdex allows you to write multi-line anonymous function expression (called a lambdex) in an idiomatic manner. </p>
				                     </div>
				                     <div class="p-2">
				                     	 <img class="lazy img-fluid mr-3" style="border-radius: 50%;max-width: 15%" data-original="https://avatars.githubusercontent.com/u/4702188?v=4&s=60" alt="Xie Jingyi" >
				                         <i class="fa fa-star ml-3" aria-hidden="true"></i> 62 <i class="fa fa-clock-o ml-3" aria-hidden="true"></i> Aug 14, 2021
				                     </div>
				                  </div>
		 						   <div class="box shadow-sm mb-3 rounded bg-white ads-box">
				                     <div class="p-3 border-bottom">
				                        <a href="/repo/scravy-awesome-pattern-matching"><h6 class="font-weight-bold text-gold ">Pattern Matching for Python 3.7+ in a simple, yet powerful, extensible manner.</h6></a>
				                        <p class="mb-0 text-muted">Awesome Pattern Matching (apm) for Python pip install awesome-pattern-matching Simple Powerful Extensible Composable Functional Python 3.7+, PyPy3.7+ </p>
				                     </div>
				                     <div class="p-2">
				                     	 <img class="lazy img-fluid mr-3" style="border-radius: 50%;max-width: 15%" data-original="https://avatars.githubusercontent.com/u/295504?v=4&s=60" alt="Julian Fleischer" >
				                         <i class="fa fa-star ml-3" aria-hidden="true"></i> 85 <i class="fa fa-clock-o ml-3" aria-hidden="true"></i> Jun 8, 2021
				                     </div>
				                  </div>
		 						   <div class="box shadow-sm mb-3 rounded bg-white ads-box">
				                     <div class="p-3 border-bottom">
				                        <a href="/repo/isman7-gimp-python-development"><h6 class="font-weight-bold text-gold ">Some ideas and tools to develop Python 3.8 plugins for GIMP 2.99.4</h6></a>
				                        <p class="mb-0 text-muted">gimp-python-development Some ideas and tools to develop Python 3.8 plugins for GIMP 2.99.4. GIMP 2.99.4 is the latest unstable pre-release of GIMP 3. </p>
				                     </div>
				                     <div class="p-2">
				                     	 <img class="lazy img-fluid mr-3" style="border-radius: 50%;max-width: 15%" data-original="https://avatars.githubusercontent.com/u/9478220?v=4&s=60" alt="Ismael Benito" >
				                         <i class="fa fa-star ml-3" aria-hidden="true"></i> 46 <i class="fa fa-clock-o ml-3" aria-hidden="true"></i> Jul 7, 2021
				                     </div>
				                  </div>
		 						   <div class="box shadow-sm mb-3 rounded bg-white ads-box">
				                     <div class="p-3 border-bottom">
				                        <a href="/repo/SethMMorton-natsort-python-miscellaneous"><h6 class="font-weight-bold text-gold ">Simple yet flexible natural sorting in Python.</h6></a>
				                        <p class="mb-0 text-muted">natsort Simple yet flexible natural sorting in Python. Source Code: https://github.com/SethMMorton/natsort Downloads: https://pypi.org/project/natsort</p>
				                     </div>
				                     <div class="p-2">
				                     	 <img class="lazy img-fluid mr-3" style="border-radius: 50%;max-width: 15%" data-original="https://avatars.githubusercontent.com/u/1596189?v=4&s=60" alt="Seth Morton" >
				                         <i class="fa fa-star ml-3" aria-hidden="true"></i> 553 <i class="fa fa-clock-o ml-3" aria-hidden="true"></i> Aug 14, 2021
				                     </div>
				                  </div>
		 						   <div class="box shadow-sm mb-3 rounded bg-white ads-box">
				                     <div class="p-3 border-bottom">
				                        <a href="/repo/rayanht-paprika"><h6 class="font-weight-bold text-gold ">Paprika is a python library that reduces boilerplate. Heavily inspired by Project Lombok.</h6></a>
				                        <p class="mb-0 text-muted">Image courtesy of Anna Quaglia (Photographer) Paprika Paprika is a python library that reduces boilerplate. It is heavily inspired by Project Lombok. </p>
				                     </div>
				                     <div class="p-2">
				                     	 <img class="lazy img-fluid mr-3" style="border-radius: 50%;max-width: 15%" data-original="https://avatars.githubusercontent.com/u/42040895?v=4&s=60" alt="Rayan Hatout" >
				                         <i class="fa fa-star ml-3" aria-hidden="true"></i> 35 <i class="fa fa-clock-o ml-3" aria-hidden="true"></i> Jul 20, 2021
				                     </div>
				                  </div>
                     </div>

            </div>
         </div>

      </div>

	      <!--       footer -->
      <footer class="bg-white">
         <div class="container">

            <div class="copyright">
               <div class="logo">
                  <a href="/">
                  <img src="/assets/images/logo_pythonrepo.png">
                  </a>
               </div>
               <p>Copyright © 2021.PythonRepo All rights reserved.
               </p>
               <ul class="social">
                  <li>
                     <a href="#"><i class="fa fa-facebook" aria-hidden="true"></i></a>
                  </li>
                  <li>
                     <a href="#"><i class="fa fa-twitter" aria-hidden="true"></i></a>
                  </li>
                  <li>
                     <a href="#"><i class="fa fa-linkedin" aria-hidden="true"></i></a>
                  </li>
                  <li>
                     <a href="#"><i class="fa fa-pinterest-p" aria-hidden="true"></i></a>
                  </li>
                  <li>
                     <a href="#"><i class="fa fa-instagram" aria-hidden="true"></i></a>
                  </li>
               </ul>
            </div>
         </div>
      </footer>
      <!--       footer-->
      <!-- Bootstrap core JavaScript -->
      <script src="https://cdnjs.cloudflare.com/ajax/libs/jquery/3.4.1/jquery.min.js" integrity="sha512-bnIvzh6FU75ZKxp0GXLH9bewza/OIw6dLVh9ICg0gogclmYGguQJWl8U30WpbsGTqbIiAwxTsbe76DErLq5EDQ==" crossorigin="anonymous"></script>
	  <script src="https://cdnjs.cloudflare.com/ajax/libs/twitter-bootstrap/4.5.0/js/bootstrap.bundle.min.js" integrity="sha512-Oy5BruJdE3gP9+LMJ11kC5nErkh3p4Y0GawT1Jrcez4RTDxODf3M/KP3pEsgeOYxWejqy2SPnj+QMpgtvhDciQ==" crossorigin="anonymous"></script>
      <!-- select2 Js -->
      <script src="https://cdnjs.cloudflare.com/ajax/libs/select2/4.0.13/js/select2.min.js" integrity="sha512-2ImtlRlf2VVmiGZsjm9bEyhjGW4dU7B6TNwh/hx/iSByxNENtj3WVE6o/9Lj4TJeVXPi4bnOIMXFIJJAeufa0A==" crossorigin="anonymous"></script>
      <!-- Custom -->
      <script src="/assets/js/custom.js"></script>
  	<script src="https://cdnjs.cloudflare.com/ajax/libs/jquery.lazyload/1.9.1/jquery.lazyload.min.js"></script>

	  <script>
		$(function() {
			$("img.lazy").lazyload({
			    threshold :180,
			    failurelimit :20,
			    effect : "fadeIn"
			});
		});
	 </script>
	<script src="//cdnjs.cloudflare.com/ajax/libs/highlight.js/10.5.0/highlight.min.js"></script>
	<script>
        hljs.initHighlightingOnLoad();
    </script>

   </body>
</html><script src="/cdn-cgi/scripts/7d0fa10a/cloudflare-static/rocket-loader.min.js" data-cf-settings="7005721116b12a66a5f8f3f3-|49" defer=""></script>
```
