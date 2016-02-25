Title: Best Practice of Python Programming  
Date: 2016-02-16 23:20  
Category: Python  
Tags: Python  
Slug: python  
Author: lshang  
Summary: Best Practice of Python Programming  

## The Zen of Python
```python
import this
```
- The Zen of Python, by Tim Peters
```text

Beautiful is better than ugly.    
Explicit is better than implicit.    
Simple is better than complex.    
Complex is better than complicated.    
Flat is better than nested.    
Sparse is better than dense.    
Readability counts.    
Special cases aren’t special enough to break the rules.    
Although practicality beats purity.    
Errors should never pass silently.    
Unless explicitly silenced.    
In the face of ambiguity, refuse the temptation to guess.    
There should be one– and preferably only one –obvious way to do it.    
Although that way may not be obvious at first unless you’re Dutch.    
Now is better than never.    
Although never is often better than *right* now.    
If the implementation is hard to explain, it’s a bad idea.    
If the implementation is easy to explain, it may be a good idea.    
Namespaces are one honking great idea — let’s do more of those!     
```

> Programs  must    be  written for people  to  read,   and only
> incidentally  for machines    to execute.  
> —Abelson  &   Sussman,    Structure   and Interpretation  of  Computer
> Programs  

## Style Guide
[PEP 0008 – Style Guide for Python Code](https://www.python.org/dev/peps/pep-0008/)  

- 4 spaces per indentation level  

- No hard tabs  

- One blank line between functions  

- Two blank lines between classes  

- Add a space after “,” in dicts, lists, tuples, & argument lists, and after “:” in dicts, but not before  

- Put spaces around assignments & comparisons (except in argument lists)  

- No spaces just inside parentheses or just before argument lists  

- No spaces just inside docstrings  

```python
def make_squares(key, value=0):
    """Return a dictionary and a list..."""
    d = {key: value}
    l = [key, value]
    return d, l
```
- Long Lines & Continuations：Keep lines below 80 characters in length  
    - Use implied line continuation inside parentheses/brackets/braces:
    - Use backslashes as a last resort:    
```python
def __init__(self, first, second, third, 
                fourth, fifth, sixth):
    output = (first + second + third
                + fourth + fifth + sixth)

VeryLong.left_hand_side \
        = even_longer.right_hand_side()
```
- Docstrings & Comment
    - Docstrings = How to use code [Docstring Conventions](https://www.python.org/dev/peps/pep-0257/)  
    - Comments = Why (rationale) & how code works  

## Best Practice 
- shebang & coding line
```python
#!/bin/env python
#-*- coding: utf-8 -*-
```
- Swap values  
```python
b, a = a, b
```
- Build a tuple, the comma is the tuple constructor, not the parenthese.  
```python
>>> 1,
(1,)
>>> (1, )
(1,)
>>> (1)
1
>>> 1
1
>>> (1) == 1
True
>>> (1, ) == 1
False
```
- Unpacked tuple  
```python
>>> l = ['A', 'B', 'C']
>>> a, b, c = l
>>> a
'A'
>>> b
'B'
>>> c
'C'
>>> charset = [l, ['D', 'E', 'F']]
>>> for(a, b, c) in charset:
...     print a, b, c
... 
A B C
D E F
>>> firstset, (a, b, c) = charset
>>> a
'D'
>>> b
'E'
>>> c
'F'
```
- join strings in a list rather than iterate the list and concatenate
```python
>>> colors = ['red', 'blue', 'green', 'yellow']
>>> result = ' '.join(colors)
>>> result
'red blue green yellow'
```
- index & item
```python
>>> items = ['zero', 'one', 'two', 'three']
>>> for(index, item) in enumerate(items):
...     print index, item
...
0 zero
1 one
2 two
3 three
```
- randomly choose one from a list  
```python
>>> import random
>>> random.choice(range(10))
6
```

