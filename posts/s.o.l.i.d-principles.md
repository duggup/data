![bob-is-watching-you](https://miro.medium.com/max/1400/1*LEpaMXyU_0qC5IG_z0V2IQ.jpeg)

This has to be one of the few questions you would hear in an interview. But there obviously you'll have only 5 minutes to prove that you know this.

*I’m here to make you sure that you've got this!*

**SOLID** is one of the most important acronyms in the world of Object-Oriented Programming.
> Why should you care about SOLID programming?

First of all, you have to realize you are not going to be forever where you are. If we use standards and well-known architectures, we can be sure that our code will be easy to maintain by other developers that come after us, and I’m sure you wouldn’t want to deal with the task of fixing a code that didn’t apply any known methodology as it would be very hard to understand it.

Let's jump right in.
![I know you’ve been waiting!](https://cdn-images-1.medium.com/max/2000/1*aPcGEHIbYlL_lj2KqQodqQ.gif)*I know you’ve been waiting!*

## What does SOLID stand for?

 1. **S** — Single Responsibility Principle.
 2. **O** — Open Closed Principle.
 3. **L** — Liskov Substitution Principle.
 4. **I** — Interface Segregation Principle.
 5. **D** — Dependency Inversion Principle.

## **S**ingle **R**esponsibility **P**rinciple:
> A class should have only one reason to change.

As its name suggests, this principle implies that a class/module must do only **one** thing, have only **one** responsibility. If our class does more than one thing, then we should **split** the functionalities into different classes.

In the context of the Single Responsibility Principle (SRP), we define **responsibility** as “a reason for change”. If you can think of more than one motive for changing a class, then that class has more than one responsibility.

Example. Let's suppose we have a `Phone` which has different functions like Calling, Messaging, Calculator, FlashLight, etc. Now when we define this class, we’ll have one `Phone.java` file, which will contain all the functions. Now, this class violates the SRP Principle as this class has been assigned multiple responsibilities. To make the class stop violating the principle, we should define the responsibilities in separate classes like `Calling.java`, `Messaging.java`, `Calculator.java`, thus making short components/classes and dividing the responsibilities.

Android-specific Example: The method `onBindViewHolder` of the `RecyclerView` widget. The role of the `onBindViewHolder` is to map a list item to a view. There should be no logic in this method. So if there's any code that relates to the logic, you should probably remove from there.

## Open Closed Principle:
> Software entities (classes, modules, functions, etc.) should be open for extension, but closed for modification.

This basically means that we should add extension points in classes that implement requirements that are intrinsically unstable due to instability in the business domain and refactor parts of code and introduce additional extension points when these parts proved to be unstable.

Android-specific Example: Extending `RecyclerView.Adapter` class is easy and we can easily create custom adapters. Developers can easily extend this class and create their own custom adapter with custom behavior without modifying the existing `RecyclerView.Adapter` class.

Another Example: can be looking at Buttons, Switches, Checkboxes inherit all from `TextView` class. This means that `TextView` is open to extension but closed for modifications.

## Liskov Substitution Principle:
> Objects in a program should be replaceable with instances of their subtypes **without changing** the behaviour of that program.

This means that a subclass should override the methods from a parent class that does not break the functionality of the parent class.

Example. In mathematics, a `Square` is a `Rectangle`. Indeed it is a specialization of a rectangle. The “is a” makes you want to model this with inheritance. However if in code you made `Square` derive from `Rectangle`, then a `Square` should be used anywhere you expect a `Rectangle`. This makes for some strange behavior. Imagine you had `SetWidth` and `SetHeight` methods on your `Rectangle` base class; this seems perfectly logical. However, if your `Rectangle` reference pointed to a `Square`, then `SetWidth` and `SetHeight` do not make sense because setting one would change the other to match it. In this case, `Square` fails the Liskov Substitution Test with `Rectangle` and the abstraction of having `Square` inherit from `Rectangle` is a bad one.

Android-specific Example: We should write the custom RecyclerView adapter class in such a way that it still works with RecyclerView. We should not write something which will lead the RecyclerView to misbehave.

## Interface Segregation Principle:
> Classes that implement interfaces, should not be forced to implement methods they do not use.

This means that if an interface becomes too fat, then it should be split into smaller interfaces so that the client implementing the interface does not implement methods that are of no use to it.

ISP relates to important characteristics — **cohesion** and **coupling**.
 Ideally, your components must be highly tailored. It improves code robustness and maintainability.

Enforcing ISP gives you the following bonuses:

 - High **cohesion** — better understandability, robustness.
 - Low **coupling** — better maintainability, high resistance to changes.

Example. Again going to the previous example of `Phone`, if we have a public interface for the whole functionality, like this:

![](https://cdn-images-1.medium.com/max/2000/1*AcWeXzVuiihvWZh6wfHDAQ.png)

Now if you want to implement a Calculator, the functions `dial()`, `lightOn()` and `lightOff()` are useless. Thus we should refactor the code to something like this:

![](https://cdn-images-1.medium.com/max/2000/1*h8uEAJgOoVLeGBbAyZhZ_Q.png)

Now, the desired class can implement one or more interfaces according to wish. This is how we can prevent violating ISP.

## Dependency Inversion Principle
> High-level modules should not depend on low-level modules. Both should depend on abstractions.

and
> Abstractions should not depend on details. Details should depend on abstractions.

If you use a class inside another class, this class will be dependent on the class injected. The importance of DIP can be distilled down to a singular goal of being able to reuse software components that rely upon external dependencies for a portion of their functionality.

Example. If we have a class `Bank` that has the following code, the calling class of Bank is unaware of the `hidden dependencies`, thus this violates DIP.

![](https://cdn-images-1.medium.com/max/2000/1*mOmrwU876tOTMxtS9A7jwg.png)

On another hand, if we refactor the code to something like this:

![](https://cdn-images-1.medium.com/max/2000/1*5s8jAIg3mKVXNKZ3wUUwFQ.png)

In this case, we are letting the calling class of `Bank` aware of the dependencies involved, instead of letting the class itself create a dependency. This also helps in the case of testing!

## Conclusion:

The SOLID Principles, are some of the most important set of principles to learn and implement if you are following Object-Oriented Design. It may seem a bit overwhelming initially, but with practice and time, you will be coding based on these principles, without even realizing it. *(Copied from StackOverflow :D)*

![Yayyyy!](https://cdn-images-1.medium.com/max/2000/1*5cIdmPVsSvEZtOFLap34kw.gif)*Yayyyy!*

Enjoy! Happy coding!
