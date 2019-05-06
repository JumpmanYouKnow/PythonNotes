---
title: "Java Notes"
date: 2018-02-08
---
# JavaNotes
Java NOtes and cheat sheet I wrote during work and academia

Generic Java
---------------------

### 1. ArrayList
ArrayList is implemented based on primitive array 

Feature: 
ArrayList<T> myarrlist = new ArrayList<T>()
#### 1.Type Satety
ArrayList provides stronger type safety ensurance than array
  
https://coderanch.com/t/625190/certification/Array-ArrayList-Thread-safety-Type

#### 2. Flexibility
ArrayList has Dynamic, and a better interface

#### 3. Size vs length
Size is the capacity
length is the actually length

#### 4. Multi-dimension
arraylist doesn't support multi-dimension, array does

#### 5, primitive types
ArrayList doesn't support primitive types

### 2. Multi-threading
Primitive types gurantees thread-safety
Immutable objects are thread-safe, but mutable objects are not.
For example, String is thread-safe, Stringbuffer is not.


### 3. String pool
```java
String str1 = new string("abc") // allocate space on heap, put it in string pool, return reference from  heap
String str2 = "abc" // search in string pool to find if same string exists, by method "equals", return reference from string pool
obvisouly, str1.equals(str2) == True 
but, str1 != str2, as str1 refer to heap, str2 refer to string pool

String str3 = "abc"
str2 = str3, as both refer to string pool

str1 = str1.intern() 
// if string pool contains the object str1 is referring(on heap), refer to string pool instead of heap. ojbect on heap will go to GC 
now str2 = str1 = str3

// string concate
a + b, if both constant, consider as string literal
a + b, if either is not constant, consider as variable, use new String()
```





> Written with [StackEdit](https://stackedit.io/).
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTEwNjQzMTUwN119
-->