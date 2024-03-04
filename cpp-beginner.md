# C++ - Beginner

## Week 1A - The Programming Experience

### Section 3 - Hello World

```cpp
// the hello world program
#include <iostream>

using namespace std;

int main()
{
    cout << "hello world\n";
    return 0;
}
```

### Section 5 - Alternate Form

```cpp
// add this line to avoid flash
cout << flush; getchar();
```

## Week 2A - Simple C++ Programs

### Section 7 - Numeric Expressions and Operators

```cpp
// endl flushes the output stream while '\n' does not
cout << "hello world" << endl;
```

## Week 2B - Data Types

### Section 1 - Numeric Types

```cpp
// if you know you will never use negative values
unsigned short int si;
unsigned long int li;
```

## Week 3A - User Input

### Section 3 - String Concatenation

```cpp
// you cannot directly concatenate two string literals
#include <string>

string s;
s = "hello" + "world"; // error
s = string("hello") + string("world");
```

### Section 4 - User Input of Strings

```cpp
// getline() acquires all the characters the user typed, including spaces
string s;
getline(cin, s);
```

### Section 5 - cin With Strings and Numbers

```cpp
// cin can be used to read numeric string directly into numeric variable
int i;
cin >> i;

// cin only reads one non-blank string at a time (separated by spaces)
string s1, s2, s3;
cin >> s1 >> s2 >> s3;

cin >> "string"; // error
cin << i; // error
cout >> i; // error
```

### Section 6 - String Conversions

```cpp
#include <sstream>

string s = "3.14";
double d;
istringstream(s) >> d; // convert string to double

ostringstream oss;
oss << d;
s = oss.str(); // convert double to string

// clearing stream for reuse
oss.str("");
oss.clear();

s = "string";
s[3] = 'c'; // change char in string
char c = s[3]; // convert string to char
```

### Section 7 - Formatting Numbers

```cpp
// number format
cout.setf(ios::fixed); // hex, dec, scientific
cout.precision(3); // number of digits
```

## Week 3B - Selection

### Section 2 - The IF/ELSE Statement

```cpp
// testing for non-numeric input
string s;
getline(cin, s);
int i;
if (istringstream(s) >> i) // true if the string starts with a number
```

### Section 3 - Switch and Case

```cpp
// the switch statement can only switch on numeric variables
```

### Section 4 - Relational Expressions

```cpp
// bool stands for boolean
bool b = true;

if (3) // non-zero is considered true
```

### Section 6 - A Sample Program Analysis

```cpp
// const means constant
const double PIE = 3.14;
```

## Week 4A - Repetition

### Section 6 - A Nice Example

```cpp
// length of string
string s = "string";
int i = s.length();

// character test functions
char c = 'c';
bool b;
b = c.isalpha(); // is a letter
b = c.isdigit(); // is a number
b = c.isalnum(); // is a letter or a number
b = c.islower();
b = c.isupper();
b = c.toupper();
b = c.tolower();
```

## Week 4B - Sneak Peek at Week 8A - Arrays and a Sort Algorithm

### Section 1 - Declaring Arrays

```cpp
// array
int array[3];
```

### Section 2 - An Array Example

```cpp
// macro constant
#define PIE 3.14 // no semicolon: not a statement but a compiler directive

// size of array
int i = sizeof(intArray) / sizeof(intArray[0]); // number of bytes
```

### Section 3 - Arrays, Methods and Sorting

```cpp
// &: reference
```

### Section 4 - Sorting String Arrays

```cpp
// sorting strings
string s1 = "hello";
string s2 = "world";
int i = s1.compare(s2); // ==: 0, <: negative number, >: positive number
```

### Section 5 - Remarks on Arrays

```cpp
// not a string but a char array
char array[12] = "hello world"; // 12th char: '\0'
```

## Week 5A - Methods

### Section 3 - Defining Methods

```cpp
// method prototype (declaration)
void method();

// method definition (can appear in any order inside the source file)
void method()
{
    // method body
}
```

