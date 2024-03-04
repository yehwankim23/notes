# C++ - Intermediate

## Week 1A - Enums, Strings, Default Parameters

### Section 4 - Enums

```cpp
// use an int for the loop counter, not an enum
enum Day
{
    monday, tuesday, wednesday, thursday, friday, saturday, sunday
};

for (int i = monday, i <= sunday; i++)
{
    Day day = static_cast<Day>(i); // or Day day = (Day) i;
    cout << day << endl;
}
```

## Week 1B - Review and Analysis of an OOP Project

### Section 1 - Static Member Data

```cpp
// satisfies the compiler but does nothing as far as initializing the array
string array[] = {0};
```

## Week 2A - Pointers, Addresses, Memory

### Section 6 - Array Names and Pointers

```cpp
// the array name is the address of the zeroth element
string array[3];
array == &array[0];
*array == array[0];
*(array + k) == array[k];
```

### Section 7 - Dynamic Arrays

```cpp
// use brackets with delete to free up the entire array
string* sp;
sp = new string[3];
delete[] string;
```

## Week 2B - Sorting, Recursion and Binary Search

### Section 3 - Binary Searching

```cpp
// we have to sort the array first
int Person::binary_search(Person array[], string name, int start, int end)
{
    int result = -1;

    if (start <= end)
    {
        int middle_index = (start + end) / 2;
        result = name.compare(array[middle_index].name);

        if (result < 0)
        {
            result = binary_search(array, name, start, middle_index - 1);
        }
        else if (result > 0)
        {
            result = binary_search(array, name, middle_index + 1, end);
        }
    }

    return result;
}
```

## Week 3A - Cellular Automata, Life and Binary Ops

### Section 8 - Passing Addresses (Pointers) to Methods

```cpp
// using reference parameters
void swap(string& s1, string& s2)
{
    string temp = s1;
    s1 = s2;
    s2 = temp;
}

int main()
{
    string s1 = "hello";
    string s2 = "world";

    swap(s1, s2);
}

// passing addresses
void swap(string* s1, string* s2)
{
    string temp = *s1;
    *s1 = *s2;
    *s2 = temp;
}

int main()
{
    string s1 = "hello";
    string s2 = "world";

    swap(&s1, &s2);
}
```

## Week 3B - Multi-Dimensional Arrays and Stacks

### Section 1 - Dynamic Allocation of 2-D Arrays

```cpp
// array of arrays
const int SIZE = 3;
string array1[SIZE][SIZE];

// simple allocation for the column and dynamic allocation for the rows
string *array2[SIZE];

for (int row = 0; row < SIZE; row++)
{
    array2[row] = new string[SIZE];
}

for (int row = 0; row < SIZE; row++)
{
    delete[] array2[row];
}

// pointer pointer
string **array3;
array3 = new string*[SIZE];

for (int row = 0; row < SIZE; row++)
{
    array3[row] = new string[SIZE];
}

for (int row = 0; row < SIZE; row++)
{
    delete[] array3[row];
}

delete[] array3;
```

### Section 2 - Stack vs. Heap Memory

```cpp
// an object is created in the heap and the pointer points to it
string *sp = new string[3];

// we are deleting the 3 strings that sp points to, not the variable sp
delete[] sp;
```

### Section 3 - Deep Memory Galaxies

```cpp
// dynamically allocated cstring
class Person
{
private:
    char* name;

    static const int MAX_LENGTH;

public:
    bool set_name(const char *c = "default");
    const char* get_name();
};

bool Person::set_name(const char* c)
{
    if (c == NULL || strlen(c) < 1 || strlen(c) > MAX_LENGTH - 1)
    {
        return false;
    }

    // free up memory (prevent memory leak)
    if (c)
    {
        delete name;
    }

    // re-allocate and copy
    name = new char[strlen(c) + 1];
    strcpy(name, c);
    return true;
}

// strcmp() will always return true. use strcpy() or reference parameter
const char* Person::get_name()
{
    // must have a static local
    static char buffer[MAX_LENGTH];
    strcpy(buffer, name);
    return buffer;
}

int main()
{
    Person person1, person2;
    char cstring[] = "hello";

    person1.set_name(cstring); // cstring
    person2.set_name("world"); // literal string
    return 0;
}
```

