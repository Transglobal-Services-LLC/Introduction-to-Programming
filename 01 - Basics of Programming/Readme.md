# Programming Basics

This documentation is intended to serve as a basic introduction to our team to some programming/scripting principles for IT Ops, Sec Ops and GIS work. It will be heavily focused on Python, since this language is heavily used across the relevant sectors for our organization. 

## Programming Environment

### Runtime
What translates the script/application code you have written into something the CPU can process, *while* the application is running. Low-level languages, which are closer to the CPU (C, C++), have hardly any runtime. Higher level languages like C# and Java have much more complex runtimes. 

.NET Runtime - C#

Python.exe - Python

Java Runtime Environment (JRE) - Java

### Development Kit
**SDKs** - Software Development Kit - what is used by the developer to have the tools to program in that language. 

.NET SDK

Java SDK

**IDEs** - Integrated Development Environment - Used to develop applications. Has various tools like intellisense. 

Visual Studio

IntelliJ

## Programming Data Types

Programming languages use "data types" which are a classification of data that tells the compiler or interpreter how the developer intends to use the data. Most programming languages support various types of data such as integers, characters, strings and booleans. 

**String** - Usually enclosed in double quotes, or a single quote. Basically just text being printed or fed to an function. In SQL, this is called varchar, or nvarchar. 
```python
# String example
string1 = "Test String"
print(string1)
```

**Integer** - Number values. No quotes represeted simply as 1 or 2. 
```python
# Int example
number = 1
print(number + 2)
```

**DateTime** - Date Time variables can be in various formats. Can usually be manipulated for timezones, different formatting, adding or removing time, etc. 

Python, unlike SQL or C#, does not treat a date as its own datatype. It instead uses a datetime module to handle datetimes as objects which can be accessed by using "import datetime."

```python
# Date Time Result 2022-02-25 17:03:18.452669
import datetime

right_now = datetime.datetime.now()
print(right_now)
```

**Boolean** - True or False. In SQL, represted as a bit with 0 or 1 as the representation; 0 being false, 1 being true. 
```python
# Boolean Example - Expected Result True. 1 will be the same as True in a boolean comparison.
test = True
if(test == 1):
    print(True)
else:
    print(False)
```

**Float** - Decimal Points. Not whole numbers. 
```python
# Float Example - Expected Result 3.67
float = 1.22
print(float + 2.45)
```

## Variables
Something that you can define as the programmer to store in memory while the application executes. 

For instance declaring Name = "Dane"

## Logical and Arithmetical Operators

```python
name = 1 # Assignment Operator; Assigns something.
name == 1 # Comparison Operator; Check if things are equal.
name != 1 # Comparison Operator; Check if NOT equal to something.
```

## Classes/Objects

Python is an object oriented programming (OOP) language. Almost everything in Python is returned as an object, with properties and methods. 

### Classes

A class is like an object constructor, or a "blueprint" for creating objects. A class has a keyword that is used to instantiate one. 

```python
# Create a class called router, create a new object instance from the class and print the IP. 
# Expected Result 10.100.100.1
class Router:
    Name = "ABC-FW01"
    Model = "Cisco ASA5505"
    IP = "10.100.100.1"

router = Router()
print(router.IP)
```

### The Init Function

The `__init__()` Function.

The examples above are classes and objects in their simplest forms. To understanding the more advanced purposes of classes, we have to understand the built-in `__init__()` function. This function is executed everytime a class is being initiated. 

Use the init function to assign values to object properties, or other operations to do when the object is created. 

```python
class Router:

    def __init__(self, name, model, ip):
        self.name = name
        self.model = model
        self.ip = ip

ciscoRouter = Router("ABC-FW01", "Cisco ASA5505", "10.100.100.1")
fortigateRouter = Router("ABC-FW02", "Foritgate 100E", "10.200.100.1")

print(ciscoRouter.ip)
print(fortigateRouter.ip)
```

### Object Methods

Objects can also contain methods. A methods in objects are functions that belong specifically to that object. 

We can create a method for instance that can print the info of the firewall out as a string:

```python
# Expected Output: The firewall ABC-FW01 is on IP 10.100.100.1
class Router:

    def __init__(self, name, model, ip):
        self.name = name
        self.model = model
        self.ip = ip

    def getInfo(self):
        print(f"The firewall {self.name} is on IP {self.ip}")

ciscoRouter = Router("ABC-FW01", "Cisco ASA5505", "10.100.100.1")

print(ciscoRouter.getInfo())
```
