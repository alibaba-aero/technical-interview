# .NET

* Common Language Runtime
  * Provides essential runtime services such as automatic memory management and exception handling
  * The word common refers to the fact that the same runtime can be shared by other managed
      programming languages, such as F#, Visual Basic, and Managed C++
  * C# is called a managed language because it compiles source code into managed code,
      which is represented in Intermediate Language (IL)
  * The CLR converts the IL into the native code of the machine, such as X86 or X64,
      usually just prior to execution. This is referred to as Just-In-Time (JIT) compilation
  * The container for managed code is called an assembly. An assembly contains not only IL,
      but type information (metadata)
* Frameworks and Base Class Libraries
  * The Base Class Libraries (BCL) sit atop the CLR, providing features useful to any kind of application
      (such as collections, XML/JSON, input/output [I/O], networking, serialization, and parallel programming)
  * Sitting atop the BCL are application framework layers, which provide the APIs for a user interface
      paradigm (such as ASP.NET Core for a web application, or Windows Presentation Foundation
      [WPF] for a rich-client application)

    ![The Framework Architecture Diagram](./../../../images/framework-architecture.png)

  * .NET Standard is not a framework; it’s merely a specification describing a minimum baseline of functionality
      (types and members) that guarantees compatibility with a certain set of frameworks. The concept is similar
      to C# interfaces: .NET Standard is like an interface that concrete types (frameworks) can implement.
    * Reference Assemblies
* Value Types
  * All numeric types, the char type, and the bool type as well as custom struct and enum types
  * The content of a value-type variable or constant is simply a value
  * The assignment of a value-type instance always copies the instance
  * Value-type instances occupy precisely the memory required to store their fields
  * Value-type instances (and object references) live wherever the variable was declared. If the instance
      was declared as a field within a class type, or as an array element, that instance lives on the heap and
      if it appears as a parameter or local variable, it will reside on the stack
* Reference Types
  * All class, array, delegate, and interface types and string type
  * Having two parts
    * An object
    * The reference to that object
  * Assigning a reference-type variable copies the reference, not the object instance
  * Require separate allocations of memory for the reference and object. The object consumes as many bytes
      as its fields, plus additional administrative overhead. The precise overhead is intrinsically private to
      the implementation of the .NET runtime, but at minimum, the overhead is eight bytes, used to store a key
      to the object’s type as well as temporary information such as its lock state for multithreading and a flag
      to indicate whether it has been fixed from movement by the garbage collector. Each reference to an object
      requires an extra four or eight bytes, depending on whether the .NET runtime is running on a 32- or 64-bit
      platform
* double Versus decimal
  * double is useful for scientific computations (such as computing spatial coordinates)
    * float and double internally represent numbers in base 2. For this reason, only numbers expressible
        in base 2 are represented precisely
  * decimal is useful for financial computations and values that are man-made rather than the result of
      real-world measurements
    * decimal works in base 10
* Although a Boolean value requires only one bit of storage, the runtime will use one byte of memory because
    this is the minimum chunk that the runtime and processor can efficiently work with. To avoid space
    inefficiency in the case of arrays, .NET provides a BitArray class in the System.Collections namespace
    that is designed to use just one bit per Boolean value
* C#’s char type (aliasing the System.Char type) represents a Unicode character and occupies 2 bytes (UTF-16)
* The elements in an array are always stored in a contiguous block of memory, providing highly efficient access
* Stack
  * The stack is a block of memory for storing local variables and parameters. The stack logically grows and
      shrinks as a method or function is entered and exited
* Heap
  * The heap is the memory in which objects (i.e., reference-type instances) reside
  * The heap also stores static fields
* The in modifier
  * An in parameter is similar to a ref parameter except that the argument’s value cannot modified by the
      method (doing so generates a compile-time error). This modifier is most useful when passing a large value
      type to the method because it allows the compiler to avoid the overhead of copying the argument prior to
      passing it in while still protecting the original value from modification
* Local method
  * Is visible only to the enclosing method
  * A benefit of local methods is that they can access the local variables and parameters of the enclosing method
  * Can appear within other function kinds, such as property accessors, constructors, or inside other local
      methods, and inside lambda expressions that use a statement block. Local methods can be iterators
      or asynchronous