### Section 4 - Destructors and Copy Constructors

```cpp
// the heap associated with an object is not automatically destroyed
Person::~Person()
{
    if (name)
    {
        delete name;
    }
}

// copy constructor
Person::Person(const Person& person)
{
    name = NULL; // so that set_name knows not to delete
    set_name(person.name); // takes care of allocation
}
```

### Section 5 - The Full Galaxy Program

```cpp
// turns off strcpy() error in visual studio
#ifdef _MSC_VER
#define _CRT_SECURE_NO_WARNINGS
#endif

const int Person::MAX_LENGTH = 10;

Person::Person(const char* c)
{
    name = NULL;

    // one way to avoid testing motator return values
    set_name();
    set_name(c);
}
```

### Section 6 - Array-Based Stacks

```cpp
// stack example (double)
class MyStack
{
private:
    static const int SIZE = 5;
    double stck[size];
    int tos;

public:
    MyStack();

    bool push(double item);
    bool pop(double& item);

    void clear_stack();
    bool test_stack(int num_requested = 1);
}

MyStack::MyStack()
{
    tos = 0;
}

bool MyStack::push(double item)
{
    if (tos == SIZE)
    {
        return false;
    }

    stck[tos++] = item;
    return true;
}

bool MyStack::pop(double& item)
{
    if (tos == 0)
    {
        return false;
    }

    item = stck[--tos];
    return true;
}

void MyStack::clear_stack()
{
    tos = 0;
}

bool MyStack::test_stack(int num_requested)
{
    if (tos >= num_requested)
    {
        return true;
    }
    else
    {
        return false;
    }
}
```

## Week 4A - Introduction to Inheritance

### Section 2 - Derived Classes, Function Chaining and Constructors

```cpp
// constructor chaining
class Person
{
private:
    string name;

public:
    const string DEFAULT_NAME = "Default name";

    Person(string name);

    string get_name();
    bool set_name(string name);

    string to_string();
};

Person::Person(string name)
{
    if (!set_name(name))
    {
        set_name(DEFAULT_NAME);
    }
}

string Person::get_name()
{
    return name;
}

bool Person::set_name(string name)
{
    bool result = false;

    if (name.length() > 0)
    {
        result = true;
        this->name = name;
    }

    return result;
}

string Person::to_string()
{
    return "Name: " + name;
}

class Student : public Person
{
private:
    int id;

public:
    Student(string name, int id);

    int get_id();
    bool set_id(int id);

    string to_string();
};

Student::Student(string name, int id) : Person(name)
{
    if (!set_name(name))
    {
        set_name(DEFAULT_NAME);
    }
    if (!set_id(id))
    {
        set_id(0);
    }
}

int Student::get_id()
{
    return id;
}

bool Student::set_id(int id)
{
    bool result = false;

    if (id > 0)
    {
        result = true;
        this->id = id;
    }

    return result;
}

string Student::to_string()
{
    ostringstream oss;
    oss << id;
    return Person::to_string() + ", ID: " + oss.str();
}
```

### Section 3 - Building Blocks of A Dynamic Stack

```cpp
// a stacknode will hold a single item that is to be pushed onto the stack
class StackNode
{
public:
    StackNode* next;

    StackNode();
    virtual ~StackNode() {};

    void show();
};

StackNode::StackNode()
{
    next = NULL;
}

void StackNode::show()
{
    cout << "(generic node) ";
}
```

### Section 4 - The Stack Class

```cpp
// a stack contains nothing more than a single stacknode pointer
class Stack
{
    StackNode* top;

public:
    Stack();
    virtual ~Stack() {};

    void push(StackNode* new_node);
    StackNode* pop();

    void show_stack();
};

Stack::Stack()
{
    top = NULL;
}

StackNode* Stack::pop()
{
    StackNode* temp = top;

    if (top != NULL)
    {
        top = top->next;
        temp->next = NULL;
    }

    return temp;
}

void Stack::push(StackNode* new_node)
{
    if (new_node == NULL)
    {
        return;
    }

    new_node->next = top;
    top = new_node;
}

void Stack::show_stack()
{
    for (StackNode* curr = top; curr != NULL; curr = curr->next)
    {
        curr->show();
    }
}
```

