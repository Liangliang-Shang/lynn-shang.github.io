Title: Python Tutorial
Date: 2016-02-24 20:20  
Category: Python  
Tags: Python  
Slug: python_tutorial   
Author: lshang  
Summary: The Tutorial of Python Programming  

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
