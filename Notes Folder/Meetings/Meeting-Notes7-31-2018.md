#  Notes

<!-- TOC -->

- [Notes](#notes)
- [7-31-2018](#7-31-2018)
- [UML?](#uml)
- [Stack vs. Head](#stack-vs-head)
- [Class vs Struct](#class-vs-struct)
- [Singleton Pattern](#singleton-pattern)

<!-- /TOC -->

  

#  7-31-2018

  

* Calculate Method

* Task: Asynchronous Operation(s)

* Delegate

* Struct

* *Boxing*/*Unboxing*: explicit conversion of a value type to an object

* Regex(Regular Expressions)

* *Static* Vs. *Non-Static*: (Stack-Overflow)

* Abstract

* Dependency Injection

  

* in abstract classes you ***can*** have *implementations*, you ***can't*** in interfaces.

  

#  UML?
* lookup

    * if you use abstract the *child* methods ***NEED*** to implement them.

    * abstracts are how C# handles *multiple* inheritance.

    * you ***can't*** create a object FROM a interface.

  

#  Stack vs. Head

* stack

    + Value

* Head

    + Ref

  
  

```C#

void  ChangeB(int num) {

obj.Color  =  'Red';

}

void  ChangeB(Animal obj){

num  =  0;

}

```

  

#  Class vs Struct

- Struct
    + Ref
    + Cant/ Does not allow *Null*
- Class
    + Value

  

#  Singleton Pattern

- essentially is a *Unique* Instance implementation to call/use in *all* locations.

    - Ex:

    ```C#

        class Config{

            public string CurrentUser{

                    Config Instance;

                    Config(){

                        if(this.instance == null){

                        instance = new Config();

                        }

                }

            }

        }```

  

- we would add static to Config Instance to load it on program **START**.

    + recommends just adding static to public string call then just using ```C# config.CurrentUser ``` to call it.

  

###  *Generally Donate 5-20% of time to **Refactoring***.

  

* 50% of the problem is understand the goal/task and the *reason* for the task.

* Ex:

    - increase preference or memory usage.

* Think from the view point of the *Customer*/*User*.

    - "Think Twice, Code Once" *Quote from Somewhere*

    - Understand the *Flow* of the task.

    - Understand the *Architecture* of the program if you are working on a Previous build program.

  

###  <u>***Look into multi-threading***.</u>
