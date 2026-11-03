# lab-sheet-06
Answers 
# FOUNDATION OF JAVA LAB SHEET – 6
## Topic: Exception Handling

### Part A – Easy / Basic Questions

### Q1. Handling ArithmeticException

**Program:**

```java
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        System.out.print("Enter first number: ");
        int a = sc.nextInt();

        System.out.print("Enter second number: ");
        int b = sc.nextInt();

        try {
            int result = a / b;
            System.out.println("Division = " + result);
        }
        catch (ArithmeticException e) {
            System.out.println("Error: Cannot divide by zero.");
        }

        sc.close();
    }
}
```

**Output:**
```text
Enter first number: 20
Enter second number: 0
Error: Cannot divide by zero.
```

### Q2. Handling ArrayIndexOutOfBoundsException

**Program:**

```java
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        int arr[] = {10, 20, 30, 40, 50};

        System.out.print("Enter array index (0-4): ");
        int index = sc.nextInt();

        try {
            System.out.println("Array element = " + arr[index]);
        }
        catch (ArrayIndexOutOfBoundsException e) {
            System.out.println("Error: Invalid array index.");
        }

        sc.close();
    }
}
```

**Output:**
```text
Enter array index (0-4): 2
Array element = 30
```

### Q3. Handling NumberFormatException

**Program:**

```java
public class Main {
    public static void main(String[] args) {
        String str = "123";

        try {
            int number = Integer.parseInt(str);
            System.out.println("Converted number = " + number);
        }
        catch (NumberFormatException e) {
            System.out.println("Error: Invalid number format.");
        }

        String str2 = "Hello";

        try {
            int number = Integer.parseInt(str2);
            System.out.println("Converted number = " + number);
        }
        catch (NumberFormatException e) {
            System.out.println("Error: String cannot be converted into integer.");
        }
    }
}
```

**Output:**
```text
Converted number = 123
Error: String cannot be converted into integer.
```

### Q4. Multiple catch Blocks

**Program:**

```java
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        try {
            System.out.print("Enter first number: ");
            String s1 = sc.nextLine();

            System.out.print("Enter second number: ");
            String s2 = sc.nextLine();

            int a = Integer.parseInt(s1);
            int b = Integer.parseInt(s2);

            int result = a / b;
            System.out.println("Division = " + result);

            int arr[] = {10, 20, 30, 40, 50};

            System.out.print("Enter array index (0-4): ");
            String s3 = sc.nextLine();

            int index = Integer.parseInt(s3);

            System.out.println("Array element = " + arr[index]);
        }
        catch (ArithmeticException e) {
            System.out.println("Error: Cannot divide by zero.");
        }
        catch (ArrayIndexOutOfBoundsException e) {
            System.out.println("Error: Invalid array index.");
        }
        catch (NumberFormatException e) {
            System.out.println("Error: Please enter valid integers.");
        }

        sc.close();
    }
}
```

**Output:**
```text
Enter first number: 20
Enter second number: 5
Division = 4
Enter array index (0-4): 2
Array element = 30
```

### Q5. Using finally

**Program:**

```java
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        try {
            System.out.print("Enter first number: ");
            int a = sc.nextInt();

            System.out.print("Enter second number: ");
            int b = sc.nextInt();

            int result = a / b;
            System.out.println("Division = " + result);
        }
        catch (ArithmeticException e) {
            System.out.println("Error: Cannot divide by zero.");
        }
        finally {
            System.out.println("Program execution completed.");
        }

        sc.close();
    }
}
```

**Output:**
```text
Enter first number: 20
Enter second number: 0
Error: Cannot divide by zero.
Program execution completed.
```

### Q6. Using throw

**Program:**

```java
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        System.out.print("Enter student marks: ");
        int marks = sc.nextInt();

        try {
            if (marks < 0 || marks > 100) {
                throw new IllegalArgumentException(
                    "Invalid marks! Marks must be between 0 and 100."
                );
            }

            System.out.println("Student marks = " + marks);
        }
        catch (IllegalArgumentException e) {
            System.out.println("Error: " + e.getMessage());
        }

        sc.close();
    }
}
```

**Output:**
```text
Enter student marks: 120
Error: Invalid marks! Marks must be between 0 and 100.
```

### Q7. Using throws

**Program:**

```java
import java.util.Scanner;

public class Main {

    static void checkAge(int age) throws Exception {
        if (age < 18) {
            throw new Exception("You are not eligible to vote.");
        }
        else {
            System.out.println("You are eligible to vote.");
        }
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        System.out.print("Enter your age: ");
        int age = sc.nextInt();

        try {
            checkAge(age);
        }
        catch (Exception e) {
            System.out.println("Error: " + e.getMessage());
        }

        sc.close();
    }
}
```

**Output:**
```text
Enter your age: 16
Error: You are not eligible to vote.
```

### Q8. Nested try-catch

**Program:**

```java
public class Main {
    public static void main(String[] args) {
        int a = 20;
        int b = 0;

        int arr[] = {10, 20, 30, 40, 50};

        try {
            try {
                System.out.println("Array element = " + arr[7]);
            }
            catch (ArrayIndexOutOfBoundsException e) {
                System.out.println("Error: Invalid array index.");
            }

            int result = a / b;
            System.out.println("Division = " + result);
        }
        catch (ArithmeticException e) {
            System.out.println("Error: Cannot divide by zero.");
        }
    }
}
```

**Output:**
```text
Error: Invalid array index.
Error: Cannot divide by zero.
```

### Q9. Exception Propagation

**Program:**

```java
public class Main {

    static void method3() {
        int a = 10;
        int b = 0;

        int result = a / b;
        System.out.println("Result = " + result);
    }

    static void method2() {
        method3();
    }

    static void method1() {
        method2();
    }

    public static void main(String[] args) {
        try {
            method1();
        }
        catch (ArithmeticException e) {
            System.out.println("Exception handled in main method.");
            System.out.println("Error: Cannot divide by zero.");
        }
    }
}
```