* CLR property implementation
  * C# property accessors internally compile to methods called get_XXX and set_XXX
* CLR indexer implementation
  * Indexers internally compile to methods called get_Item and set_Item
* new versus override

  ```csharp
  public class BaseClass 
  {
    public virtual void Foo()
    { 
      Console.WriteLine ("BaseClass.Foo");
    }
  }
  
  public class Overrider : BaseClass
  {
    public override void Foo()
    {
      Console.WriteLine ("Overrider.Foo");
    }
  }
  
  public class Hider : BaseClass
  {
    public new void Foo()
    { 
      Console.WriteLine ("Hider.Foo");
    }
  }

  Overrider over = new Overrider();
  BaseClass b1 = over;
  over.Foo();             // Overrider.Foo
  b1.Foo();               // Overrider.Foo
  
  Hider h = new Hider();
  BaseClass b2 = h;
  h.Foo();                // Hider.Foo
  b2.Foo();               // BaseClass.Foo
  ```

* Constructor and field initialization order
    1. From subclass to base class
        1. Fields are initialized
        2. Arguments to base-class constructor calls are evaluated
    2. From base class to subclass
        1. Constructor bodies execute
* Copying semantics of boxing and unboxing
  * Boxing copies the value-type instance into the new object, and unboxing copies the contents of the object
      back into a value-type instance. In the following example, changing the value of i doesn’t change
      its previously boxed copy:

    ```csharp
    int i = 3;
    object boxed = i;
    i = 5;
    Console.WriteLine (boxed); // 3
    ```
* GetType Method vs typeof Operator
* Struct
  * A struct is a value type, whereas a class is a reference type
  * A struct does not support inheritance (other than implicitly deriving from object, or more precisely,
      System.ValueType)
  * A struct is appropriate when value-type semantics are desirable
  * A struct can have all of the members that a class can, except the following
    * A parameterless constructor
    * Field initializers
    * A finalizer
    * Virtual or protected members
  * Converting a struct to an interface causes boxing. Calling an implicitly implemented member on a struct
      does not cause boxing:

    ```csharp
    interface I { void Foo();
    }
    struct S : I { public void Foo() {} } ...
    S s = new S();
    s.Foo(); // No boxing.
    I i = s; // Box occurs when casting to interface.
    i.Foo();
    ```

  * Ref Structs
    * To ensure that it can only ever reside on the stack
    * Introduced mainly for the benefit of the Span<T> and ReadOnly Span<T> structs
    * Ref structs cannot partake in any C# feature that directly or indirectly introduces the possibility
        of existing on the heap
      * Lambda expressions
      * iterators
      * asynchronous functions
      * Cannot appear inside non-ref structs
      * Cannot implement interfaces (because this could result in boxing)
* Friend Assemblies
  * Expose internal members to other friend assemblies
* Reimplementing an Interface in a Subclass

  ```csharp
  public interface IUndoable { void Undo(); }
  public class TextBox : IUndoable {
  void IUndoable.Undo() => Console.WriteLine ("TextBox.Undo"); }
  public class RichTextBox : TextBox, IUndoable {
  public void Undo() => Console.WriteLine ("RichTextBox.Undo"); }

  RichTextBox r = new RichTextBox();
  r.Undo();// RichTextBox.Undo
  ((IUndoable)r).Undo();   // RichTextBox.Undo
  ```

  Assuming the same RichTextBox definition, suppose that TextBox implemented Undo implicitly:

  ```csharp
  public class TextBox : IUndoable {
  public void Undo() => Console.WriteLine ("TextBox.Undo"); }

  RichTextBox r = new RichTextBox();
  r.Undo();// RichTextBox.Undo
  ((IUndoable)r).Undo();// RichTextBox.Undo
  ((TextBox)r).Undo();// TextBox.Undo
    
  ```

* Enum Type-Safety Issues
  * Use `Enum.IsDefined`
