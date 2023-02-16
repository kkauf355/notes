# C#
C# is an object-oriented and type-safe programming language to write .NET applications

A solution is a grouping of projects
A project is a collection of files
A namespace is a collection of classes inside of a project


## Two Data Types
pre-defined     bool, int(int32), float, double, decimal, char, byte (sbyte), short(ushort), object, string
user-defined    enum, struct, class, interface, delegate

### Changing between types
Implicit conversion
    int a = 12345;
    long l = a;
Casting (explicit conversion)
    double d = 12345.0;
    int a = (int) d;
Helpers

## Member
A field, property, or method within a class or structure
    E.x. int.MaxValue, char.IsWhiteSpace,  .IsDigit,  .IsLetter 

## Variable
named space in memory to store data

## Fields
class level variables

## Methods
class level functions which define behavior of an object

### Method Syntax
<access modifier> <return type> Method_Name (Parameters) {
    // code
}
OR 
<access modifier> <return type> Method_Name (Parameters) => <expression>

```c#
public int AddTwoNumbers(int a, int b) {
    return a + b;
}
```

## Properties
wrap the fields to provides a flexible mechanism to read, write, or compute the value of a private field
members of a class, just like methods that sit around the private data of a class
hides implementation
```c#
public class Employee {
    private int age;
    public int Age {
        get { return age; }
        set { age = value; }
    }
}
```

## Access Modifiers
Public: makes a method usable to the outside
Private: only accessible from within the class
Protected: accessible to class in inheriters

## Optional Parameters
```c#
public int AddNumbers (int a, int b, int c = 100) {
    int sum = a + b + c;
    return sum;
}
AddNumbers(10, 20); // No 3rd parameter
AddNumbers(10, 20, 30);
```

### Named Arguments
```c#
public static int AddNumbers(int a, int b) {
    return a + b;
}
AddNumbers(b: 10, a: 20);
```

## Strings
strings use "", chars use ''

### String Interpolation
```c#
$"Hello {friend}, it's {me}"
```
### Verbatim Strings
if a string contains \ as part of the content
```c#
@"C:\Documents\readme.txt";
```

### StringBuilder
StringBuilder builds strings in a more performant way, without all the copies.
If you need to concat alot of strings, use a stringbuilder
```c#
StringBuilder builder = new StringBuilder();
builder.Append("Last name: ");
builder.AppendLine(lastName);
builder.Append("First name: ");
builder.Append(firstName);
string result = builder.ToString();
```

# Types in .NET
There are 5 types in .NET
Classes, Enumeration, Struct, Interface, Delegate

## Classes
A class is the blueprint of an object

Class Template
```c#
public class MyClass {
    public int a;
    public string b;

    public void MyMethod() {
        Console.WriteLine("Hello world");
    }
}
```

### Objects
An object is an instance of a class
Employee kevin = new Employee();

#### Adding a Constructor
A constructor is a method whose name is the same as the name of its type.
They initialize new objects.
If we do not create a constructor, c# will create a default constructor for us.
```c#
public class Employee {
    public string firstName;
    public int age;

    public Employee(string name, int ageValue) {
        firstName = name;
        age = ageValue;
    }
}
```
## Struct
Like a class, but too simple to be a class
Can be new'ed
Can contain methods
Created on stack
```c#
struct WorkTask {
    public string description;
    public int hours;

    public void PerformWorkTask() {
        // Perform work!
    }
}
```

## Interfaces
define a contract that must be implemented by classes that use it
```c#
public interface IEmployee {
    void PerformWork();
    int ReceiveWage();
}
```

## Arrays
```c#
int[] sampleArray1 = new int[5];
int[] sampleArray2 = new int[] {1,2,3,4,5};

Array.Sort(sampleArray2);

int[] array2Copy = new int[5];
sampleArray2.CopyTo(array2Copy, 0);

Array.Reverse(array2Copy);
```

## Lists
```c#
List<int> sampleList = new List<int>();
sampleList.Add(2);
sampleList.Add(4);
sampleList.Remove(2);
sampleList.Count;
sampleList.Contains(2);
sampleList.Clear();
sampleList.Insert(0, 9);
```

## Values Types and Reference Types
#### value types
fixed size, allocated by compiler on stack. Value is copied to this memory location. E.g. primitives (int, float, double, char), Enumerations, Structs
#### reference types
allocated on heap. The stack contains a reference to the object. E.g. strings, Classes, Interfaces, Delegates

### Passing Parameters
#### by value
default way of passing parameters
A copy is created for the method
Value in caller is not changed

#### by reference
a reference to the value is passed
no copy is made
changes made in method affect original values
ref keyword is used

##### ref/out keywords
the ref keyword requires a variable to be initialized
the out keyword:
also passes by reference
does not require the variable to be initialized
multiple values may be returned
before the method exists, the out parameter must be initialized

ref keyword syntax
```c#
public int AddTwoNumbers(int a, ref int b) {
    b += 10;
    return a + b;
}
```
out keyword syntax
```c#
public int AddTwoNumbers(int a, out int b, out int c) {
    b = 10;
    int sum = a + b;
    c = sum / 10;
    return sum;
}
```

## Static
member defined on the class level, not the object level. Sometehing that is shared for all objects and should not change.

## Null
adding ? to variable type (double?) allows the variable to be a double OR null
hourlyRate = rate ?? 10; // says if rate is null, make hourlyRate 10

# Visual Studio Shortcuts
Add comment:        Ctrl + K -> Ctrl + C
Remove comment:     Ctrl + K -> Ctrl + U
Trigger build:      Ctrl + Shft + B

# Vocab
Constructor: called when instantiating an object with the new keyword (new objects are created by constructors)
immutable: once created, it cannot be changed
namespace: a way to organize types in groups (folder with subfolders)
virtual: signal that types can provide own implementation
override: this version is the new version of the method

# OOP
## Encapsulation
Containing information inside objects
Only certain information is exposed
Hides internal implementation of data
Avoid data corruption
Private and public

## Abstraction
Abstract representation of the program
Only mechanisms useful for other objects are revealed
    Implementation is hidden
    making changes becomes easier

## Inheritance
Classes can resue functionality from others
Relation between classes
Lower development time because of reusability

## Polymorphism
Share behaviors but can be in more than one form
Child can sstill be used like its parent
Correct method will be used based on execution

