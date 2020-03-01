---
layout: post
title: Built-in Sort in Python
---
# Main Idea
* `list.sort()`: **method** defined for **list**, modifies the list in-place (returns None)
* `sorted()`: built-in **function**, builds a new sorted list from an **iterable** (e.g. string -> list of characters, dict -> list of dictionary keys)

\* both sorts are **stable**

* example: sort v.s. sorted
```python
>>> 'acb'.sort()
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
AttributeError: 'str' object has no attribute 'sort'
>>> sorted('acb')
['a', 'b', 'c']
```

* caution: when using dictionary as an iterable
```python
>>> scores = {'Alice': 90, 'Carl': 95, 'Bob': 80}                                                                  
>>> list(scores)                                                                                                   
['Alice', 'Carl', 'Bob']
>>> for name in scores: # equivalent to scores.keys()
...     print(name)
... 
Alice
Carl
Bob
>>> sorted(scores)                                                                                      
['Alice', 'Bob', 'Carl']
```

# Arguments
* `key`: **function** to be called on each element, e.g. `str.lower`, `lambda x: x.attribute`
* `reverse`: False (default) - Ascending, True - Descending

```python
>>> sorted(scores, key=lambda x: scores[x], reverse=True)
['Carl', 'Alice', 'Bob']
```

Reference: [https://wiki.python.org/moin/HowTo/Sorting](https://wiki.python.org/moin/HowTo/Sorting)

Relevant:
1. [LeetCode 1366. Rank Teams by Votes]({% post_url 2020-03-01-lc1366 %})
