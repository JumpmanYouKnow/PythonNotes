---
title: "Useful tool kit"
date: 2019-04-08
---
---------------------
Useful tools could be used in python development
#### 1. track memory usage line by line
https://pypi.org/project/memory_profiler/

#### 2. track run time for each line
https://pypi.org/project/line_profiler/

#### 3. regular expression
https://docs.python.org/3/library/re.html

#### 4. google word to vector, trained model
GoogleNews-vectors-negative300.bin
https://code.google.com/archive/p/word2vec/

#### 5. trace execution for each line/function flow
```python
python -m trace --count -C . somefile.py ...
```
[https://docs.python.org/3.7/library/trace.html](https://docs.python.org/3.7/library/trace.html)

#### 6. get time analysis for a statement execution
```
usage:
python -m timeit 'stmt' # number = 10000
or:
timeit.timeit('stmt', number=10000)
In Ipython:
%timeit 'stmt'
```
[https://docs.python.org/2/library/timeit.html](https://docs.python.org/2/library/timeit.html)

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE0NTc4Nzg1MTMsMTI0NDU2MDk2OV19
-->