* Generic
  * Avoid casting and boxing
  * Open generic types do not exist at runtime: open generic types are closed as part of compilation
      (see  also [Generics in the Run Time](https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/generics/generics-in-the-run-time))
  * Static data is unique for each closed type
  * Constraints

    ```csharp
    where T : base-class // Base-class constraint
    where T : interface    // Interface constraint
    where T : class  // Reference-type constraint
    where T : class?  // Nullable Reference-type constraint
    where T : struct  // Value-type constraint (excludes Nullable types)
    where T : unmanaged // Unmanaged constraint
    where T : new() // Parameterless constructor constraint
    where U : T // Naked type constraint
    where T : notnull // Non-nullable value type, or from C# 8 
                      // a non-nullable reference type.
    ```

  * Covariance
    * Assuming A is convertible to B, X has a covariant type parameter if `X<A>` is convertible to `X<B>`
        (convertible via an implicit reference conversion— such as A subclassing B, or A implementing B)
    * For instance, type IFoo<T> has a covariant T if the following is legal:

      ```csharp
        IFoo<string> s = ...;
        IFoo<object> b = s;
      ```

    * Interfaces and delegates permit covariant type parameters, but classes do not because a class can implement
        both Covariance and Contravariance interfaces
    * B[] can be cast to A[] if B subclasses A (and both are reference types)

        ```csharp
        Bear[] bears = new Bear[3];
        Animal[] animals = bears;  // OK
        ```

      The downside of this reusability is that element assignments can fail at runtime:

        ```csharp
        animals[0] = new Camel(); // Runtime error
        ```

    * Declaring a covariant type parameter
      * Type parameters on interfaces and delegates can be declared covariant by marking them with
          the `out` modifier
      * Ensures that, unlike with arrays, covariant type parameters are fully type-safe
      * The out modifier on `T` indicates that `T` is used only in output positions
          (e.g., return types for methods)
      * The compiler will generate an error if you use a covariant type parameter in an input position
          (e.g., a parameter to a method or a writable property)

        ```csharp
          public interface IPoppable<out T> { T Pop(); }
          var bears = new Stack<Bear>();
          bears.Push (new Bear());
          // Bears implements IPoppable<Bear>. We can convert to IPoppable<Animal>:
          IPoppable<Animal> animals = bears; // Legal
          Animal a = animals.Pop();
        ```

  * Contravariance
    * assuming that A allows an implicit reference conversion to B, Contravariance is when you can convert
        in the reverse direction—from `X<B>` to `X<A>`
    * Is supported if the type parameter appears only in input positions and is designated with the `in` modifier

        ```csharp
          public interface IPushable<in T> { void Push (T obj); }
          IPushable<Animal> animals = new Stack<Animal>();
          IPushable<Bear> bears = animals; // Legal
          bears.Push (new Bear());
        ```
* Delegate
  * Parameter compatibility

      When you call a method, you can supply arguments that have more specific types than the parameters
      of that method. This is ordinary polymorphic behavior. For the same reason, a delegate can have more
      specific parameter types than its method target. This is called *Contravariance*:

      ```csharp
      delegate void StringAction(string s);
      class Test
      {
          static void Main()
          {
              StringAction sa = new StringAction(ActOnObject); sa("hello");
          }
          static void ActOnObject(object o) => Console.WriteLine(o); // hello
      }
      ```

  * Return type compatibility

      If you call a method, you might get back a type that is more specific than what you asked for.
      This is ordinary polymorphic behavior. For the same reason, a delegate’s target method might return
        a more specific type than described by the delegate. This is called *Covariance*:

      ```csharp
      delegate object ObjectRetriever();
      class Test
      {
          static void Main()
          {
              ObjectRetriever o = new ObjectRetriever(RetrieveString);
              object result = o();
              Console.WriteLine(result);  // hello 
          }
          static string RetrieveString() => "hello";
      }
      ```
  
  * Generic delegate type

      ```csharp
      delegate TResult Func<out TResult>();
      // allowing:
      Func<string> x = ...; 
      Func<object> y = x;

      delegate void Action<in T> (T arg);
      // allowing:
      Action<object> x = ...;
      Action<string> y = x;
      ```

