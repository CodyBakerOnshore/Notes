# C# Interfaces

<!-- TOC -->

- [C# Interfaces](#c-interfaces)
    - [The Basics](#the-basics)
        - [Example:](#example)
    - [Define a Interface](#define-a-interface)
    - [Interface Can and Cannot](#interface-can-and-cannot)
    - [Implementing](#implementing)
    - [Interface Implementation Example](#interface-implementation-example)
    - [For Information about Explicit Implementation:](#for-information-about-explicit-implementation)
    - [More Details](#more-details)
    - [Interfaces Summery](#interfaces-summery)
    - [Related Pages](#related-pages)
    - [Feature Chapter Comes From Book:](#feature-chapter-comes-from-book)

<!-- /TOC -->

## The Basics
* A(n) interface contains *only the structures* of methods, properties, events, ***or*** indexers.
* A class or struct that implements the interface *must* implement *all* of the members of the interface that are specified in the interface definition.
* A(n) interface can be a member of a namespace ***or*** a class and *can* contain certain signatures of the following members:
    - Methods
    - Properties
    - Indexers
    - Events
* A(n) interface *can* inherit from ***from one or more*** base interfaces.
    - when a base type list contains a base class *and* interfaces, the base class *must* come first in the list.
* A class that implements a(n) interface *can* explicitly implement members of that interface.
    - A(n) explicitly implemented member *cannot* be accessed through a class instance, but instead *only* through an instance of the ***interface***.

### Example:
* The following example demonstrates interface Implementation. In this example, the interface contains the *property declaration* and the class contains the *implementation*. Any instance of a class that implements <code> Ipoint </code> has integer properties <code>x</code> and <code>y</code>.

```C#
        interface IPoint
        {
            // Property signatures:
            int x
            {
                get;
                set;
            }
            int y
            {
                get;
                set;
            }
        }
        class Point : IPoint
        {
        // Fields:
        private int _x;
        private int _y;

        // Constructor:
        public Point(int x, int y)
        {
            _x = x;
            _y = y;
        }

        // Property implementation:
        public int x
        {
            get
            {
                return _x;
            }
            set
            {
                _x = value;
            }
        }
        public int y
        {
            get
            {
                return _y;
            }
            set
            {
                _y = value;
            }
        }
        class MainClass
        {
        static void PrintPoint(IPoint p)
        {
            Console.WriteLine("x={0}, y={1}", p.x, p.y);
        }
        static void Main()
        {
            IPoint p = new Point(2, 3);
            Console.Write("My Point: ");
            PrintPoint(p);
        }
    }// Output: My Point: x=2, y=3   
```

## Define a Interface

* You can define an interface by using the <code> interface </code> keyword, as the following example shows.

```C#
    interface IEquatable<T>
    {
        bool equals(T obj);
    }
```
* Any class the *implements* the <code>IEquatable<T></code> interface *must* contain a definition for an *Equals* method that matches the signature the the interface specifies. As a result, you can count on a class that *implements* <code> IEquatable<T> </code> to contain a <code> Equals </code> method with which an instance of the class can determine weather it's equal to another instance of the same class.

To see the help page for *Equals* Method go [Here](https://docs.microsoft.com/en-us/dotnet/api/system.iequatable-1.equals?view=netframework-4.7.2).

* The definition of <code> IEquatable<T> </code> doesn't provide an implimentation for <code> Equals </code>. The interface defines *only* the signature. In that way, an interface in C# is similar to a *abstract class* in which all the method *are* abstract. However, a class or struct can implement multiple interfaces, but a class can inherit *only* a single class, *abstract or not*. Therefore, by using interfaces, you can include behavior from multiple sources from *multiple sources* in a class.
    - For more information on *Abstract/Sealed classes and class members* go [Here](https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members)

## Interface Can and Cannot

* Interfaces can contain:
    - Methods
    - Properties
    - Events
    - Indexers
    -or
        + Any combination of the four.
* Interfaces *cant* contain:
    - Constants
    - Fields
    - Operators
    - Instance *Constructors*
    - Finalizers
    - or
        + Types
* Interface Members are *Automatically Public*, and can't include *any* access modifiers.
    - The also can't be static(s).

## Implementing

* To implement an interface member, the corresponding member of the implementing class *must* be:
    - Public
    - Non-Static
    - AND
        + have the same name *and* signature as the interface member.

* When a class or struct implements an interface, the class *or* struct *must* provide an implementation for *all* of the members that the interface *defines*. The interface itself provides ***NO***  functionality that a class or struct can inherit in a way that it can inherit base class functionality. *However*, if a base class *implements* an interface, *any* class that's *derived* from the base class inherits *that* implementation.


## Interface Implementation Example
* The Following example show's and implementation of the <code>IEquatable<T></code> interface. The implementing class, <code>car</code>, *must* provide an implementation of the <code>Equals</code> method.

```C#
    public class Car : IEquatable<Car>{
        public string Make {
            get;
            set;
        }
        public string Model{
            get;
            set;
        }
        public string Year{
            get;
            set;
        }

        // Implementation of IEquatable<T> interface
        public bool Equals(Car car){
        return this.make == car.Make &&
               this.Model == car.Model &&
               this.Year == car.Year;
        }
    }
```

* Properties and Indexers of a class *can* define extra accessors for a property or indexer thats defined in an interface.
    - For example, an interface might declare a property that has a <code>get</code> accessor. The class that *implements* the interface can *declare* the property with both a <code>get</code> *and* <code>set</code> accessors.
        + However if the property or indexer uses explicit Implementation, the accessors *must* match!

## For Information about Explicit Implementation:

* [Explicit Interface Implementation](https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/interfaces/explicit-interface-implementation)
* [Interface Properties](https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/classes-and-structs/interface-properties)


## More Details

Interfaces *can* implement *other* interfaces. A class might include an interface multiple times through base classes that it inherits or through interfaces that *other* interfaces have implemented. However, the class *declares* the interface as part of the *definition* of the class<code>(class ClassName: InterfaceName )</code>. If the interface *is* inherited *because* you inherited a base class that implements the interface, the base class *provides* the implimentation.
* However, the derived class *can re-implement* the interface members instead of using the *inherited implimentation*.

A base class can also implicitly implement interface members by using *virtual members*. In that case, a derived class can change the interface behavior by overriding the the virtual members. 
* For more information on Virtual Members, See [Polymorphism](https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/classes-and-structs/polymorphism)

## Interfaces Summery

An interface has the following properties:
* An interface is *like* an abstract base class.
    - any class or struct that implements the interface *must* implement *all* of it's members.
* An interface *can't* be instantiated *directly*.
    - It's members are implemented in any class or struct the implements the interface.
* Interfaces *can* contain:
    - events
    - indexers
    - methods
    - and properties
* Interfaces contain *no* implementation of *methods*.
* A class or struct can implement *multiple* interfaces.
    - a class can inherit a base class *and* also implement one *or more* interfaces.

## Related Pages

* [Interface Properties](https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/classes-and-structs/interface-properties)
    - Personal notes when made go here!
* [Indexers in Interfaces](https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/indexers/indexers-in-interfaces)
    - Personal notes when made go here!
* [How To impliment Interface Events](https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/events/how-to-implement-interface-events)
    - Personal notes when made go here!
* [Classes and Structs](https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/classes-and-structs/index)
    - Personal notes when made go here!
* [Inheritance](https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/classes-and-structs/inheritance)
    - Personal notes when made go here!
* [Methods](https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/classes-and-structs/methods)
    - Personal notes when made go here!
* [Polymorphism](https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/classes-and-structs/polymorphism)
    - Personal notes when made go here!
* [Abstract and Sealed Classes and Class Members](https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members)
    - Personal Notes when made go here!
* [Properties](https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/classes-and-structs/properties)
    - Personal Notes When Made Go Here!
* [Events](https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/events/index)
    - Personal Notes when made Here!
* [Indexers](https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/indexers/index)
    - Personal Notes will go here

## Feature Chapter Comes From Book:
[Learning C# 3.0 Master The Fundamentals of C# 3.0](https://docs.microsoft.com/en-us/previous-versions/visualstudio/visual-studio-2008/ff652493(v=orm.10))
    - Specific Chapter: [Interfaces](http://msdn.microsoft.com/library/orm-9780596521066-01-13.aspx)