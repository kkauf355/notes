# .NET Framework

.NET is an open source developer platform to build applications (It's a computing framework for building applications on Windows, and it serves as an environment in which computer programs can run.)

It is composed of: 
- **Assemblies**, which are typically `.exe` or `.dll` files that contain compiled code which requires .NET to run.
- **The Common Language Runtime (CLR)**. This is a set of Windows libraries whose job is to run assemblies. It's essentially a Virtual Machine.
- **Class libraries**. A set of object-oriented APIs which can be used by assemblies.

It's possible for anyone to create a compiler that compiles a language for .NET, but the most common languages that use .NET are C# and VB.NET.

If you write your code to the framework, you can be sure it will work on anything that the framework says it can run on. In the case of Windows .NET, that means 'any' version of Windows. In the case of .NET Core, that's starting to mean 'any' modern device.


# C#
C# is an object-oriented and type-safe programming language to write .NET applications

A solution is a grouping of projects
A project is a collection of files

### Two Data Types
pre-defined     bool, int(int32), float, double, decimal, char, byte (sbyte), short(ushort), object, string
user-defined    

### Members on Primative Types
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


# Visual Studio Shortcuts
Ctrl + K -> Ctrl + C    add comment
Ctrl + K -> Ctrl + U    remove comment