# Object Oriented Programming

## Object Oriented Programming

- Object-Oriented Programming is a methodology or programming paradigm to design a program using classes and objects.
- It deals with Real-World Entity. (Object)
- Four Important Principles of OOP's are - Encapsulation, Abstraction, Inheritance, Polymorphism.

## Class

- Class is a user-defined data type which is having its own data members and member functions, which can be accessed and used by creating an instance of that class.
- A class is like a blueprint for an object.
- The class does not occupy any memory space till the time an object is instantiated.
- Ex - Creating a class of human, humans are having eyes, nose and their name. These are properties and having functions such as sleep, walk, talk.
<!-- - Data members are the data variables and member functions are the functions used to manipulate these variables and together these data members and member functions define the properties and behaviour of the objects in a Class. -->

_C++ Syntax (for class):_

```cpp
class Employee {
    int x;  // members are by default private
public:
    string Name; // data member
    string Company;
    int Age;
    void Introduce() { // member function
        cout << "Name:" << Name << endl;
        cout << "Company:" << Company << endl;
        cout << "Age" << Age << endl;
    }
};
```

- There are some OOPS principle that need to be satisfied while creating a class. This principle is called as SOLID where each letter has some specification. I won't be going into this points deeper. A single line of each explanation may clear you with some points.

1. SRP (The Single Responsibility Principle) - A class should have one, and only one responsibility.
2. OCP (The Open Closed Principle) - You should be able to extend a classes behavior, without modifying it.
3. LSP (The Liskov Substitution Principle) - Derived classes must be substitutable for their base classes. If S is a subtype of T, then objects of type T in a program may be replaced with objects of type S without altering any of the desirable properties of that program.
4. ISP (The Interface Segregation Principle) - Make fine chopped interface instead of huge interface as client cannot be forced to implement an interface which they don't use.
5. DIP (The Dependency Inversion Principle) - High-level modules should not depend on low-level modules. Both should depend on abstractions (e.g. interfaces). Abstractions should not depend on details. Details (concrete implementations) should depend on abstractions.

