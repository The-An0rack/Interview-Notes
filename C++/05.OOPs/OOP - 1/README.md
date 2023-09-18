## **OBJECT ORIENTED PROGRAMMING IN C++ (Part 1)**

As the size of the program increases, readability, maintainability and bug-free nature of programs decreases. Also, there is a need for data security (_not every component must be able to access all data). Hence,_ Object Oriented Programming came into the picture.

OOP uses classes to solve this problem by modelling programs like a real world scenario.

<table><tbody><tr><td><strong>Procedure Oriented Programming</strong></td><td><strong>Object Oriented Programming</strong></td></tr><tr><td>Consists of writing a set of instructions for the computer to follow.</td><td>Works on the concept of classes and objects</td></tr><tr><td>The main focus is on functions and not on the flow of data.</td><td>Decomposes the problem in objects and builds data&nbsp;<br>and functions around the objects.</td></tr><tr><td>Functions can either use local or global data.</td><td>Objects use data as per the scope and access.</td></tr><tr><td>Data moves openly from function to function.</td><td>Treats data as a critical element</td></tr></tbody></table>

### Some key terms:

**Classes:** Basic templates for creating objects. Blueprint of objects. Binds attributes and methods together.

**Objects:** Basic run time entities. Instance of a class.

### Pillars of OOPs

1.  **Encapsulation:** Wrapping of data and methods into a single unit known as a class.
2.  **Abstraction:** It is hiding complex details and showing only aspects meaningful to the outside world. 
3.  **Inheritance:** Properties(attributes and methods) of one class can be inherited by other classes.
4.  **Polymorphism:** Ability to take more than one form. eg. function overloading.

**Data Binding:** Code which will be executed is not known until the program runs.

**Message Binding:** Passing of data into the method of an object. An object oriented program consists of a set of objects that communicate with each other. Objects communicate with each other by sending and receiving information.

<table><tbody><tr><td><strong>Structure&nbsp;</strong></td><td><strong>Class</strong></td></tr><tr><td>It does not have data hiding.</td><td>It has data hiding.</td></tr><tr><td>It can not contain functions.</td><td>It can contain functions.</td></tr></tbody></table>

### Benefits of OOPs

1.  Better **code reusability** using objects and inheritance.
2.  The principle of data hiding **helps build secure** systems.
3.  Multiple objects can coexist without interference.
4.  OOP makes it **easy to maintain and modify** existing code as new objects can be created with small differences to existing ones.

### Access Specifiers 

**Access specifiers** or **access modifiers** are the labels that specify the type of access given to members of a class. These are used for data hiding. These are also called **visibility modes**. There are three types of access specifiers:

1.  private 
2.  public 
3.  protected 


1.  **Private:** If the data members are declared as private access, then they cannot be accessed from other functions outside the class. It can only be accessed by the functions declared within the class.
2.  **Public:** If the data members are declared public access then they can be accessed from other functions out side the class.
3.  **Protected:** The access level of protected declaration lies between public and private. This access specifier is used at the time of inheritance.

_If no access specifier is specified then it is treated by default as private_

---

**Code:**

```cpp
#include <iostream>
using namespace std;
class Employee
{
   public:
       int a;
       void hello() 
       {
           cout << "Hello World!!!";
       }
       
};
int main() {
   
   Employee e;
   e.hello();
   cout << e.a;
   return 0;
}
```

**Output:** 

```plaintext
Hello World!!!0
```

#### Writing functions outside the class body

```cpp
class Employee
{
   public:
       int a;
       void hello();
};
void Employee :: hello()
{
   cout << "Hello World!!!";
}
```

### Nesting of member functions

```cpp
#include <iostream>
using namespace std;
class Binary {
   private: 
       string s;
       void chk_bin(void);
   public:
       void read(void);
       
};
void Binary :: read(){
   cout << "Enter a binary number: ";
   cin >> s;
   chk_bin();
}
void Binary :: chk_bin() {
   for(int i = 0; i < s.length(); i++) {
       if(s.at(i) != '0' && s.at(i) != '1') {
           cout << "Not a valid binary number.";
           exit(0);
       }
   }
   cout << "It is a valid binary string";
}
```

### **Memory Allocation for Objects**

Memory for objects is allocated when they are declared but not when a class is defined. 

All objects in a given class use the same member functions. The member functions are created and placed in memory only once when they are defined in the class definition.

