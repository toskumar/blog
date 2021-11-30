### Variables

* __Variable__ is a name of memory location. There are three types of variables in java local, instance and static.

```java
class Variable {

  int a = 10; //instance variable
  static int b = 20; // static variable

  public static void main(String args[]) {
     int c = 20; //local variable;
     
     System.out.println("Instance variable a =  " + a);
     System.out.println("Static variable b " + b);
     System.out.println("Local variable c = " + c);
  }
}
```