# **Singleton is an anti-pattern**
This document presents a study that reveals Singleton design pattern is actually an anti-pattern.

## **Introduction**

Java is an object-oriented language and has a  number of design patterns to design and  meet the business requirements. Design patterns are the ways that help the developer deceide how to design and document his/her code efficiently namely; Singlteon pattern , Decorator  pattern, Null Object pattern,etc. Out of these, Singleton is undoubtedly the most famous and most used patterns in programming world. Singleton design pattern is a pattern that allows the programmer to restrict the class instantiation to one and provide a global point of access.Singlteon pattern basically implements a very simple strategy, “If a class instance does not exist; create a new instance else return the same instance each time an isntance is requested”. The following example presents a basic scenario of using Singleton

```
public class SingletonDemo{                                                           

  private static SingletonDemo instance  = null;              

  private SingletonDemo(){}                                            

  public static SingletonDemo getInstance(){        

    if(instance == null){                                                                    
      instance = new SingletonDemo();
    }                              

    return instance;           
  }
}
 ```

A very common use of implementing Singletons is use of Logging or interacting with the database maitaining a single database connection in day-to-day project work. Using Singleton in this scenario allows us to create a single instance of logger whenever we want to log something. As well said, everything acts as boon as well as bane. Similarly, over the course of time, Singleton design pattern has undergone a lot of dis-couragement and is now considered as an ti-pattern . Following are the resons why Singleton is considered as an anti-pattern:

1. Singletons are basically used as global variables. Using global variables is an enemy of encapsulation because using global variables it becomes difficult to define pre and post conditions for the client’s object interface, because working of the interface can be handled from within and  not from outside the interface.
1. Use of Singletons make it difficult to unit test the classes because for unit testing,classes must be loosely coupled allowing classes to be tested individually
1. Singletons break the single responsibility principle because when unit testing two classes,one implementing Singleton and other not,we need to pass in the Singleton as a parameter to the constructor,allowing tester to mock out the singleton class easily.The singleton then does not has to enforce its own singularity, this can be done by factory class eliminating the global state.
1. Singletons are bad when used with multi-threading because with just a single object, the options of threading are limited.
1. Singletons make it easy to break stuff File System is usually implemented as a singleton and mostly all the file operations are performed under a single method. However, bounding the team to use just a common method to implement File operations makes it very difficult to implement.
1. Singletons decrease performance If we have a number of lazy-initialized singletons, the compiler cannot fold  multiple SingletonDemo.getInstance() calls into one. This is because,each call to getInstance()  will cause a branch instruction and possibly a cache mismatch.
1. Singletons promote tight coupling between classes Singletons tightly couples the code to the exact object type and removes the scope of polymorphism.
1. Singletons does not complete what they are meant to do because a number of techniques; namely Java Reflection , Serialization, etc. are available to create more than one instances of a singleton class
1. Using static method to initialize singleton objects is considered a good approach implementing Singleton. But, this approach forces the programmer to know the internal code structure of the class as static methods can be inoked only on class names. Moreover, unit testing static methods is not an easy task using simple mockito frameworks.
1. In agile world, we need to unit test even a very single functionality . One of the most important things about these unit tests is that these nust be independent of each other making it difficult to implement with singletons.
1. Extending Singletons is not easy. Programmer needs to use some kind of decorator pattern to change the behavior.
1. In a garbage collected system, singletons can become very hard with regard to memory management.
1. Singletons can’t be used with clustering.


Comments:
```
Nice arguments, I tend to agree with them. But you need synchronized & volatile 
for correct multi-threading correctness. 
 ```
