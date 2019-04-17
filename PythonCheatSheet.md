---
title: "Python CheatSheet"
date: 2019-04-08
---
##### This cheatsheet includes some very basic but easy to forget operations and some random notes.
##### [A good tutorial for beginner in Chinese](https://gist.github.com/SEKIRO-J/217f84929b37d40b827abbb1b6796342)
---------------------
### 1. Decorator Syntax
```Python
def decorator(func):  
	def new_func(*args, **argkw):  
		#add stuff
		print("Hello World")   
		return func(*args, **argkw)
return new_func 
 
@decorator  
def f(args):
	pass

#run function f
f()
#result:
#Hello World
```

### 2. Open file, read, write
```Python
Open: f = open(“hello.text”, flag), flag: 'r' = read, 'b' = binary, 'w' = write
read sing line:
f.readline() 
read a list of lines:
f.readlines()
read whole file as string:
f.read()
```
### 3.  Read from stdin
```Python
import sys
for line in sys.stdin.readlines():
	#convert each line from a string to a list of integer
	line_list = (map(int, line.split()))
```
### 4.  look up table of element, origin index -> the sorted index
```Python
idx = np.argsort()
lut = np.zeros_like(idx)  
lut[idx] = np.arange(len(origin_list))

lut[origin_index] = sorted_index
```

### 5. load object and save object
```Python
def save_obj(obj, name ):
    with open('obj/'+ name + '.pkl', 'wb') as f:
        pickle.dump(obj, f, pickle.HIGHEST_PROTOCOL)

def load_obj(name ):
    with open('obj/' + name + '.pkl', 'rb') as f:
        return pickle.load(f)
```

### 6.   xrange and range
```Python
difference between list[0,1,2,3,4] and range(0,5) in python 3.0+
difference between range(0,5) and xrange(0,5) in python before 3.0)

the former one needs to allocate the actuall space on memory, the later one doesn't have to.
The later ones returns a range object( a iterable object similar to iteratorbut allows random access), so allocate memory on demand.
```

### 7. install different python version packages using pip
```
python 2.x:
pip2 install -r requirements.txt
python 3.x:
pip3 install -r requirements.txt
```


<!--stackedit_data:
eyJoaXN0b3J5IjpbLTY3NTYxODM5NSwtOTM3NjI0Nzk3LDEwNj
U5ODA0NTQsMTYyNTU0MDIwMiwxMTkzNTE5MzgwXX0=
-->
