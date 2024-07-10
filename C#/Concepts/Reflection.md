# Learning Plan for Reflection in C#

## Core Concepts

1. **Understanding Reflection**
   - What is Reflection?
   - When and why to use Reflection?

2. **Key Classes and Namespaces**
   - `System.Reflection` namespace
   - `Type` class
   - `MethodInfo`, `PropertyInfo`, `FieldInfo` classes

3. **Basic Operations with Reflection**
   - Loading assemblies
   - Getting types from assemblies
   - Inspecting types (properties, methods, fields)
   - Invoking methods dynamically
   - Getting and setting property/field values dynamically

4. **Practical Use Cases**
   - Creating instances dynamically
   - Accessing private members
   - Working with attributes
   - Reflection in Unit Testing (e.g., setting private fields)

## Step-by-Step Learning Plan

### 1. Understanding Reflection

**Read**: Overview of Reflection in C#
- Article: [Introduction to Reflection in C#](https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/concepts/reflection)
- Key Points: What reflection is, and its typical use cases.

### 2. Key Classes and Namespaces

**Learn**: The most important classes in `System.Reflection`.
- `Type`: Represents type declarations for class types, interface types, array types, value types, enumeration types, type parameters, generic type definitions, and open or closed constructed generic types.
- `MethodInfo`, `PropertyInfo`, `FieldInfo`: Represent methods, properties, and fields of a class.

**Read**: [System.Reflection Namespace](https://docs.microsoft.com/en-us/dotnet/api/system.reflection)

### 3. Basic Operations with Reflection

**Practice**: Write code to perform basic reflection operations.

**Example**: Getting the type of an object and listing its methods and properties.

```csharp
using System;
using System.Reflection;

class Program
{
    static void Main()
    {
        // Get the type of a class
        Type type = typeof(SomeClass);

        // List all methods
        MethodInfo[] methods = type.GetMethods();
        foreach (var method in methods)
        {
            Console.WriteLine("Method: " + method.Name);
        }

        // List all properties
        PropertyInfo[] properties = type.GetProperties();
        foreach (var property in properties)
        {
            Console.WriteLine("Property: " + property.Name);
        }
    }
}

class SomeClass
{
    public int SomeProperty { get; set; }
    public void SomeMethod() { }
}
```

**Explore**: Invoking methods and accessing properties/fields dynamically.

**Example**:

```csharp
class Program
{
    static void Main()
    {
        SomeClass instance = new SomeClass();
        Type type = typeof(SomeClass);

        // Set property value
        PropertyInfo prop = type.GetProperty("SomeProperty");
        prop.SetValue(instance, 42);

        // Invoke method
        MethodInfo method = type.GetMethod("SomeMethod");
        method.Invoke(instance, null);

        Console.WriteLine("Property Value: " + prop.GetValue(instance));
    }
}

class SomeClass
{
    public int SomeProperty { get; set; }
    public void SomeMethod() { Console.WriteLine("Method Invoked"); }
}
```

### 4. Practical Use Cases

**Create Instances Dynamically**:

**Example**:

```csharp
Type type = typeof(SomeClass);
object instance = Activator.CreateInstance(type);
```

**Accessing Private Members**:

**Example**:

```csharp
class Program
{
    static void Main()
    {
        SomeClass instance = new SomeClass();
        Type type = typeof(SomeClass);

        // Access private field
        FieldInfo field = type.GetField("_privateField", BindingFlags.NonPublic | BindingFlags.Instance);
        field.SetValue(instance, 100);

        Console.WriteLine("Private Field Value: " + field.GetValue(instance));
    }
}

class SomeClass
{
    private int _privateField = 0;
}
```

**Working with Attributes**:

**Example**:

```csharp
using System;
using System.Reflection;

class Program
{
    static void Main()
    {
        Type type = typeof(SomeClass);
        foreach (var prop in type.GetProperties())
        {
            if (Attribute.IsDefined(prop, typeof(MyAttribute)))
            {
                Console.WriteLine($"{prop.Name} has MyAttribute");
            }
        }
    }
}

class SomeClass
{
    [MyAttribute]
    public int SomeProperty { get; set; }
}

[AttributeUsage(AttributeTargets.Property)]
class MyAttribute : Attribute { }
```

**Reflection in Unit Testing**:

**Use reflection to set private fields or call private methods to test internal behavior.**

Example with NUnit:

```csharp
[TestFixture]
public class SomeClassTests
{
    [Test]
    public void TestPrivateField()
    {
        var instance = new SomeClass();
        var field = typeof(SomeClass).GetField("_privateField", BindingFlags.NonPublic | BindingFlags.Instance);
        field.SetValue(instance, 123);

        // Use reflection to get the private field value
        var fieldValue = (int)field.GetValue(instance);
        Assert.AreEqual(123, fieldValue);
    }
}

class SomeClass
{
    private int _privateField;
}
```

### Summary

By focusing on the above key concepts and practical use cases, you'll cover the 20% of reflection in C# that will give you the most benefits. This foundational knowledge will enable you to understand and apply reflection effectively in your projects.
