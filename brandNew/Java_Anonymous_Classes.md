Anonymous classes in Java are a special type of inner class without a name. They are used to create an instance of an object with certain "extras" such as overloading methods of a class or interface without having to actually subclass a class. 

- **Definition**: An anonymous class is defined and instantiated in a single concise expression using the `new` keyword.
- **Syntax**: The syntax of an anonymous class is similar to the declaration of a local inner class, except that it has no name. The class declaration and object creation are combined in one statement.
  
  ```java
  new ParentClassOrInterface() {
      // override methods and/or add new members
  }
  ```

- **Extending a class**: You can extend a class using an anonymous class by providing an implementation for one or more of its methods.

  ```java
  new Book("Design Patterns") {
      @Override
      public String description() {
          return "Famous GoF book.";
      }
  }
  ```

  If the parent class constructor requires parameters, they are passed within the parentheses.

- **Implementing an interface**: Anonymous classes are often used to provide quick and dirty implementations for interfaces, especially in graphical user interface (GUI) event handling or callbacks.

  ```java
  ActionListener actionListener = new ActionListener() {
      public void actionPerformed(ActionEvent e) {
          // handle action event
      }
  };
  ```

- **Use Cases**: Common use cases include event handling, such as in GUI applications, creating runnable objects for threads, or providing a one-off implementation for an interface or abstract class.
  
- **Limitations**:
  - They can only access final or effectively final variables from the enclosing scope.
  - They cannot have explicit constructors because they have no name.
  - They cannot have static initializers or member interfaces.
  - They are not reusable and cannot be instantiated again as they have no name.
  
- **Creating Instances**: To instantiate an anonymous class, you use the `new` keyword followed by the constructor of the superclass or the interface to implement, with curly braces containing any method overrides or implementations.

  ```java
  Thread thread = new Thread() {
      public void run() {
          System.out.println("Hello World");
      }
  };
  thread.start();
  ```

- **Best Practices**: While anonymous classes can be useful for quick and simple use cases, they can lead to less readable and maintainable code if overused. It's generally advisable to use them only when the class definition is short and will not be used elsewhere. 
- With the introduction of lambda expressions in Java 8, many use cases for anonymous classes can be replaced with more concise and readable lambda expressions, especially for interfaces with a single abstract method (SAM interfaces).

Remember, anonymous classes are a powerful tool, but they should be used judiciously to keep your code clean and maintainable.