# Object Oriented Design Activity

```java
import java.util.ArrayList; // import the ArrayList class
import java.util.Scanner;  // Import the Scanner class


// Person class
class Person {
    protected String name;
    protected int age;

    public Person(String name, int age) {
        this.name = name;
        this.age = age;
    }

    public void info() {
        System.out.println("Name: " + name);
        System.out.println("Age: " + age);
    }
}

// Student class inheriting from Person
class Student extends Person {
    private String studentId;
    private ArrayList<String> courses;

    public Student(String name, int age, String studentId) {
        super(name, age);
        this.studentId = studentId;
        this.courses = new ArrayList<>();
    }
    
    public void enroll(String course) {
        courses.add(course);
    }
    
    public void displayCourses() {
        System.out.println("Enrolled courses:");
        for (String course : courses) {
            System.out.println(course);
        }
        System.out.println();
    }

    @Override
    public void info() {
        super.info();
        System.out.println("Student ID: " + studentId);
    }
}

// Teacher class inheriting from Person
class Teacher extends Person {
    private String teacherId;
    private ArrayList<String> classesTaught;

    public Teacher(String name, int age, String teacherId) {
        super(name, age);
        this.teacherId = teacherId;
        this.classesTaught = new ArrayList<>();
    }

    public void addClass(String classes) {
        classesTaught.add(classes);
    }
    
    public void displayClasses() {
        System.out.println("Classes Handled:");
        for (String classes : classesTaught) {
            System.out.println(classes);
        }
        System.out.println();
    }

    @Override
    public void info() {
        System.out.println();
        super.info();
        System.out.println("Teacher ID: " + teacherId);
    }
}

// Main class to demonstrate the student management system
class StudentManagementSystem {
    public static void main(String[] args) {
        Scanner scan = new Scanner(System.in);
        System.out.println("Enter your student id: ");
        String studentid = scan.nextLine();
        System.out.println("Enter your name: ");
        String name = scan.nextLine();
        System.out.println("Enter your age: ");
        int age = scan.nextInt();
        
        // Will take all as an input
        scan.nextLine();
        
        System.out.println("Enter the courses you want to take (Separated by a space only): ");
        String input = scan.nextLine();
        String[] inputArray = input.split(" ");
        Student student = new Student(name, age, studentid);
        // Add each input to the ArrayList
        for (String item : inputArray) {
            student.enroll(item);
        }
        student.info();
        student.displayCourses();
            
    }
}

```