---
layout: page
title: python notlarım
---
Mümkün olan her yerde `try`, `except`, `else` kullanmaya çalış.
```python
try:
    # Some Code.... 
except:
    # optional block
    # Handling of exception (if required)
else:
    # execute if no exception
finally:
    # Some code .....(always executed)
```
Saymak için `while` yerine `for` kullan (çok daha hızlı)
```python
def for_loop(n=100_000_000):
    s = 0
    for i in range(n):
        s += i
    return s

import timeit
print('for loop\t\t', timeit.timeit(for_loop, number=1))
```