## Week 4B - Implementing Inheritance

### Section 1 - Deriving a FloatNode

```cpp
// derive from stacknode
class FloatNode : public StackNode
{
private:
    float data;

public:
    FloatNode(float x);

    float get_data();

    void show();
};

FloatNode::FloatNode(float x)
{
    data = x;
}

float FloatNode::get_data()
{
    return data;
}

void FloatNode::show()
{
    cout << "[" << data << "] ";
}
```

### Section 2 - Deriving a FloatStack Class

```cpp
// all members and methods declared in stack will be private in floatstack
class FloatStack : private Stack
{
public:
    ~FloatStack() {};

    void push(float x);
    bool pop(float& f);
};

FloatStack::~FloatStack()
{
    StackNode* np;

    while (np = Stack::pop())
    {
        delete np;
    }
}

void FloatStack::push(float x)
{
    FloatNode* fp = new FloatNode(x);
    Stack::push(fp);
}

bool FloatStack::pop(float& f)
{
    f = 0.0F;
    FloatNode* fp = (FloatNode*) Stack::pop();

    if (fp == NULL)
    {
        return false;
    }

    f = fp->get_data();
    delete fp;
    return true;
}
```

## Week 5A - Operator Overloading

### Section 1 - Implications of Constructor Overloading

```cpp
// implied constructor calls
class Person
{
private:
    string name;

public:
    Person(const char* name);

    string get_name() { return name; }
};

Person::Person(const char* name)
{
    this->name = name;
}

void say_hello(Person person)
{
    cout << "hello " << person.get_name() << endl;
}

int main()
{
    say_hello("world"); // the compiler constructs a Person from the string
    return 0;
}

// explicit constructors
class Person
{
private:
    string name;

public:
    explicit Person(const char* name);

    string get_name() { return name; }
};

Person::Person(const char* name)
{
    this->name = name;
}

void say_hello(Person person)
{
    cout << "hello " << person.get_name() << endl;
}

int main()
{
    say_hello("world"); // error
    return 0;
}
```

### Section 2 - Friends

```cpp
// declaring friend functions
class Person
{
private:
    string name;

public:
    Person(string name);

    friend string get_name(Person person);
};

Person::Person(string name)
{
    this->name = name;
}

string get_name(Person person)
{
    return person.name; // no error
}

int main()
{
    cout << get_name(Person("hello")) << endl;
    return 0;
}

// declaring friend classes
class Person
{
private:
    string name;

public:
    Person(string name);

    friend class Human;
};

class Human
{
public:
    string get_name(Person person);
};

Person::Person(string name)
{
    this->name = name;
}

string Human::get_name(Person person)
{
    return person.name; // no error
}

int main()
{
    Human human;
    cout << human.get_name(Person("hello")) << endl;
    return 0;
}
```

### Section 3 - Operator Overloading

```cpp
// defining operator functions
class Person
{
private:
    Person* parent1, * parent2;

public:
    static Person operator+(Person person1, Person person2);
    Person operator+(Person person2);
};

Person Person::operator+(Person person1, Person person2)
{
    Person person;
    person.parent1 = &person1;
    person.parent2 = &person2;
    return person;
}

Person Person::operator+(Person person2)
{
    Person person;
    person.parent1 = this;
    person.parent2 = &person2;
    return person;
}

int main()
{
    Person person1, person2, person3;
    person3 = Person::operator+(person1, person2);
    person3 = person1 + person2;
    return 0;
}
```

### Section 5 - Overloading Insertion and Assignment Ops

```cpp
// overload as a non-member function
class Person
{
private:
    string name;

public:
    Person(string name);

    friend ostream& operator<<(ostream& os, const Person& person);
};

Person::Person(string name)
{
    this->name = name;
}

ostream& operator<<(ostream& os, const Person& person)
{
    return os << "name: " << person.name;
}

int main()
{
    cout << Person("hello") << endl;
    return 0;
}

// overload the assignment operator is much like defining a copy constructor
class Person
{
private:
    string name;

public:
    Person(string name);

    string get_name() { return name; }

    Person& operator=(const Person& person);
};

Person::Person(string name)
{
    this->name = name;
}

Person& Person::operator=(const Person& person)
{
    if (this != &person)
    {
        // any heap data should be allocated and copied
        this->name = person.name;
    }

    return *this;
}

int main()
{
    Person person1("hello");
    Person person2 = person1;
    cout << person2.get_name() << endl;
    return 0;
}
```

