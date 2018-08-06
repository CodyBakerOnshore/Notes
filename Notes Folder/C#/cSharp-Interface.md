# C# Interfaces

<!-- TOC -->

- [C# Interfaces](#c-interfaces)
    - [The Basics](#the-basics)
    - [Define a Interface](#define-a-interface)
    - [Interface Can and Cannot](#interface-can-and-cannot)
    - [Implimenting](#implimenting)
    - [Interface Implimentation Example](#interface-implimentation-example)
    - [For Information about Explicit Implimentation:](#for-information-about-explicit-implimentation)
    - [More Details](#more-details)
    - [Interfaces Summery](#interfaces-summery)
    - [Related Pages](#related-pages)
    - [Feature Chaptor Comes From Book:](#feature-chaptor-comes-from-book)

<!-- /TOC -->

## The Basics
* A(n) interface containes *only the structures* of methods, properties, events, ***or*** indexers.
* A class or struct that impliments the interface *must* impliment *all* of the members of the interface that are specified in the interface definition.
* A(n) interface can be a member of a namespace ***or*** a class and *can* contain certain signatures of the following members:
    - Methods
    - Properties
    - Indexers
    - Events
* A(n) interface *can* inherit from ***from one or more*** base interfaces.
    - when a base type list containes a base class *and* interfaces, the base class *must* come first in the list.
* A class that impliments a(n) interface *can* explicitly impliment members of that interface.
    - A(n) explicitly implimented member *cannot* be accessed through a class instance, but instead *only* through an instance of the ***interface***.

### Example:
* The following example demonstraites interface Implimentation. In this example, the interface containes the *property declaration* and the class containes the *implimentation*. Any instance of a class that impliments <code> Ipoint </code> has integer properties <code>x</code> and <code>y</code>.

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
* Any class the *impliments* the <code>IEquatable<T></code> interface *must* contain a definition for an *Equals* method that matches the signature the the interface specifies. As a result, you can count on a class that *impliments* <code> IQuatable<T> </code> to contain a <code> Equals </code> method with which an instance of the class can determine weather it's equal to another instance of the same class.

To see the help page for *Equals* Method go [Here](https://docs.microsoft.com/en-us/dotnet/api/system.iequatable-1.equals?view=netframework-4.7.2).

* The definition of <code> IEquatable<T> </code> doesn't provide an implimentation for <code> Equals </code>. The interface defines *only* the signature. In that way, an interface in C# is similar to a *abstract class* in which all the method *are* abstract. However, a class or struct can impliment multiple interfaces, but a class can inherit *only* a single class, *abstract or not*. Therefore, by using interfaces, you can include behavior from multiple sources from *multiple sources* in a class.
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
* Interface Members are *Automattically public*, and can't include *any* access modifiers.
    - The also can't be static(s).

## Implimenting

* To impliment an interface member, the corresponding member of the implimenting class *must* be:
    - Public
    - Non-Static
    - AND
        + have the same name *and* signature as the interface member.

* When a class or struct impliments an interface, the class *or* struct *must* provide an implomentation for *all* of the members that the interface *defines*. The interface itself provides ***NO***  functionality that a class or struct can inherit in a way that it can inherit base class functionality. *However*, if a base class *impliments* an interface, *any* class that's *derived* from the base class inherts *that* implimentation.


## Interface Implimentation Example
* The Following example showes and implimentation of the <code>IEquatable<T></code> interface. The implimenting class, <code>car</code>, *must* provide an implimentation of the <code>Equals</code> method.

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

        // Implimentation of IEquatable<T> interface
        public bool Equals(Car car){
        return this.make == car.Make &&
               this.Model == car.Model &&
               this.Year == car.Year;
        }
    }
```

* Preoperties and Indexers of a class *can* define extra accessors for a property or indexer thats defined in an interface.
    - For example, an interface might declare a property that has a <code>get</code> accessor. The class that *impliments* the interface can *declare* the property with both a <code>get</code> *and* <code>set</code> accessors.
        + However if the property or indexer uses explicit Implimentation, the accessors *must* match!

## For Information about Explicit Implimentation:

* [Explicit Interface Implementation](https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/interfaces/explicit-interface-implementation)
* [Interface Properties](https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/classes-and-structs/interface-properties)


## More Details

Interfaces *can* impliment *other* interfaces. A class might include an interface multiple times through base classes that it inherits or through interfaces that *other* interfaces have implimented. However, the class *declares* the interface as part of the *definition* of the class<code>(class ClassName: InteraceName )</code>. If the interface *is* inherited *because* you inherited a base class that impliments the interface, the bvase class *provides* the implimentation.
* However, the derived class *can reimpliment* the interface members instead if using the *inheriated implimentation*.

A base class can also implicitly implement interface members by using *virtual members*. In that case, a derived class can change the interface behavior by overiding the the virtual members. 
* For more information on Virtual Members, See [Polymorphism](https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/classes-and-structs/polymorphism)

## Interfaces Summery

An interface has the following properties:
* An interface is *like* an abstract base class.
    - any class or struct that impliments the interface *must* impliment *all* of it's members.
* An interface *can't* be instantiated *directly*.
    - It's members are implimented in any class or struct the impliments the interface.
* Interfaces *can* contain:
    - events
    - indexers
    - methods
    - and properties
* Interfaces contain *no* implimentation of *methods*.
* A class or struct can impliment *multiple* interfaces.
    - a class can inherit a base class *and* also impliment one *or more* interfaces.

## Related Pages

* [Interface Properties](https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/classes-and-structs/interface-properties)
    - Personal notes when made go here!
* [Indexers in Interfaces](https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/indexers/indexers-in-interfaces)
    - Personal notes when made go here!
* [How To impliment Interface Events](https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/events/how-to-implement-interface-events)
    - Personal notes when made go here!
* [Classes and Structs](https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/classes-and-structs/index)
    - Personal notes when made go here!
* [Inheriatence](https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/classes-and-structs/inheritance)
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

## Feature Chaptor Comes From Book:
[Learning C# 3.0 Master The Fundamentals of C# 3.0](https://docs.microsoft.com/en-us/previous-versions/visualstudio/visual-studio-2008/ff652493(v=orm.10))
    - Specific Chapter: [Interfaces](http://msdn.microsoft.com/library/orm-9780596521066-01-13.aspx)