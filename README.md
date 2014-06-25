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

Japy is free, use it however you like (see LICENSE for details). 

Japy has no dependencies (other than some STL), just grab japy.hpp and go. 
For examples of use, see examples.cpp. Your feedback will be very much 
appreciated.

I will soon make some optimizations, and maybe add some features, but
the current public interface is unlikely to be changed. And, by the way,
it does not decode escaped UTF sequences yet, that will also be added. 

And here is what my 'json-path' language is:

sample: 
<code>array:/object:/array:some_name//!array:/?integral:another_name</code>

same as abbreviated form:
<code>#/$/#some_name//!#/?i:another_name</code>

Path consists of selectors. Selectors are separated by '/'.  
Selectors may contain any or all of these, in this order:  
* <code>/</code> - to mean 'recursive' (match not only children, but all descendants)  
* <code>!</code> - to mean 'inverse' (select nodes that do not match the selector)  
* <code>?</code> - to mean 'optional' (don't throw exceptions if selector does not match)  
* type - to specify type of node:  
    * <code>*</code> or <code>any:</code> - any type  
    * <code>#</code> or <code>#:</code> or <code>array:</code> - array  
    * <code>$</code> or <code>$:</code> or <code>object:</code> - object  
    * <code>@</code> or <code>@:</code> or <code>value:</code> - anything except <code>#</code> and <code>$</code>  
    * <code>i:</code> or <code>integral:</code> - integral values  
    * <code>f:</code> or <code>float:</code> - floating-point values  
    * <code>b:</code> or <code>boolean:</code> - boolean value (true or false)  
    * <code>n:</code> or <code>null:</code> - null  
    * <code>s:</code> or <code>string:</code> - string  
* <code>name</code> - name of node if it is a member of object (or quoted "name" if you  want to use symbols other than a-zA-Z0-9 and -_).  

That's it. Take a look at examples.cpp to see how it works.

Copyright © 2014, Artur Brugeman, brugeman.artur@gmail.com.