### Section 4 - The Mortgage Calculator

```cpp
// math functions
#include <cmath> // pow(), sqrt(), abs(), sin(), cos()
```

## Week 5B - Parameters Passing and Global Variables

### Section 4 - Formal Parameters and Overloading

```cpp
// the value of the argument is copied down into the formal parameter
// the parameter is local and is only a copy of the object
// if we don't want to use global variables, we have two choices
// C: pointers, C++: reference and reference parameters
```

## Week 6A - Object-Oriented Programming (OOP)

### Section 2 - Classes You Define

```cpp
// if there is no keyword, the data is assumed to be private (default)
```

## Week 6B - Instance Methods

### Section 1 - Methods Defined in Classes

```cpp
// class prototype
class Person
{
private:
    string name;

public:
    Person();

    bool set_name(string s);
    string get_name();
};

// class definition
Person::Person()
{
    name = "default";
}

bool Person::set_name(string s)
{
    bool result = false;

    if (s.length() > 0)
    {
        name = s;
        result = true;
    }

    return result;
}

string Person::get_name()
{
    return name;
}
```

### Section 2 - Understanding Constructors

```cpp
// if a constructor takes only one parameter, we can use = instead of ()
Person::Person(string s)
{
    if (!set_name(s))
    {
        name = "default";
    }
}

int main()
{
    Person person1("hello"), person2 = "world";
    return 0;
}
```

### Section 4 - Instance Members and Methods

```cpp
// only use in-line method implementation for accessors (short and easy)
class Person
{
private:
    string name;

public:
    string get_name() { return name; }
};
```

### Section 5 - Essential Ingredients in All Class Designs

```cpp
// initialize most static members outside the class prototype
class Person
{
public:
    static const string DEFAULT_NAME;
};

const string Person::DEFAULT_NAME = "default";
```

## Week 7A - Deeper into Classes

### Section 1 - Static Members

```cpp
// initializing static member
class Person
{
private:
    static long population;

public:
    Person();
};

long Person::population = 0;

Person::Person()
{
    population++;
}
```

### Section 3 - This

```cpp
// the arrow notation is pervasive in C++ and is not restricted to "this"
class Person
{
private:
    string name;

public:
    bool set_name(string name);
};

bool Person::set_name(string name)
{
    bool result = false;

    if (name.length() > 0)
    {
        this->name = name;
        result = true;
    }

    return result;
}
```

## Week 7B - Interaction Between Objects and Methods

### Section 1 - Reference Parameters

```cpp
// passing an object reference rather than the object itself
class Person
{
private:
    int age;

public:
    int get_age() { return age; }
    bool set_age(int age);
};

bool Person::set_age(int age)
{
    bool result = false;

    if (age > 0)
    {
        this->age = age;
        result = true;
    }

    return result;
}

void get_older(Person& person);
void print_age(const Person& person);

void get_older(Person& person)
{
    person.set_age(person.get_age() + 1);
}

void print_age(const Person& person)
{
    cout << person.get_age() << endl;
}
```

## Week 8B - Compound Data Types: Arrays in Classes

### Section 4 - Arrays Inside Classes

```cpp
// default parameter
class Person
{
public:
    static const string DEFAULT_NAME;
    static const int DEFAULT_AGE;

    Person(string name = DEFAULT_NAME, int age = DEFAULT_AGE);
}

const string Person::DEFAULT_NAME = "default";
const int Person::DEFAULT_AGE = -1;
```

## Week 10A - Pointers and Dynamic Memory

### Section 1 - Pointers, Addresses and Memory

```cpp
// the address of an object
string s;
cout << &s << endl; // in base 16 (hexadecimal notation)
```

### Section 2 - Pointers

```cpp
// C++ makes us state explicitly what kind of address we indent to store
string s1;
string* sp = &s1;
cout << sp << endl; // "0x" is a hex value

string s2;
sp = &(s1 + s2); // error

s1 = "hello";
cout << *sp << endl; // de-referencing the pointer
```

### Section 3 - Dynamic Memory Allocation