* Events

  * Three things happen under the hood when you declare an event as follows:

      ```csharp
      public class Broadcaster
      {
          public event PriceChangedHandler PriceChanged;
      }
      ```

    * First, the compiler translates the event declaration into something close to the following:

      ```csharp
      PriceChangedHandler priceChanged; // private delegate
      public event PriceChangedHandler PriceChanged
      {
          add { priceChanged += value; }
          remove { priceChanged -= value; }
      }
      ```

    * Second, the compiler looks within the Broadcaster class for references to PriceChanged that perform operations
        other than += or -=, and redirects them to the underlying priceChanged delegate field.

    * Third, the compiler translates += and -= operations on the event to calls to the event’s add and remove
        accessors.
  * If remove the *event* keyword and use *PriceChanged* as a delegate, subscribers could do the following
    * Replace other subscribers by reassigning PriceChanged (instead of using the += operator).
    * Clear all subscribers (by setting PriceChanged to null).
    * Broadcast to other subscribers by invoking the delegate.
  * Standard Event Pattern
* Lambda Expressions
  * The compiler immediately converts the lambda expression to either of the following:
    * A delegate instance
    * An expression tree, of type Expression<TDelegate>, representing the code inside the lambda expression
        in a traversable object model. This allows the lambda expression to be interpreted later at runtime
  * Internally, the compiler resolves lambda expressions of this type by writing a private method and then
        moving the expression’s code into that method:

    ```csharp
    delegate int Transformer (int i);
    Transformer sqr = x => x * x;
    Console.WriteLine (sqr(3)); // 9
    ```
  
  * A lambda expression that captures variables is called a *Closure*
  * Outer variables referenced by a lambda expression are called *captured variables*
  * Captured variables are evaluated when the delegate is actually invoked,
      not when the variables were captured

    ```csharp
    int factor = 2;
    Func<int, int> multiplier = n => n * factor; factor = 10;
    Console.WriteLine(multiplier(3));  // 30
    ```

  * Lambda expressions can themselves update captured variables

    ```csharp
    int seed = 0;
    Func<int> natural = () => seed++;
    Console.WriteLine(natural());// 0 
    Console.WriteLine(natural());// 1 
    Console.WriteLine(seed);// 2 
    ```
  
  * A local variable instantiated within a lambda expression is unique per invocation of the delegate instance
  * Capturing is internally implemented by “hoisting” the captured variables into fields of a private class.
      When the method is called, the class is instantiated and lifetime-bound to the delegate instance
  * Capturing iteration variables
  * Lambda Expressions Versus Local Methods
  * Anonymous and local methods capture outer variables in the same way lambda expressions do
* try Statements and Exceptions
  * Checking for preventable errors is preferable to relying on try/catch blocks because exceptions are
      relatively expensive to handle, taking hundreds of clock cycles or more
  * Exception filters
  * The finally Block
  * The using statement
  * If we replaced throw with throw ex, the example would still work, but the StackTrace property of the
      newly propagated exception would no longer reflect the original error.
* Enumeration and Iterators
  * The compiler converts iterator methods into private classes that implement `IEnumerable<T>`
      and/or `IEnumerator<T>`. The logic within the iterator block is “inverted” and spliced into the MoveNext
      method and Current property on the compilerwritten enumerator class. This means that when you call an
      iterator method, all you’re doing is instantiating the compilerwritten class; none of your code actually
      runs! Your code runs only when you start enumerating over the resultant sequence, typically with a
      foreach statement.
  * `yield break` and `yield return`
  * A `yield return` statement cannot appear in a try block that has a catch clause Nor can yield return appear
      in a catch or finally block.
    * These restrictions are due to the fact that the compiler must translate iterators into ordinary classes
        with MoveNext, Current, and Dispose members, and translating exception handling blocks would create
        excessive complexity
* The Array Class
* `Nullable<T>` Struct
  * Operator Lifting
    * Equality operators
    * Relational operators
* Nullable Reference Types
* Extension Methods
* Anonymous Types
* Tuple and ValueTuple
* Patterns
  * Property Patterns
  * Tuple Patterns
  * Positional Patterns
  * `var` Patterns
  * Constant Patterns
* Caller Info Attributes
  * CallerMemberName
  * CallerFilePath
  * CallerLineNumber
