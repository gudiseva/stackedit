## Java Interview Questions and Answers

Q. Difference ArrayList and LinkedList

Q. Difference Class and Object

Q. Difference Static and Instance Variables

Q. Difference Functional and Object Oriented Programming


 

Q. Generics - bonding reqd

Q. Collections

Q. Set internals

### OOPS Concepts
Q. Inheritance (Is A relationship)
E.g. Animal Class -> Dog Class; Cat Class

Q. Abstract Class
 - We cannot create an instance
 - Can provide functionality that needs to be extended
 - Sub Classes should provide implementation for the abstract methods

Q. Interface
 - Shares the common responsibility
 - Is used when 2 or more Classes perform the common action
 - Methods in an Interface do not provide implementation
 - Classes that implement the Interface should make the Methods public that are implemented

Q. Polymorphism
For Class
Animal animal = new Dog();
Animal animal = new Cat();
animal.bark();

For Interface
interface Flyable {
 void fly();
 }
class Aeroplane implements Flyable { ... }
class Bird implements Flyable { ... }
Flyable flyable = new Aeroplane();
Flyable flyable = new Bird();
flyable.fly();

Q. Encapsulation
 - Data and the Methods that act on the data are encapsulated, i.e. they are together defined in a Blueprint (i.e. Class)

Q. Coupling
 - It is a measure of how much a Class is dependent on other Classes
 - There should be minimal dependencies between Classes

Q. Cohesion
 - It is a measure of how related the responsibilities of a Class are
 - E.g. This Class is downloading from Internet, parsing data, and storing data to 
 - The responsibilities of this Class are not really related.  This is not Cohesion.

Q. SOLID Principles
1. Single Responsibility Principle
	a. Class - A Class should have one and only one reason to change
	b. Method - A Method should do related things.  A Method should be at a high level or low level

2. Open / Closed Principle (OCP)
	- Software entities should be open for extension but closed for modification
	- E.g. Area of Rectangle and Circle

3. Liskov Substitution Principle (LSP)
	- Subtypes must be substitutable for their base types
	- A Subclass may override a parent method only under certain conditions:
		- Preconditions can only be weaker
		- Postconditions can only be stronger
	- E.g. Rectanlge and Square -> Width and Height

4. Interface Segregation Principle (ISP)

<!--stackedit_data:
eyJoaXN0b3J5IjpbMTQ1MDgxMzg3MSwzMTcxMDA0NzEsLTYyMD
M2NDc4OSwxNjMwMDczODQ5XX0=
-->