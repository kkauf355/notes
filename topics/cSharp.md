# .NET Framework

.NET is an open source developer platform to build applications (It's a computing framework for building applications on Windows, and it serves as an environment in which computer programs can run.)

It is composed of: 
- **Assemblies**, which are typically `.exe` or `.dll` files that contain compiled code which requires .NET to run.
- **The Common Language Runtime (CLR)**. This is a set of Windows libraries whose job is to run assemblies. It's essentially a Virtual Machine.
- **Class libraries**. A set of object-oriented APIs which can be used by assemblies.

It's possible for anyone to create a compiler that compiles a language for .NET, but the most common languages that use .NET are C# and VB.NET.

If you write your code to the framework, you can be sure it will work on anything that the framework says it can run on. In the case of Windows .NET, that means 'any' version of Windows. In the case of .NET Core, that's starting to mean 'any' modern device.

### .dll

Basically a module i.e. a collection of reusable code for other programs to call.

### .bat

A script file, equivalent to a Linux shell/bash script.

### Class Library

Applications consist of the building block classes.  

Related classes are organized in containers called Namespaces.  

Namespaces are organized in an Assembly, either an EXE (Executable) or DLL (Dynamically Linked Library)

When the application is compiled, one or more Assemblies are made.

# For Development

1. .NET contains a large set of programs which you can call through your program. These are the programs which contain simple functions like join two arrays to complex functions like translate voice to text /or recognize red object in a image(image analyses) etc, Provide functionality to make a internet application, mobile application etc, alot of them are provided(you can call those functions from your program). The .NET libraries are soo vast that you can program Robots/Arduino etc to develop signal processing, image analysis, large set of web application frameworks, etc.

2. It maintains a common language underneath and allows you to program in different higher level languages like C#, VB, IronPython etc. When you compile it convert to a common language. It provides different set of build tools to develop applications, integrate, add other frameworks, allow others to easily write frameworks, etc.

# For End User: 

When you develop a program in .NET (or you can say using .NET) to run this program on many other computers you need to have a corresponding .NET framework available on that computer. So you have to install the .NET framework before you run your program. The .NET framework which you install on different computers have all the functionality your program needs but it wont have the tools for compile/build/develop .NET applications (because those are not needed on the end user machines. They also ported this framework to Linux so you can run .NET applications on Linux platform.

# C#
C# is an object-oriented and type-safe programming language to write .NET applications

A solution is a grouping of projects
A project is a collection of files
A namespace is a collection of classes inside of a project


### Two Data Types
pre-defined     bool, int(int32), float, double, decimal, char, byte (sbyte), short(ushort), object, string
user-defined    

### Members on Primative Types
a member is a field, property, or method within a class or structure
int intMaxValue = int.MaxValue;
char.IsWhiteSpace  .IsDigit  .IsLetter  

Check the data type documention for members

strings use "", chars use ''

### Changing between types
Implicit conversion
    int a = 12345;
    long l = a;
Casting (explicit conversion)
    double d = 12345.0;
    int a = (int) d;
Helpers



## Methods
### Method Syntax
method signature
<access modifier> <return type> Method_Name (Parameters) {
    // code
}
OR <access modifier> <return type> Method_Name (Parameters) => <expression>

public int AddTwoNumbers(int a, int b) {
    return a + b;
}



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
If we do not create a constructor, c# will create a default constructor for us
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

# Visual Studio Shortcuts
Ctrl + K -> Ctrl + C    add comment
Ctrl + K -> Ctrl + U    remove comment
Ctrl + Shft + B         trigger build



# Vocab
Variable: named space in memory to store data
Fields: class level variables
Methods: class level functions
Properties: wrap the fields
Events

Interface: how it can be used
Public: makes a method usable to the outside
Private: only accessible from within the class
Protected: accessible to class in inheriters

Constructor: called when instantiating an object with the new keyword (new objects are created by constructors)

immutable: once created, it cannot be changed

namespace: a way to organize types in groups (folder with subfolders)
static: defined on the class level, not the object level. Sometehing that is shared for all objects and should not change.
