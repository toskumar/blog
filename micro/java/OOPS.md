# OOPS

__Procedural Language__ is based on the concept of the procedure call. A procedure is a set of instruction which has one or more input parameters and output parameter.
```C
float areaOfCircle(int radius) {
  return 3.14 * radius * radius;
}
```
__Object Oriented Language__ is a programming style which uses objects that contain both data and methods.

__Encapsulation__ refers to the bundling of data and methods
```java
class Circle {
 int radius;
 Circle (int radius) {
  this.radius = radius;
 }
 int area() {
  return 3.14 * this.radius * this.radius 
 }
}
```
__Abstraction__ is a process of hiding certain details and showing only essential information to the user.
```java
abstract class Bike {
 Engine engine = new Engine();
 void start(){
  this.engine.start();
 }
 void stop() {
    this.engine.stop()
 }
 abstract void ride();
}
```
__Inheritance__ is a process of extending the features and behavior of one class to another class
```java
class MyBike extends Bike {
  Color color;
  Horn horn;
  MyBike() {
    this.color = new Color(BLACK);
    this.horn = new Horn(HONK);
  }
  void ride() {
    Sysout.out.println("I'm riding my bike");
  }
}
```
__polymorphism__ the ability of an object to take many forms eg., method overriding and method overloading
```java
class Printer {
   void print(Document doc) {
     //prints doc, docx, pdf and txt documents
   }
   void print(Scanned image) {
     //prints an image file png, jpeg
   }
}
```
### OOPS example
```java
public class MyDevice {
	public static void main(String arg[]) {
		Epson2010 e2010 = new Epson2010();
		e2010.model();
		e2010.print();

		Epson3010 e3010 = new Epson3010();
		e3010.model();
		e3010.print();
		e3010.scan();
		e3010.copy();
	}
}

abstract class Printer {
	abstract void print();
	abstract void model();
}

interface Scanner {
	abstract void scan();
}

interface Copier {
	abstract void copy();
}

abstract class SingleFunctionPrinter extends Printer {
	void print() {
		System.out.println("SingleFunctionPrinter printing ...");
	}
}

abstract class MultiFunctionPrinter extends Printer implements Scanner, Copier {
	void print() {
		System.out.println("MultiFunctionPrinter printing ...");
	}

	public void scan() {
		System.out.println("MultiFunctionPrinter scanning ...");
	}

	public void copy() {
		System.out.println("MultiFunctionPrinter copying ...");
	}
}

final class Epson2010 extends SingleFunctionPrinter {
	void model() {
		System.out.println("Category: SingleFunctionPrinter, Model: Epson Model 2010");
	}
}

final class Epson3010 extends MultiFunctionPrinter {
	void model() {
		System.out.println("Category: MultiFunctionPrinter, Model: Epson Model 3010");
	}
}

```
