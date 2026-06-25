# source-code
this is java code create the employee management.
/////////////////////////////////////////////
Create an Employee class with id, name, and department.
Store employees in ArrayList<Employee>.
Display a menu repeatedly using a while(true) loop.
Use switch to call methods:
addEmployee()
viewEmployees()
searchEmployee()
updateDepartment()
Exit the program with option 5.
////////////////////////////////////
import java.util.ArrayList;
import java.util.Scanner;

public class EmployeeApp {

    static ArrayList<Employee> employees = new ArrayList<>();
    static Scanner sc = new Scanner(System.in);

    public static void main(String[] args) {

        while (true) {

            System.out.println("\n===== Employee Management System =====");
            System.out.println("1. Add Employee");
            System.out.println("2. View Employees");
            System.out.println("3. Search Employee");
            System.out.println("4. Update Department");
            System.out.println("5. Exit");
            System.out.print("Enter your choice: ");

            int choice = sc.nextInt();

            switch (choice) {

                case 1:
                    addEmployee();
                    break;

                case 2:
                    viewEmployees();
                    break;

                case 3:
                    searchEmployee();
                    break;

                case 4:
                    updateDepartment();
                    break;

                case 5:
                    System.out.println("Exiting...");
                    System.exit(0);

                default:
                    System.out.println("Invalid Choice!");
            }
        }
    }

    // Add Employee
    static void addEmployee() {

        System.out.print("Enter ID: ");
        int id = sc.nextInt();
        sc.nextLine();

        System.out.print("Enter Name: ");
        String name = sc.nextLine();

        System.out.print("Enter Department: ");
        String dept = sc.nextLine();

        employees.add(new Employee(id, name, dept));

        System.out.println("Employee Added Successfully!");
    }

    // View Employees
    static void viewEmployees() {

        if (employees.isEmpty()) {
            System.out.println("No Employees Found!");
            return;
        }

        System.out.println("\nEmployee List:");

        for (Employee e : employees) {
            System.out.println(
                    "ID: " + e.id +
                            " | Name: " + e.name +
                            " | Department: " + e.department);
        }
    }

    // Search Employee
    static void searchEmployee() {

        System.out.print("Enter Employee ID: ");
        int id = sc.nextInt();

        for (Employee e : employees) {

            if (e.id == id) {

                System.out.println("Employee Found:");
                System.out.println("ID: " + e.id);
                System.out.println("Name: " + e.name);
                System.out.println("Department: " + e.department);
                return;
            }
        }

        System.out.println("Employee Not Found!");
    }

    // Update Department
    static void updateDepartment() {

        System.out.print("Enter Employee ID: ");
        int id = sc.nextInt();
        sc.nextLine();

        for (Employee e : employees) {

            if (e.id == id) {

                System.out.print("Enter New Department: ");
                e.department = sc.nextLine();

                System.out.println("Department Updated Successfully!");
                return;
            }
        }

        System.out.println("Employee Not Found!");
    }
}

class Employee {
    int id;
    String name;
    String department;

    Employee(int id, String name, String department) {
        this.id = id;
        this.name = name;
        this.department = department;
    }
}