[Solid Principles](https://platis.solutions/blog/2020/06/22/how-to-write-solid-cpp/)

## Object

- Object is a run-time entity having attributes and behavior. It is an instance of the class. An object can represent a person, place or any other item. An object can operate on both data members and member functions.
- These objects are provided memory when instantiated, that means memory is provided dynamically & hence called Run Time Entities. Easy way to understand this concept is - Objects don't occupy memory at the time writing the source code.

_C++ Syntax (for object):_

```cpp
Employee employee = new Employee();
```

- Note : When an object is created using a new keyword, then space is allocated for the variable in a heap, and the starting address is stored in the stack memory. When an object is created without a new keyword, then space is not allocated in the heap memory, and the object contains the null value in the stack.

## Encapsulation

- Encapsulation is the process of combining data and functions into a single unit called class.
- Encapsulation has been done with the purpose of preventing anything outside of our class to be able to directly access our data and to interact with it and to modify it.
- In Encapsulation, the data is not accessed directly; it is accessed through the functions present inside the class.
- In simpler words, attributes of the class are kept private and public getter and setter methods are provided to manipulate these attributes. Thus, encapsulation makes the concept of data hiding possible.
- (Data hiding: a language feature to restrict access to members of an object, reducing the negative effect due to dependencies. e.g. "protected", "private" feature in C++).
- Ex -

```cpp
class Student {
    int marks;
    public:
    void setMarks(int mark){
        marks = mark;
    }
    int getMarks(){
        return marks;
    }
};

int main(){
    Student s1;
    s1.setMarks(50);
    cout << getMarks() << endl;
}
```

## Abstraction

- Abstraction means displaying only essential information and hiding the unnecessary details. Data abstraction refers to providing only essential information about the data to the outside world, hiding the background details or implementation.

- Types

1. Abstraction using Classes: We can implement Abstraction in C++ using classes. The class helps us to group data members and member functions using available access specifiers. A Class can decide which data member will be visible to the outside world and which is not.
2. Abstraction in Header files: One more type of abstraction in C++ can be header files. For example, consider the pow() method present in math.h header file. Whenever we need to calculate the power of a number, we simply call the function pow() present in the math.h header file and pass the numbers as arguments without knowing the underlying algorithm according to which the function is actually calculating the power of numbers.

- Examples -
- Withdrawl of money from ATM Machine but did not know the internal working.
- In Cars, we can brake, accelerate but we dont know internal working of it.

- Ex -

```cpp
class abstractStudent {
    virtual void scholarship() = 0;
};

class Student : abstractStudent{
    public:
    string name;
    int id;

    void scholarship() {
        if(marks>70) cout<<"You are eligible for Scholarship" << endl;
        else cout<<"You are not eligible for Scholarship" << endl;
    }
};

int main(){
    Student s;
    s.name = 'Nikk';
    s.marks = 80;
    s.scholarship();
    return 0;
}
```

## Access Specifiers IMP

- The access specifiers are used to define how functions and variables can be accessed outside the class. There are three types of access specifiers:

1. **Private:** Functions and variables declared as private can be accessed only within the same class, and they cannot be accessed outside the class they are declared.
2. **Public:** Functions and variables declared under public can be accessed throughout the program.
3. **Protected:** Functions and variables declared as protected cannot be accessed outside the class except a child class. This specifier is generally used in inheritance.

<!-- ### Data binding

- Data binding is a process of binding the application UI and business logic. Any change made in the business logic will reflect directly to the application UI. -->

## Constructor

- Constructor is a special method which is invoked automatically at the time of object creation. Generally It is used to initialize the data members of new objects. The constructor in C++ has the same name as class or structure and does not have any return type.

- There can be two types of constructors in C++.

1. Default constructor : A constructor which has no parameters is known as default constructor. It is invoked at the time of creating an object.
2. Parameterized constructor : Constructor which has parameters is called a parameterized constructor. It is used to provide different values to distinct data members.
3. Copy Constructor : A Copy constructor is an overloaded constructor used to declare and initialize an object from another object. It is of two types - default copy constructor and user defined copy constructor.

_C++ Sample Code :_

```cpp
class go {
   public:
    int x;
    go() {  // default constructor.
        x = 5;
    }
    go(int a) {  // parameterized constructor.
        x = a;
    }
    go(go &i) {  // copy constructor
        x = i.x;
    }
};

int main() {
    go a1;      // Calling the default constructor.
    go a2(20);  // Calling the parameterized constructor.
    go a3(a2);  // Calling the copy constructor.
    cout << a1.x << " ";
    cout << a2.x << " ";
    cout << a3.x << " ";
    return 0;
}
// Output : 5 20 20
```

## Inheritance

- The capability of a class to inherit properties and characteristics from another class is called Inheritance. In such a way, you can reuse, extend or modify the attributes and behaviors which are defined in other classes.

- In C++, The class that inherits properties from another class is called Sub class or Derived Class. The class whose properties are inherited by sub class is called Base Class or Super class. The derived class is the specialized class for the base class.

_C++ Syntax :_

```cpp
class derived_class : visibility-mode base_class;
```

- visibility-modes = {private, protected, public}

## Types of Inheritance :

1. Single inheritance : In single inheritance, a class is allowed to inherit from only one class. i.e. one sub class is inherited by one base class only.
2. Multiple inheritance : In Multiple Inheritance, a class can inherit from more than one classes. i.e one sub class is inherited from more than one base classes.
3. Multilevel inheritance : In Multilevel inheritance, a class is derived from another derived class.
4. Hierarchical inheritance : In Hierarchical inheritance, More than one sub class is inherited from a single base class. i.e. more than one derived class is created from a single base class.
5. Hybrid inheritance : Hybrid inheritance is a combination of simple, multiple inheritance and hierarchical inheritance.

## Polymorphism

- Polymorphism is an object-oriented programming concept that refers to the ability of a variable, function or object (Entity) to have multiple forms.

- Ex1:
- We can have an operator “+” that is the binary addition operator which behaves differently when the operands change. For Example, when both the operands are numeric, it performs addition.
- On the other hand, when the operands are string, it acts as concatenation operator. Thus polymorphism, in a nutshell, means an entity taking up many forms or behaving differently under different conditions.

## Types of Polymorphism _IMP_

1. Compile Time Polymorphism (Static)
2. Runtime Polymorphism (Dynamic)

Let’s understand them one by one :

## Compile Time Polymorphism

- The polymorphism which is implemented at the compile time is known as compile-time polymorphism. Function is invoked at compilation time. Example - Function Overloading, Operator Overloading

### Function Overloading

- Function overloading is a technique which allows you to have more than one function with the same function name but with different parameters. Function overloading can be possible on the following basis:

1. The return type of the overloaded function.
2. The type of the parameters passed to the function.
3. The number of parameters passed to the function.

_Example :_

```cpp
class Add {
public:
    int add(int a,int b){
        return (a + b);
    }
    int add(int a,int b,int c){
        return (a + b + c);
    }
};

int main() {
    Add obj;
    int res1,res2;
    res1 = obj.add(2,3);
    res2 = obj.add(2,3,4);
    cout << res1 << " " << res2 << endl;
    return 0;
}
/*
Output : 5 9
add() is an overloaded function with a different number of parameters. */
```

### Operator Overloading

- Specify extra tasks to operators without converting its real meaning.

## Runtime Polymorphism

- Runtime polymorphism is also known as dynamic polymorphism. Function is invoked at execution time. ex - Function overriding is an example of runtime polymorphism.

### Function Overriding

- In object-oriented programming when we allow a subclass or child class to provide a specific implementation of a method that is already provided by one of its superclasses or parent classes is known as Function Overriding.

_C++ Sample Code :_

```cpp
// C++ program to demonstrate function overriding
#include <bits/stdc++.h>
using namespace std;

class Base {
   public:
    virtual void intro(){
        cout<<"Base class intro" << endl;
    }
    void print() { cout << "Base Function" << endl; }
};

class Derived : public Base {
   public:
    void print() {
        cout << "Derived Function" << endl;

        // call overridden function
        // Base::print();
    }

    void intro(){
        cout<< "Derived class Intro" << endl;
    }
};

int main() {
    Derived derived1;
    Base base1;
    derived1.print();

    base1.print();  //  Base function using base object

    derived1.Base::print();  // access print() function of the Base class

    // pointer of Base type that points to derived1
    Base* ptr = &derived1;
    // call function of Base class using ptr
    ptr->print();


    Base *b1;
    Derived d1;

    b1 = &d1;

    b1->intro();        // derived intro
    b1->print();        // base print

    return 0;
}
```

## Destructor

- Destructors are usually used to deallocate memory and do other cleanup for a class object and its class members when the object is destroyed. A destructor is called for a class object when that object passes out of scope or is explicitly deleted. A destructor is a member function with the same name as its class prefixed by a ~(tilde).

_Example :_

```cpp
class A {
public:
// constructor and destructor are called automatically, once the object is instantiated
    A() {
        cout << "Constructor in use" << endl;
    }

    ~A() {
        cout << "Destructor in use" << endl;
    }
};

int main(){
    A a;
    A b;
    return 0;
}
/*
Output:
Constructor in use
Constructor in use
Destructor in use
Destructor in use
*/
```

## "this" Pointer

- this is a keyword that refers to the current instance of the class. There can be 3 main uses of 'this' keyword:

1. It can be used to pass the current object as a parameter to another method
2. It can be used to refer to the current class instance variable.
3. It can be used to declare indexers.

_C++ Syntax :_

```cpp
struct node{
    int data;
    node *next;
    node(int x){
        this->data = x;
        this->next = NULL;
    }
}
```

## Friend Function

- Friend function acts as a friend of the class. It can access the private and protected members of the class. The friend function is not a member of the class, but it must be listed in the class definition. The non-member function cannot access the private data of the class. Sometimes, it is necessary for the non-member function to access the data. The friend function is a non-member function and has the ability to access the private data of the class.

### Note :

1. A friend function cannot access the private members directly, it has to use an object name and dot operator with each member name.
2. Friend function uses objects as arguments.

_Example IMP :_

```cpp
class A {
    int a = 2;
    int b = 4;
public:
    // friend function
    friend int mul(A k){
        return (k.a * k.b);
    }
};

int main() {
    A obj;
    int res = mul(obj);
    cout << res << endl;
    return 0;
}
// Output : 8
```

## Aggregation

- It is a process in which one class defines another class as any entity reference. It is another way to reuse the class. It is a form of association that represents the HAS-A relationship.

## Virtual Function IMP

- A virtual function is used to replace the implementation provided by the base class. The replacement is always called whenever the object in question is actually of the derived class, even if the object is accessed by a base pointer rather than a derived pointer.

1. A virtual function is a member function which is declared within a base class and is re-defined(Overriden) by a derived class.
2. When we use the same function name in both base and derived class, the function in base class is declared with a keyword virtual.
3. When the function is made virtual, then C++ determines at run-time which function is to be called based on the type of the object pointed by the base class pointer. Thus, by making the base class pointer to point to different objects, we can execute different versions of the virtual functions.

### Key Points :

1. Virtual functions cannot be static.
2. A class may have a virtual destructor but it cannot have a virtual constructor.

_C++ Example :_

```cpp
#include <bits/stdc++.h>
using namespace std;

class base {
public:
    // virtual function (re-defined in the derived class)
    virtual void print() {
        cout << "print base class" << endl;
    }

    void show() {
        cout << "show base class" << endl;
    }
};

class derived : public base {
public:
    void print() {
        cout << "print derived class" << endl;
    }

    void show() {
        cout << "show derived class" << endl;
    }
};

int main() {
    base* bptr;
    derived d;
    bptr = &d;
    // virtual function, binded at runtime
    bptr->print();
    // Non-virtual function, binded at compile time
    bptr->show();
}
/*
output :
print derived class // (impact of virtual function)
show base class
*/
```

## Pure Virtual Function :

1. A pure virtual function is not used for performing any task. It only serves as a placeholder.
2. A pure virtual function is a function declared in the base class that has no definition relative to the base class.
3. A class containing the pure virtual function cannot be used to declare the objects of its own, such classes are known as abstract base classes.
4. The main objective of the base class is to provide the traits to the derived classes and to create the base pointer used for achieving the runtime polymorphism.

_C++ Syntax :_

```cpp
virtual void display() = 0;
```

_C++ Example :_

```cpp
#include<bits/stdc++.h>
using namespace std;

class Base{
public:
   virtual void show() = 0;
};

class Derived : public Base {
public:
    void show() {
        cout << "You can see me !" << endl;
    }
};

int main(){
    Base *bptr;
    Derived d;
    bptr = &d;
    bptr->show();
    return 0;
}
// output : You can see me !
```

## Abstract Classes

- In C++ class is made abstract by declaring at least one of its functions as a pure virtual function. A pure virtual function is specified by placing "= 0" in its declaration. Its implementation must be provided by derived classes.

_Example :_

```cpp
#include<bits/stdc++.h>
using namespace std;
// abstract class
class Shape{
public:
    virtual void draw()=0;
};

class Rectangle : Shape{
public:
    void draw(){
        cout << "Rectangle" << endl;
    }
};

class Square : Shape{
public:
    void draw(){
        cout << "Square" << endl;
    }
};

int main(){
    Rectangle rec;
    Square sq;
    rec.draw();
    sq.draw();
    return 0;
}
/*
Output : Rectangle Square
*/
```

## Namespaces in C++ :

1. The namespace is a logical division of the code which is designed to stop the naming conflict.
2. The namespace defines the scope where the identifiers such as variables, class, functions are declared.
3. The main purpose of using namespace in C++ is to remove the ambiguity. Ambiguity occurs when a different task occurs with the same name.
4. For example: if there are two functions with the same name such as add(). In order to prevent this ambiguity, the namespace is used. Functions are declared in different namespaces.
5. C++ consists of a standard namespace, i.e., std which contains inbuilt classes and functions. So, by using the statement "using namespace std;" includes the namespace "std" in our program.

_C++ Example :_

```cpp
#include <bits/stdc++.h>
using namespace std;
// user-defined namespace
namespace Add {
    int a = 5, b = 5;
    int add() {
        return (a + b);
    }
}

int main() {
    int res = Add :: add(); // accessing the function inside namespace
    cout << res;
}
// output : 10
```

## Key Notes

- **Delete** is used to release a unit of memory, delete[] is used to release an array.
- **Virtual inheritance** facilitates you to create only one copy of each object even if the object appears more than one in the hierarchy.
- **Operator overloading:** Operator overloading is defined as the standard operator can be redefined so that it has a different meaning when applied to the instances of a class.

<!-- ## You can skip this section ( C )

- The name malloc and calloc() are library functions that allocate memory dynamically. It means that memory is allocated during runtime(execution of the program) from the heap segment.
- The "malloc" or "memory allocation" method in C is used to dynamically allocate a single large block of memory with the specified size. It returns a pointer of type void which can be cast into a pointer of any form. It doesn’t Iniatialize memory at execution time so that it has initializes each block with the default garbage value initially.
- "calloc" or "contiguous allocation" method in C is used to dynamically allocate the specified number of blocks of memory of the specified type. it is very much similar to malloc() but has two different points and these are:

1. It initializes each block with a default value "0".
2. It has two parameters or arguments as compare to malloc().

- "realloc" or "re-allocation" method in C is used to dynamically change the memory allocation of a previously allocated memory.
- "free" method in C is used to dynamically de-allocate the memory. The memory allocated using functions malloc() and calloc() is not de-allocated on their own. Hence the free() method is used, whenever the dynamic memory allocation takes place. It helps to reduce wastage of memory by freeing it.
- -->