## Week 5B - Exceptions

### Section 1 - Guarded Code

```cpp
// a try/catch block
try
{
    // the try clause or a guarded section of code
}
catch (...)
{
    // the catch block or the exception handler
}
```

### Section 2 - Handling C++ Exceptions

```cpp
// (...) means "any exception at all"
```

### Section 3 - Throwing Exceptions and Nested Classes

```cpp
// use nested classes to distinguish different exceptions
class Person
{
private:
    string name;

public:
    Person(string name);

    bool set_name(string name);

    class IllegalName {};
};

Person::Person(string name)
{
    if (!set_name(name))
    {
        set_name("default name");
    }
}

bool Person::set_name(string name)
{
    if (name.length() == 0)
    {
        return false;
    }

    if (name[0] == ' ')
    {
        throw IllegalName();
    }

    this->name = name;
    return true;
}
```

### Section 4 - Catching Custon Exceptions

```cpp
// set_name() throws an exception
int main()
{
    try
    {
        Person person(" ");
    }
    catch (Person::IllegalName)
    {
        cout << "illegal name" << endl; // illegal name
    }

    return 0;
}
```

## Week 6A - Polymorphism and Virtual Functions

### Section 2 - Virtual Functions

```cpp
// fix show()
class StackNode
{
public:
    StackNode* next;

    StackNode();
    virtual ~StackNode() {};

    virtual void show();
};
```

### Section 4 - Abstract Classes and Pure Virtual Functions

```cpp
// virtual functions are not defined
class Person
{
protected:
    string name;

public:
    Person(string name) : name(name) {}

    virtual void say_hi() = 0;
};

class Student : public Person
{
public:
    Student(string name) : Person(name) {}

    void say_hi();
};

void Student::say_hi()
{
    cout << "Hi!" << endl;
}
```

## Week 6B - Deep Copies and 2D Barcode Readers

### Section 1 - Deep Copies of Images

```cpp
// define the assignment operator first, then call it from the copy constructor
#include <limits>

class Person
{
private:
    int** data;

public:
    static const int MAX_HEIGHT;
    static const int MAX_WIDTH;

    Person();
    ~Person();
    Person(const Person& person);
    const Person& operator=(const Person& person);

    bool set_data(int row, int col, int value);
    int get_data(int row, int col);

private:
    void allocateData();
    void deallocateData();
};

const int Person::MAX_HEIGHT = 5;
const int Person::MAX_WIDTH = 5;

Person::Person()
{
    data = NULL;
    allocateData();
}
Person::~Person()
{
    deallocateData();
}

Person::Person(const Person& person)
{
    data = NULL;
    allocateData();
    *this = person;
}

const Person& Person::operator=(const Person& person)
{
    if (this != &person)
    {
        for (int row = 0; row < MAX_HEIGHT; row++)
        {
            for (int col = 0; col < MAX_WIDTH; col++)
            {
                data[row][col] = person.data[row][col];
            }
        }
    }

    return *this;
}

bool Person::set_data(int row, int col, int value)
{
    if (row < 0 || row >= MAX_HEIGHT || col < 0 || col >= MAX_WIDTH)
    {
        return false;
    }

    data[row][col] = value;
    return true;
}

int Person::get_data(int row, int col)
{
    if (row < 0 || row >= MAX_HEIGHT || col < 0 || col >= MAX_WIDTH)
    {
        return INT_MAX; // use as an error
    }

    return data[row][col];
}

void Person::allocateData()
{
    if (data != NULL)
    {
        deallocateData();
    }

    data = new int* [MAX_HEIGHT];

    for (int row = 0; row < MAX_HEIGHT; row++)
    {
        data[row] = new int[MAX_WIDTH];

        for (int col = 0; col < MAX_WIDTH; col++)
        {
            data[row][col] = 0;
        }
    }
}

void Person::deallocateData()
{
    if (data == NULL)
    {
        return;
    }

    for (int row = 0; row < MAX_HEIGHT; row++)
    {
        delete[] data[row];
    }

    delete[] data;
    data = NULL;
}
```
