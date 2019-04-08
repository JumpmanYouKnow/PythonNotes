Generic Python
---------------------

#### 1. Open file, read, write
```Python
Open: f = open(“hello.text”, flag), flag: 'r' = read, 'b' = binary, 'w' = write
read sing line:
f.readline() 
read a list of lines:
f.readlines()
read whole file as string:
f.read()
```
#### 2.  Read from stdin
```Python
import sys
for line in sys.stdin.readlines():
	#convert each line from a string to a list of integer
	line_list = (map(int, line.split()))
```
#### 2.  look up table of element, origin index -> the sorted index
```Python
idx = np.argsort()
lut = np.zeros_like(idx)  
lut[idx] = np.arange(len(origin_list))

lut[origin_index] = sorted_index
```

#### 3. load object and save object
```Python
def save_obj(obj, name ):
    with open('obj/'+ name + '.pkl', 'wb') as f:
        pickle.dump(obj, f, pickle.HIGHEST_PROTOCOL)

def load_obj(name ):
    with open('obj/' + name + '.pkl', 'rb') as f:
        return pickle.load(f)
```

#### 4.  
```Python
difference between list[0,1,2,3,4] and range(0,5) in python 3.0+
ie: difference between range(0,5) and xrange(0,5) in python before 3.0

the former one needs to allocate the actuall space on memory, the later one doesn't have to.
The later ones returns a object similar to iterator, (but allows random access), so allocate memory on demand.


<!--stackedit_data:
eyJoaXN0b3J5IjpbMTYyNTU0MDIwMiwxMTkzNTE5MzgwXX0=
-->