```cpp
// wait until we need a variable before we allocate it
string* sp;
sp = new string;
*sp = "hello";
cout << *sp << endl;

delete sp; // deallocate manually
```

### Section 4 - Classes and Dynamic Allocation

```cpp
// dereferencing objects through pointers
Person* person = new Person("default", 3);
*person.set_name("hello");
person->set_name("world");
```

## Week 10B - Older C Style Strings (Char Arrays)

### Section 1 - Defining CStrings

```cpp
// '\0' tells all CString functions where the CString ends
char array[] = "hello world";
array[5] = '\0';
strcpy(array, "world");
array = "hello world"; // error
```

### Section 2 - CString Input and Output

```cpp
// the length does not include the null terminator nor is the size of the array
#include <cstring>

char array[100];
int n;

cin >> array; // input: hello world

n = strlen(array);

cout << array << ", " << n << endl; // output: hello, 5

cin.getline(array, sizeof(array) - 1, '\n'); // input: hello world
n = strlen(array);

cout << array << ", " << n << endl; // output: hello world, 11
```

### Section 3 - More CString Functions

```cpp
// array name is just the constant address of the zero'th element of the array
char array1[] = "hello", array2[5];
array2 = array1; // wrong
strcpy(arary2, array1);
strcpy(array1, "world");

strcpy(array1, "hello world"); // big trouble
strncpy(array1, "hello world", 5); // will stop copying after 5 chars (or '\0')

cout << flush; // forces the output to the screen before input is requested
fgets(); // not well synchronized with cout, flush() may be needed

// converting cstring to int or double
strcpy(array1, "3");
strcpy(array2, "3.14");
int i;
double d;
sscanf(array1, "%d", &i); // %ld for long
sscanf(array2, "%lf", &d); // for both long float and double
istringstream(array1) >> i; // this also works (preferred)

// comparing two cstrings
i = !strcmp(array1, array2); // ==: 0, <: negative number, >: positive number

// looking for substrings
strcpy(array1, "hello world");
strcpy(array2, "hello");
char* cp = strstr(array1, array2); // first occurance or null
```

### Section 4 - Comparing CStrings, S-C Strings and .NET Strings

```cpp
// three data types for handling character strings
int i;
char c;
bool b;

// the most primitive are the cstrings, built from char arrays
#include <cstring>

using namespace std;

char c1[100], c2[100] = "world"; // declaration, initialization
strcpy(c1, "hello"); // assignment

cin >> c1 >> c2; // input
cin.getline(c1); // input
cout << c1 << c2; // output

strcat(c1.c2); // concatenation (modifies c1)
i = strlen(c1); // length
i = strcmp(c1, c2); // comparison
i = strpos(c1, c2); // position of substring
// no substring
c = c1[3]; // char at position
istringstream(c1) >> i; // converting to number


// the string class
#include <string>

using namespace std;

String s1, s2("world"); // declaration, initialization
s1 = "hello"; // assignment

cin >> s1 >> s2; // input
getline(s1); // input
cout << s1 << s2; // output

s1 = s1 + s2; // concatenation
i = s1.length(); // length
i = s1.compare(s2); // comparison
b = s1 < s2; // comparison
b = s1 == s2; // comparison
b = s1 > s2; // comparison
i = s1.find(s2); // position of substring
s2 = s1.substr(0, 3); // substring
c = s1[3]; // char at position
istringstream(s1) >> i; // converting to number

// microsoft's .net string^ class, used in c# nad legacy microsoft c++ compilers
using namespace System;

String ^n1, ^n2 = "world"; // declaration, initialization
n1 = "hello"; // assignment

n1 = textbox1->text; // input
textbox1->text = n1; // output

n1 = n1 + n2; // concatenation
i = n1->Length; // length
i = n1->CompareTo(n2); // comparison
i = n1->IndexOf(n2); // position of substring
n2 = n1->Substring(0, 3); // substring
c = n1[3]; // char at position
int::TryParse(n1, i); // converting to number
```
