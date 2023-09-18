## **OBJECT ORIENTED PROGRAMMING IN C++**

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