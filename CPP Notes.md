---
title: "CPP Notes"
date: 2018-09-08
---

---------------------
### 1. lvalue and rvalue

you can get memory address for lvalue, you can't for rvalue

### 2. lvalue reference
Reference is cpp is like pointer in c, but not exactly same.

Pass lvalue as parameter, you can just refer to its address, we know its memory address, we can access the data without deep copy, save both time and space. 


### 3. rvalue reference
Pass rvalue as parameter, you can't refer to its address(for example, when a function returns, a heap object allocated, but the variable holds the object's heap address will be poped with the stackframe). To forward the data content in rvalue, you need to deep copy it again and again.
With new feature rvalue reference introduced in c++11, you can use rvalue reference, it allows you to make shallow copy when forward the data content of a rvalues.


class Test {
    int * arr{nullptr};
public:
    Test():arr(new int[5000]{1,2,3,4}) { 
    	cout << "default constructor" << endl;
    }
    Test(const Test & t) {
        cout << "copy constructor" << endl;
        if (arr == nullptr) arr = new int[5000];
        memcpy(arr, t.arr, 5000*sizeof(int));  // a lot of data to copy!
    }
    Test(Test && t): arr(t.arr) {
        cout << "move constructor" << endl;
        t.arr = nullptr;
    }
    ~Test(){
        cout << "destructor" << endl;
        delete [] arr;
    }
};

Test createTest() {
    return Test();   // line A, call copy constructor 1st time
}

int main() {    
Scenario 1:
    Test t(createTest());   
    /* not reasonable to use copy constructor, object one line A is clearly a temporary object, what we want it move/steal its content/data to object on line B, use move copy constructor!*/
    
Scenario 2:
    Test test1; 
	  // do something to test1
	  Test test2(test1); // duplicate test1
	  // do something to test2
    /*Here you might or might not want to keep both objects, if you want to keep test1, it's reasonable to use copy constructor */
    Test test2(std::move(test1)); // move data content of test1 to test2
    /*If you don't need test1 anymore, move copy constructor, it's more efficient*/    
}

### 4. keyword friend
pros: 
1.allows more efficience program, a friend class of class A can directly access class A's private field, withou calling class A's member function frequently.
2.More flexiable If class A want to share some resource with class B, but not class C. Instead of set the resource publice, A can keep the resource private and set B as friend.

cons:
1. Bad for the Encapsulation feature. 



> Written with [StackEdit](https://stackedit.io/).
<!--stackedit_data:
eyJoaXN0b3J5IjpbNjk4MjY0NzQ3XX0=
-->