### **Static Members of a Class**

A class can have 2 types of static members:

1.  Static data members
2.  Static member functions

1.  **Static Data Members:** Only one copy of a data member is created for the entire class and is shared by all the objects of that class, no matter how many objects are created. It has the following properties:
    1.  It is initialized to zero when the first object of its class is created. No other initialization is permitted.
    2.  It is visible only within the class, but its lifetime is the entire program.
    3.  Static data member is defined by a keyword `static`.
    4.  To initialize a static data member with a custom value, outside the class we set it to the custom value.
2.  **Static Member Functions: .**A member function that is declared static has the following properties: 
    1.  A static function can have access to **only** other static members (functions or variables) declared in the same class.
    2.  A static member function is to be called using the class name (instead of its objects) as follows: `class-name :: function-name;`

 Example:

```cpp
#include <iostream>

using namespace std;

class emp {
   public:
       static int count;
       int d;
       static void inc_count(void);
};
int emp::count; // If we set a value here, the static member will be initialised to that value. And writing this is IMP!!!
void emp :: inc_count()  
{
   count++;
}

int main() {
   emp e;
   emp::inc_count();
   cout << e.count;
   
   return 0;
}
```

### **Array of Objects**

```cpp
#include <iostream>
using namespace std;
class Person{
   private:
       string name;
   public:
       void set_name(string s);
       string get_name(void);
};
void Person::set_name(string s) {
   name = s;
}
string Person :: get_name() {
   return name;
}

int main() {
   Person p[3];
   p[0].set_name("Ram");
   p[1].set_name("Shyam");
   p[2].set_name("Babu Rao");
   cout << p[0].get_name() << endl;
   cout << p[1].get_name() << endl;
   cout << p[2].get_name() << endl;
   return 0;
}
```

**Output:**

```plaintext
Ram
Shyam
Babu Rao
```

### Passing Objects as arguments

```cpp
#include <iostream>
using namespace std;
class complex_num {
   private:
       int a;
       int b;
   public:
       void display() {
           cout << a << " + i" << b;
       }
       void set_num(int r, int i) {
           a = r;
           b = i;
       }
       void add(complex_num num1, complex_num num2) {
           a = num1.a + num2.a;
           b = num1.b + num2.b;
           
       }
};
int main() {
   
   complex_num num1;
   complex_num num2;
   complex_num result;
   
   num1.set_num(1, 2);
   num2.set_num(3, 4);
   result.add(num1, num2);
   
   cout << "Num 1: "; num1.display(); cout << endl;
   cout << "Num 2: "; num2.display(); cout << endl;
   cout << "Num 1 + Num2: "; result.display();
   
   return 0;
}
```

**Output:**

```plaintext
Num 1: 1 + i2
Num 2: 3 + i4
Num 1 + Num2: 4 + i6
```

### Friend Functions in C++

A friend function is a function which is declared within a class and is defined outside the class. It does not require any scope resolution operator for defining . It can access private members of a class. It is declared by using the keyword `friend`.

```cpp
#include <iostream>
using namespace std;
class X 
{
   private:
       int data = 10;
       friend void display(X obj);        
};
void display(X obj) {
   cout << "Value of data: " << obj.data;
}
int main() {
   X e;
   display(e);
   return 0;
}
```

**Output:**

```plaintext
Value of data: 10
```

A friend function possesses certain special characteristics:  

*   It is not in the scope of the class to which it has been declared as friend. 
*    Since it is not in the scope of the class, it cannot be called using the object of that class. It can be invoked like a normal function without the help of any object. 
*   Unlike member functions, it cannot access the member names directly and has to use an object name and dot membership operator with each member name.
*   It can be declared either in the public or private part of a class without affecting its meaning.  
*   Usually, it has the objects as arguments.

### Friend Classes in C++

A class can also be declared to be the friend of some other class. When we create a friend class then all the member functions of the friend class also become the friend of the other class. This requires the condition that the friend becoming class must be first declared or defined **(forward declaration)**.

