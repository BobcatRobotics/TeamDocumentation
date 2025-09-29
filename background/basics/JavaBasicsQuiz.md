# Quiz: Java Basics

Test your knowledge of fundamental Java concepts!

Online Version is available here : https://forms.gle/DKoq1KXxiRiRhA4LA 

------------------------------------------------------------------------

# Java Basics Quiz

Test your knowledge of Java fundamentals with these questions!

---

## Multiple Choice

1. Which of the following is **not** a valid Java data type?  
   a) int  
   b) boolean  
   c) string  
   d) double  

2. Which of the following is a valid way to start a Java program?  
   a) `void main(String args)`  
   b) `public static void main(String[] args)`  
   c) `main()`  
   d) `start(String[] args)`  

3. What does the `static` keyword in Java mean?  
   a) The member belongs to the object instance  
   b) The member belongs to the class itself  
   c) The member cannot be changed  
   d) The member is private by default  

4. Which of the following is true about a `static` variable?  
   a) Each object has its own copy  
   b) It is shared among all instances of the class  
   c) It cannot be changed once assigned  
   d) It must be declared as `final`  

5. Which of these **cannot** be done in a `static` method?  
   a) Call another static method  
   b) Access a static variable  
   c) Access a non-static instance variable directly  
   d) Be called without creating an object  

6. What is a **static block** used for?  
   a) Initializing instance variables  
   b) Initializing static variables when the class is loaded  
   c) Declaring methods  
   d) Creating new objects  

7. Which of the following correctly calls a static method `display()` from class `Demo`?  
   a) `Demo obj = new Demo(); obj.display();`  
   b) `Demo.display();`  
   c) `display();`  
   d) `new Demo.display();`  
1. Which of the following is **not** a type of comment in Java?  
   a) Single-line comment  
   b) Multi-line comment  
   c) Documentation (Javadoc) comment  
   d) Inline XML comment  

2. What symbol is used to start a single-line comment in Java?  
   a) `/*`  
   b) `//`  
   c) `#`  
   d) `<!--`  

3. Which type of comment can be used to temporarily disable a block of code?  
   a) Single-line comment  
   b) Multi-line comment  
   c) Documentation comment  
   d) Inline comment  

4. What tool uses Javadoc comments to generate documentation?  
   a) `javac`  
   b) `javadoc`  
   c) `java`  
   d) `javap`  

5. Where are Javadoc comments typically placed?  
   a) Above methods, classes, and fields  
   b) At the end of the program  
   c) Inside the `main` method only  
   d) Between import statements  
1. What is the result of `7 % 3`?  
   a) 0  
   b) 1  
   c) 2  
   d) 3  

2. Which shorthand operator would you use to multiply a variable `a` by 3?  
   a) `a =* 3;`  
   b) `a *= 3;`  
   c) `a = a x 3;`  
   d) `a => 3;`  

3. What will the following code output?  
   ```java
   int counter = 5;
   counter++;
   System.out.println(counter);
   ```  
   a) 4  
   b) 5  
   c) 6  
   d) Error  

4. Which method of the `Math` class returns the larger of two values?  
   a) `Math.max(a, b)`  
   b) `Math.min(a, b)`  
   c) `Math.abs(a)`  
   d) `Math.pow(a, b)`  

5. What happens when you divide two integers in Java (e.g., `7 / 2`)?  
   a) It always produces a decimal  
   b) It truncates the decimal part (result = 3)  
   c) It rounds to the nearest whole number  
   d) It throws an error  

1. What is the main purpose of methods in Java?  
   a) To store data values  
   a) To perform specific tasks in reusable blocks of code  
   a) To define variables  
   a) To create loops  

2. Which of the following correctly declares a method that returns an integer?  
   a) `public void addNumbers(int a, int b) { return a + b; }`  
   a) `public int addNumbers(int a, int b) { return a + b; }`  
   a) `int addNumbers(a, b) { return a + b; }`  
   a) `public addNumbers(int a, int b) -> int { return a + b; }`  

---

3. How do you call a method in Java?  
   a) `call addNumbers(5, 3);`  
   a) `int result = addNumbers(5, 3);`  
   a) `addNumbers : 5, 3;`  
   a) `method addNumbers(5, 3)`  

---

4. What keyword is used when a method should return no value?  
   a) `null`  
   a) `empty`  
   a) `void`  
   a) `none`  
---

## True/False

8. Java is case-sensitive.  
9. A constructor must have the same name as the class.  
10. In Java, arrays can change size after they are created.  
11. The `final` keyword can be used to declare constants.  
12. Java supports multiple inheritance for classes.  
13. A `static` variable is initialized once and shared across all objects.  
14. Static methods can directly access instance (non-static) variables.  
15. A static nested class can be created without an instance of the outer class.  
16. You can overload static methods in Java.  
17. Static methods can be overridden in Java.  
6. Comments in Java are executed by the compiler.  
7. Single-line comments can be written after a line of code.  
8. Multi-line comments must always start with `/**` and end with `*/`.  
9. Documentation comments can include tags like `@param` and `@return`.  
10. Good practice is to comment on **why** code is written, not just **what** it does.  
6. A variable in Java must always be given a value when it is declared.  
7. Reference types in Java are used to store objects or complex data.  
8. You can update the value of a `final` variable after it has been assigned.  
9. Variable names in Java are case-sensitive.  
10. The type of a variable determines what kind of values it can store.  
6. The operator `%` gives the remainder of a division.  
7. `counter--` is equivalent to `counter = counter - 1`.  
8. `Math.sqrt(25)` will return `4`.  
9. Casting is sometimes required when dividing integers to preserve decimals.  
10. `Math.round(3.6)` returns `4`.  
10. The `void` keyword means that a method does not return a value.  

---

## Short Answer

18. What is the difference between `==` and `.equals()` when comparing Strings in Java?  

19. Write the correct syntax to declare an integer variable named `count` and initialize it to 10.  

20. What is the purpose of the `import` statement in Java?  

21. Explain what the term "object-oriented programming" means in the context of Java.  

22. Write a simple `if` statement that prints `"Hello"` if the variable `x` is greater than 5.  

23. Explain why you cannot directly access instance variables inside a static method.  

24. Write a short example of a class with a static variable `count` that increments every time the constructor is called.  

25. What is the difference between a static method and a non-static method?  

26. Why might you use a static block in a Java class?  

27. How do you call a static variable named `maxScore` inside a class `Game`?  

13. Why is `int 123speed;` an invalid variable declaration?  

14. Rewrite the following variable declaration to follow Java naming best practices:  
   ```java
   int RSpeed = 100;
   ```

11. Write a line of Java code that increases `speed` by 5 using a shorthand operator.  

12. What is the difference between `Math.floor(3.7)` and `Math.ceil(3.7)`?  

13. Why does `int result = 7 / 2;` store the value `3` instead of `3.5`?  

14. Give an example of when you would use `Math.abs(x)` in a robot program.  

15. What is the purpose of using intermediate variables in calculations?  

---

## Bonus Challenge

16. Write a small Java method called `square` that takes an integer as input and returns its square.  

16. Write a Java program with a class `Calculator` that has:  
   - A static method `add(int a, int b)` returning the sum  
   - A static variable `operationsCount` that increases every time `add` is called  
   - A `main` method that calls `add` multiple times and prints the number of operations performed.  
