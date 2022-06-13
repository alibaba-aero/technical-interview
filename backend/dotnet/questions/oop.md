# Object-Oriented

## Programming paradigms
* What are programming paradigms?
  * A programming paradigm is a way of conceptualizing what it means to perform computation, and how tasks that are to be carried out on a computer should be structured and organized.
  * Programming paradigm involves viewing the solution of a problem by combining Data and Algorithms in different ways
## OOP Paradigms
* What's OOP paradigms
  * A very powerful paradigm for modeling real-world phenomena in a computational model
## Object-Oriented
  * What Is a Class?
  * What Is an Abstract Class?
  * What Is an Interface?
  * What Is an Object?
  * What is the difference between a class and an object?
  * What are the differences between an abstract class and an interface?
  * What are access specifiers?
  * What is Static Class?
  * What is the Static Method?
  * What are **Object Oriented Principles**
    * [Abstraction](#abstraction)
    * [Encapsulation and Information Hiding](#encapsulation-and-information-hiding)
    * [Inheritance](#inheritance)
    * [Polymorphism](#polymorphism)
### Object Oriented Principles
* What are Abstraction, Encapsulation, and Information Hiding differences?
    * **Abstraction** is only concerned about which item should be hidden. What should (not) be hidden (or ignored) is the concern of abstraction. 
    * **Encapsulation** is bundling of data and operations on the data into an entity called a class and is not concerned with whether the items that are bundled in an entity are hidden from other modules in the application or not. 
    * **Information Hiding** is concerned with how an item is hidden
### Abstraction
* What's Abstraction?
  * Abstraction is a way to perform decomposition of a problem by focusing on relevant details and ignoring the irrelevant details about it in a particular context
* what's decomposition?
  * involves analyzing a complex problem or system and breaking it down into smaller parts that are more manageable and easy to understand
* What types of Abstraction are there?
  * [Data Abstraction](#data-abstraction)
  * [Procedural (Process,Control) Abstraction](#procedural-processcontrol-abstraction)
#### Data Abstraction
* What's Data Abstraction?
  * hiding the details about the data
  * lets programmers create a new data type called an abstract data type (ADT)
* How can achieve data abstraction?
#### Procedural (Process,Control) Abstraction
* What's Procedural Abstraction?
  * hide the internal implementation and details
* What types of Procedural Abstraction exists?
  * [Procedural Abstraction by Parameterization](Procedural-Abstraction-by-Parameterization)
  * [Procedural Abstraction by Specification](Procedural-Abstraction-by-Specification)
##### Procedural Abstraction by Parameterization
  * What is Procedural Abstraction by Parameterization?
    * We seek generality by allowing the same mechanism to be adapted to many different contexts by providing it with information on that context
##### Procedural Abstraction by Specification
  * What is Procedural Abstraction by Specification?
    * We ignore the implementation details and agree to treat as acceptable any implementation that adheres to the specification
### Encapsulation and Information Hiding
  * What is Encapsulation?
    * Encapsulation is simply the bundling of items together into one entity
  * What is Information Hiding?
    * Information hiding is the process of hiding implementation details that are likely to change
### Inheritance
  * What's Inheritance?
    * The inheritance mechanism lets you define a new abstraction by extending an existing abstraction
    * Inheritance allows you to use varying degrees of abstraction at different levels of hierarchy
    * Inheritance is also used as a technique to implement polymorphism
  * What's Multiple Inheritance?
    * **Name ambiguity**
      * Inherited, different features can have the same name
      * Same features may be inherited several times
    * **Impact on substitutability**
      * Parent constructor calling in Diamond problem
      * Ambiguity in calling method has override in supper classes but not in descendent class
      * Overriding a method that has been inherited from several supper classes
    * **Increase Complexity**
### Polymorphism
  * What's Polymorphism?
    * Polymorphism is the ability of an entity (e.g. variable, class, method, object, code, parameter, etc.) to take on different meanings in different contexts.
  * What types of Polymorphism are there?
    * [Ad hoc Polymorphism](#ad-hoc-polymorphism)
      * [Overloading Polymorphism](#overloading-polymorphism)
      * [Coercion polymorphism](#coercion-polymorphism)
    * [Universal Polymorphism](#universal-polymorphism)
      * [Inclusion Polymorphism](#inclusion-polymorphism)
      * [Parametric polymorphism](#parametric-polymorphism)
#### Ad hoc Polymorphism
  * What's Ad hoc Polymorphism?
    * a piece of code works finite and all those types must be known when the code is written
  * What types of Ad hoc Polymorphism are there?
    * [Overloading Polymorphism](#overloading-polymorphism)
    * [Coercion polymorphism](#coercion-polymorphism)
##### Overloading Polymorphism
  * What's Overloading Polymorphism?
    * When a method or an operator has at least two definitions that work on a different type
  * Make an example
    ```C#
    //Method overloading
    Do()
    Do(10)

    //operator overloading
    var i = 1 + 1;
    var j = 1.5 + 2;
    ```
##### Coercion Polymorphism
  * What's Coercion Polymorphism?
    * When a type is implicitly converted (coerced) to another type automatically even if it was not intended explicitly
  * Make an example
    
    ```C#
    var int i = 1;
    var double d = i;
    var double d = (double)i;  
    ```
#### Universal Polymorphism
  * What's Universal Polymorphism?
    * a piece of code is written in such a way that it works for an infinite number of types
  * What types of Universal Polymorphism are there?
    * [Inclusion Polymorphism](#inclusion-polymorphism)
    * [Parametric polymorphism](#parametric-polymorphism)
##### Inclusion Polymorphism
  * What's Inclusion Polymorphism?
    * When a piece of code that is written using a type works for all its subtypes
  * Make an example

    ```C#
    void processDetails(Person p) 
    { 
      // Write code using the formal parameter p, which is of type Person.
      // The same code will work if an object of any of the subclass of Person is passed to this method.
    } 
    /************************************client code*************************************************/ 
    Person p1 = new Person(); 
    Employee e1 = new ; 
    Customer c1 = create a Customer object; 
    processDetails(p1); // Use Person type 
    processDetails(e1); // Use Employee type, which is a subclass of Person 
    processDetails(c1); // Use Customer type, which is a subclass of Person
    ```
##### Parametric polymorphism
  * What's Parametric polymorphism?
    * Parametric polymorphism is achieved by using a type variable when writing the code, rather than using any specific type
    * It is also called “true” polymorphism because it lets you write true generic code that works for any types (related or unrelated)
  * What types of Parametric Polymorphism are there?
    * [Invariant](#invariant)
      * Means that you can use only the type originally specified
    * [Covariant](#covariant)
      * Enables you to use a more derived type than originally specified
    * [Contravariant](#contravariant)
      * Enables you to use a more generic (less derived) type than originally specified
###### Invariant Parametric polymorphism
  * What's Invariant Parametric polymorphism?
      * Means that you can use only the type originally specified

  ```C#
    var list = new Lis<int>();
  ```
###### Covariant Parametric polymorphism
  * What's Covariant Parametric polymorphism?
      * Enables you to use a more derived type than originally specified

  ```C#
    IEnumerable<Derived> enumerable1 = new List<Derived>(); //IEnumerable<out T> 
    IEnumerable<Base> enumerable2 = enumerable1;
  ```
###### Contravariant Parametric polymorphism
  * What's Contravariant Parametric polymorphism?
    * Enables you to use a more generic (less derived) type than originally specified

  ```C#
    Action<Base> action1 = target => { ... }; //Action<in T> 
    Action<Derived> action2 = action2; 
    action2(new Derived());
  ```
### Dispatch
  * What's Dispatching?
    * it is a way how the programming language calls a method or a function
  * What types of Dispatch are there?
    * [Static Dispatch](#static-dispatch)
      * Every method is known at the compile time
    * [Dynamic Dispatch](#dynamic-dispatch)
      * Dynamically dispatched methods are determined at run time based on its parameter’s types
#### Static Dispatch
  * What's Static Dispatch?
    * Every method is known at the compile time
  * Make an example
    ```C#
    //classes
    interface IBar {} 
    class Bar : IBar {} 
    sealed class FooBar : Bar {} 
    
    //methods
    void Print(IBar item){Console.WriteLine("It is an IBar.");} 
    void Print(Bar item){Console.WriteLine("It is a Bar.");} 
    void Print(FooBar item){Console.WriteLine("It is a FooBar.");}

    //call methods
    var bar = new Bar(); 
    var foo = new FooBar(); 
    IBar ibar = new FooBar(); 
    Print(bar);
    Print(foo);
    Print(ibar);
    ```
    Output:
    ```
    It is an Bar.
    It is a FooBar.
    It is an IBar.
    ```
#### Dynamic Dispatch
  * What's Dynamic Dispatch?
    * Dynamically dispatched methods are determined at run time based on their parameter’s types
  * What types of Dynamic Dispatch are there?
    * Single dynamic dispatch
      * Single ones use just one parameter to select a method
      * Satisfy by **overriding**
    * Multiple dynamic Dispatch
      * The multiple ones can take advantage of as many parameters they want
      * Satisfy by **DLR** (Dynamic Language Runtime)

##### Single dynamic dispatch
  * What's Single dynamic dispatch?
    * Single ones use just one parameter to select a method
  * Make an example
    ```C#
    class SurveyBase{ public virtual void DoSurvey(){...} } 
    class Survey : SurveyBase{ public override void DoSurvey() {...} } 
    /*****************************Client Code**************************************/ 
    SurveyBase base = new Survey(); 
    base.DoSurvey(); // Survey.DoSurvey will be called
    ```

##### Multiple dynamic dispatch
  * What's Multiple dynamic Dispatch?
      * The multiple ones can take advantage of as many parameters they want
  * Make an example
    ```C#
    //classes
    interface IBar {} 
    class Bar : IBar {} 
    sealed class FooBar : Bar {} 
    //methods
    void Print(IBar item){Console.WriteLine("It is an IBar");} 
    void Print(Bar item){Console.WriteLine("It is a Bar");} 
    void Print(FooBar item){Console.WriteLine("It is a FooBar");}
    //call methods, 
    var bar = new Bar();
    var foo = new FooBar();
    IBar ibar = new FooBar();
    IBar[] items = { bar, foo, ibar };

    foreach (var item in items) 
    { 
      Print(item); 
    }
    foreach (dynamic item in items) 
    { 
      ConsolePrinter.Print(item);
    }
    ```
    Output:
    ```
    It is an IBar.
    It is an IBar.
    It is an IBar.

    It is an IBar.
    It is a FooBar.
    It is a FooBar.
    ```
### Method Hiding and Overriding
  * What's Method Hiding?
    * Method hiding means Subclass has defined a class method with the same signature as a class method in the superclass. In that case, the method of the superclass is hidden by the subclass.
  * What's Method Overriding?
    * The ability of a subclass to override a method allows a class to inherit from a superclass whose behavior is "close enough" and then to modify behavior as needed.
