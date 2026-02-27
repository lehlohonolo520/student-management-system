import java.util.ArrayList;
import java.util.Scanner;

class Student {
    private String name;
    private int age;
    private String course;

    public Student(String name, int age, String course) {
        this.name = name;
        this.age = age;
        this.course = course;
    }

    public String getName() {
        return name;
    }

    public void display() {
        System.out.println("Name: " + name);
        System.out.println("Age: " + age);
        System.out.println("Course: " + course);
        System.out.println("----------------------");
    }
}

public class StudentManagementSystem {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        ArrayList<Student> students = new ArrayList<>();
        int choice;

        do {
            System.out.println("1. Add Student");
            System.out.println("2. View All Students");
            System.out.println("3. Search Student");
            System.out.println("4. Exit");
            System.out.print("Choose option: ");
            choice = scanner.nextInt();
            scanner.nextLine();

            switch (choice) {
                case 1:
                    System.out.print("Enter name: ");
                    String name = scanner.nextLine();

                    System.out.print("Enter age: ");
                    int age = scanner.nextInt();
                    scanner.nextLine();

                    System.out.print("Enter course: ");
                    String course = scanner.nextLine();

                    students.add(new Student(name, age, course));
                    System.out.println("Student added successfully!");
                    break;

                case 2:
                    for (Student s : students) {
                        s.display();
                    }
                    break;

                case 3:
                    System.out.print("Enter student name to search: ");
                    String searchName = scanner.nextLine();
                    boolean found = false;

                    for (Student s : students) {
                        if (s.getName().equalsIgnoreCase(searchName)) {
                            s.display();
                            found = true;
                        }
                    }

                    if (!found) {
                        System.out.println("Student not found.");
                    }
                    break;

                case 4:
                    System.out.println("Exiting system...");
                    break;

                default:
                    System.out.println("Invalid option.");
            }

        } while (choice != 4);

        scanner.close();
    }
}
