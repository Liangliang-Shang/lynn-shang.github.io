Title: Python Tutorial
Date: 2016-03-04 20:20  
Category: Python  
Tags: Python  
Slug: python_tutorial   
Author: lshang  
Summary: The Tutorial of Python Programming  

## String  
```python  
>>> "Let's go!"
"Let's go!"
>>> '"Hello, world!" she said'
'"Hello, world!" she said'
>>> 'Let\'s go!'
"Let's go!"
>>> 'Let\'s go!'
"Let's go!"
# repr creats a string that is representation of the value as a legal
# expression
>>> print repr("Hello, world!")
'Hello, world!'
>>> print repr(10000L)
10000L
>>> print '''This is a very long string.
... It continues here. 
... And it's not over yet.
... "Hello, world!"
... Still here.'''
This is a very long string.
It continues here. 
And it's not over yet.
"Hello, world!"
Still here.
>>> print 'Hello,\nworld!'
Hello,
world!
>>> print r'Hello,\nworld!'
Hello,\nworld!
>>> print r'Let\'s go!'
Let\'s go!
```

## List comprehension
```python
# map((lambda x: x**2), xrange(10))
>>> [ x ** 2 for x in xrange(10) ]
[0, 1, 4, 9, 16, 25, 36, 49, 64, 81]
>>> L = ['1', 'a', 2, 'b', '3', 'c']
# map((lambda x: int(x) if str(x).isdigit() else None), L)
>>> [ int(x) if str(x).isdigit() else None for x in L ]
[1, None, 2, None, 3, None]
>>> S = 'abc'
# map((lambda (x, y): x +y), [(x, y) for x in S for y in S])
>>> [ ''.join((x, y)) for x in S for y in S ]
['aa', 'ab', 'ac', 'ba', 'bb', 'bc', 'ca', 'cb', 'cc']
# map((lambda (x, y): (x, y)), 
#        filter((lambda (x, y): x%2 == 0 and y%2 ==1), 
#            [(x, y) for x in xrange(5) for y in xrange(5)]))
>>> [ (x, y) for x in xrange(5) if x % 2 == 0 for y in xrange(5) if y % 2 == 1 ]
[(0, 1), (0, 3), (2, 1), (2, 3), (4, 1), (4, 3)]
# map((lambda line: line.rstrip()), open(r'hello.py'))
>>> [ line.rstrip() for line in open(r'hello.py') ]
['#!/bin/env python', 'print "Hello, Python!"']
```