* Dynamic Binding
* Unsafe Code and Pointers
  * Pointer types are primarily useful for interoperability with C APIs, but you also can use them for
      accessing memory outside the managed heap or for performance-critical hotspots
  * The `stackalloc` Keyword
* Preprocessor Directives
  * Conditional Attributes
* Comparing Strings
  * Equality comparison
  * order comparison
    * Ordinal versus culture comparison
* StringBuilder
* Text Encodings and Unicode
* Dates and Times
  * TimeSpan
  * DateTime and DateTimeOffset
  * Time Zones
  * Alternatives
* BigInteger
* Complex
* Random
* The Guid Struct
* Standard Equality Protocols
  * == and !=
  * The virtual object.Equals method
  * The static object.Equals method
  * The static object.ReferenceEquals method
  * The IEquatable<T> interface
  * When Equals and == are not equal
  * Overriding GetHashCode
  * Overriding Equals
* Collections
  * BitArray
  * HashSet<T> and SortedSet<T>
  * Dictionaries
  * EqualityComparer<T>
* LINQ Query
  * The compiler processes a *Query Expression* by translating it into fluent syntax. It does this in a fairly
      mechanical fashion—much like it translates foreach statements into calls to GetEnumerator and MoveNext.
      This means that anything you can write in query syntax you can also write in fluent syntax
  * Deferred Execution
    * How Deferred Execution Works
    * Captured Variables
  * Subqueries
    * Subqueries and Deferred Execution
  * Interpreted Queries
* Expression Trees
  * The Expression DOM
* Garbage Collection and Memory Consumption
  * Finalizers
  * How the GC Works
    * Generational collection
    * The Large Object Heap
    * Workstation versus server collection
    * Background collection
    * Memory Pressure
    * Array Pooling
    * Sync vs Async resource release (await using vs using) eg: DisposeAsync
  * Managed Memory Leaks
    * Timers
    * Event handlers and Weak References
* Cross-Platform Diagnostics Tools
  * dotnet-counters
  * dotnet-trace
  * dotnet-dump
* Concurrency and Asynchrony
  * On a single-core computer, the operating system must allocate “slices” of time to each thread
      (typically 20 ms in Windows) to simulate concurrency, resulting in repeated blocks of x and y.
      On a multicore or multiprocessor machine, the two threads can genuinely execute in parallel
      (subject to competition by other active processes on the computer), although you still get
      repeated blocks of x and y in this example because of subtleties in the mechanism by which
      Console handles concurrent requests
  * Thread.Sleep(0) relinquishes the thread’s current time slice immediately, voluntarily handing over the
      CPU to other threads. Thread.Yield() does the same thing except that it relinquishes only to threads
      running on the same processor.
  * Blocking
    * I/O-bound versus compute-bound
    * Blocking versus spinning
  * Local versus Shared State
  * Passing Data to a Thread
    * Lambda expressions and captured variables
  * Exception Handling
    * Centralized exception handling
  * Foreground versus Background Threads
  * Signaling
  * Synchronization Contexts
  * The Thread Pool
    * Hygiene in the thread pool
  * Tasks
    * Long-running tasks
    * The CLR wraps the exception in an AggregateException in order to play well with parallel programming
        scenarios
    * awaiter.GetResult() vs .Result
    * TaskCompletionSource
    * Task.Delay is the asynchronous equivalent of Thread.Sleep
    * Awaiting
      * Upon encountering an await expression, execution (normally) returns to the caller—rather like with yield
          return in an iterator. But before returning, the runtime attaches a continuation to the awaited task,
          ensuring that when the task completes, execution jumps back into the method and continues where it left
          off. If the task faults, its exception is rethrown, otherwise its return value is assigned to the
          await expression
      * Capturing local state
    * Asynchronous call graph execution
    * `ValueTask<T>`
      * Precautions
    * `ConfigureAwait(false)`
    * Cancellation
* Stream Architecture
  * Backing stores
  * Decorators
  * Adapters

  ![The Stream Architecture Diagram](./../../../images/stream-architecture.png)

  * PipeStream
  * Named pipes
