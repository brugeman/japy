JAPY
====

JAPY is a new json parser in C++.

JAPY is yet another json path (and parser) thing, written 
in C++ (currently - C++11). It has some unusual features:

1. Stream parsing - if you are consuming, say, Twitter's json
streams, japy is for you.
2. Path language, allowing you to make complex traversals through
the json document with a single 'expression'.
3. Easy to use and efficient (not yet that much, but will soon become).

Japy is free, feel free to use it however you like (see LICENSE for details). 

For examples of use, see examples.cpp.

I will soon make some optimizations, and maybe add some features, but
the current public interface is unlikely to be changed. And, by the way,
it does not decode escaped UTF sequences, that will also be added. 

Your feedback will be very much appreciated.

And, yeah, here is what my 'json-path' language is:

sample: 
array:/object:/array:some_name//!array:/?decimal:another_name

same as abbreviated form:
#/$/#some_name//!#/?d:another_name

Path consists of selectors. Selectors are separated by '/'.
Selectors may contain any or all of these, in this order:
'/' - to mean 'recursive' (match not only children, but all descendants)
'!' - to mean 'inverse' (select nodes that do not match the selector)
'?' - to mean 'optional' (don't throw exceptions if selector does not match)
type - to specify type of node:
  '*' or 'any:' - any type
  '#' or '#:' or 'array:' - array
  '$' or '$:' or 'object:' - object
  '@' or '@:' or 'attribute:' - anything except # or $
  'd:' or 'decimal:' - decimal values
  'f:' or 'float:' - floating-point values
  'b:' or 'boolean:' - boolean value (true or false)
  'n:' or 'null:' - null
  's:' or 'string:' - string
name - name of node if it is a member of object (or quoted "name" if you 
       want to use symbols other than a-zA-Z0-9 and -_).

That's it. Take a look at examples.cpp to see how it works.

Copyright © 2014, Artur Brugeman, brugeman.artur@gmail.com.