```cpp
#include <iostream>
using namespace std;
class sample2;
class sample1{
   private:
       int data1;
       friend class sample2;
   public:
       void get_data_1() {
           cout << "Enter value of data1: ";
           cin >> data1;
       }
       void display1()
       {
           cout << "data1: " << data1 << endl;
       }
};
class sample2 
{
   private:
       int data2;
       sample1 obj1;
   public:
       void get_data_2()
       {
           obj1.get_data_1();
           cout << "Enter value of data2: ";
           cin >> data2;
       }
       int sum()
       {
           return obj1.data1 + data2;
       }
       void display2() 
       {
           cout << "data1: " << obj1.data1 << endl;
           cout << "data2: " << data2 << endl;
           cout << "sum: " << sum();
       }
};
int main() {
   sample2 o2;
   o2.get_data_2();
   o2.display2();
   return 0;
}
```

**Output:**

```plaintext
Enter value of data1: 10
Enter value of data2: 20
data1: 10
data2: 20
sum: 30
```

We can also declare a specific method of a class as a friend of given class as: `friend void sample2 :: display();`


---

### Constructors in C++

Constructor is a special member function, with the same name as that of the class and is used to initialize the objects of its class.

It is automatically invoked whenever an object is created.

#### CHARACTERISTICS OF CONSTRUCTOR 

*   They should be declared in the public section. 
*   They are invoked automatically when the objects are created. 
*   They do not have a return type, not even void. 
*   They cannot be inherited, though a derived class can call the base class constructor. 
*   Like other C++ functions, they can have default arguments. 
*   Constructors cannot be virtual.  
*   We cannot refer to their addresses. 
*   They make _implicit calls_ to the operators _new_ and _delete_ when memory allocation is required.

#### Constructors are of 3 types: 

1\. Default Constructor 

2\. Parameterized Constructor 

3\. Copy Constructor

#### 1\. Default Constructor

A constructor that accepts no parameters is called the default constructor.

```cpp
#include <iostream>
using namespace std;
class X 
{
   private:
       int data;
   public:
       X()
       {
           data = 10;
       }
       void display()
       {
           cout << "Data: " << data;
       }
};
int main() {
   X e;
   e.display();
   return 0;
}
```

**Output:**

```plaintext
Data: 10
```

#### 2\. Parametrised Constructor

The constructors that take parameters are called parameterized constructors.

```plaintext
#include <iostream>
using namespace std;
class X 
{
   private:
       int data;
   public:
       X(int val)
       {
           data = val;
       }
       void display()
       {
           cout << "Data: " << data;
       }
};
int main() {
   int temp;
   cout << "Enter value of data: ";
   cin >> temp;
   X e(temp);
   e.display();
   
   return 0;
}
```

**Output:**

```plaintext
Enter value of data: 12
Data: 12
```

We must pass the initial values as arguments to the constructor function when an object is declared. This can be done in 2 ways:

1.  **Explicit Call:** `item t=item(10,20);`
2.  **Implicit Call:** `item t(10,20);`

#### 3\. Copy Constructor

A copy constructor is used to declare and initialize an object from another object.

Copy constructor is called in both cases: `item t2(t1);` or `item t2=t1;`

The process of initializing through a copy constructor is known as **copy initialization.**

`t2=t1` will not invoke copy constructor. t1 and t2 are objects, assigns the values of t1 to t2. 

A copy constructor takes a reference to an object of the same class as itself as an argument.

When no copy constructor is found, then the compiler supplies it with a copy constructor.

**Code:**

```cpp
#include <iostream>
using namespace std;
class X 
{
   private:
       int data;
   public:
       X(int val)
       {
           data = val;
       }
       X(X &obj)
       {
           data = obj.data;
       }
       void display()
       {
           cout << "Data: " << data << endl;
       }
};
int main() {
   int temp;
   X e(10);
   e.display();
   X e2(e);
   e2.display();
   
   return 0;
}
```

**Output:**

```cpp
Data: 10
Data: 10
```

Constructors can also be overloaded in C++, i.e. a class can have multiple constructors with different arguments.

We can also have default arguments in constructors.

### Destructors in C++

A destructor is used to destroy the objects that have been created by a constructor. Like a constructor, the destructor is a member function whose name is the same as the class name but is preceded by a tilde. Eg: `~item() { }` 

A destructor _never takes any argument nor does it return any value._

It will be invoked implicitly by the compiler upon exit from the program to clean up storage that is no longer accessible. 

It is good practice to declare destructors in a program since it releases memory space for future use.

```cpp
#include <iostream>
using namespace std;
class X 
{
   private:
       int data;
   public:
       X(int val)
       {
           data = val;
       }
       ~X()
       {
           cout << "Destructor";
       }
};
int main() {
   X e(10);
   return 0;
}
```