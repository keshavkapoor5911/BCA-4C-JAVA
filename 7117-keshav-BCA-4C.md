# BCA-4C-JAVA
Dear Students, Java first assignment need to complete on time

Encapsulation in Java is the process by which data (variables) and the code that acts upon them (methods) are integrated as a single unit. By encapsulating a class's variables, other classes cannot access them, and only the methods of the class can access them. 
Create a class EMPLOYEE having data members as NameOfEmp, Emp-Id, BasicSalary and GrossSalary. NameOfEmp, Emp-Id, BasicSalary should be entered as user input. Calculate HRA (HRA is 25% of BasicSalary).Also, calculate DA (DA is 40% of BasicSalary). Then, calculate GrossSalary (GrossSalary=BasicSalary+HRA+DA). 
Implement the following queries: 
a) Display the NameOfEmp and GrossSalary of employees whose name starts With a consonent.
b) Display the Emp-Id and GrossSalary of Employees whose Emp-Id is between 101 and 150.
c) Count the total number of Employees whose GrossSalary is less than 35000/-

ans)
import java.util.Scanner;

class Employee {
    private String nameOfEmp;
    private int empId;
    private double basicSalary;
    private double grossSalary;

    public Employee(String nameOfEmp, int empId, double basicSalary) {
        this.nameOfEmp = nameOfEmp;
        this.empId = empId;
        this.basicSalary = basicSalary;
        calculateGrossSalary();
    }

    private void calculateGrossSalary() {
        double hra = 0.25 * basicSalary;
        double da = 0.40 * basicSalary;
        grossSalary = basicSalary + hra + da;
    }

    public String getNameOfEmp() {
        return nameOfEmp;
    }

    public int getEmpId() {
        return empId;
    }


    public double getGrossSalary() {
        return grossSalary;
    }

    public boolean startsWithConsonant() {
        char firstChar = nameOfEmp.toLowerCase().charAt(0);
        return !(firstChar == 'a' || firstChar == 'e' || firstChar == 'i' || firstChar == 'o' || firstChar == 'u');
    }
}

public class Main {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        System.out.println("Enter number of employees:");
        int numEmployees = scanner.nextInt();
        scanner.nextLine();

        Employee[] employees = new Employee[numEmployees];

        for (int i = 0; i < numEmployees; i++) {
            System.out.println("Enter details for Employee " + (i + 1) + ":");
            System.out.print("Name: ");
            String name = scanner.nextLine();
            System.out.print("Emp Id: ");
            int empId = scanner.nextInt();
            System.out.print("Basic Salary: ");
            double basicSalary = scanner.nextDouble();
            scanner.nextLine();
            employees[i] = new Employee(name, empId, basicSalary);
        }


        System.out.println("\nEmployees whose Emp-Id is between 101 and 150:");
        for (Employee emp : employees) {
            if (emp.getEmpId() >= 101 && emp.getEmpId() <= 150) {
                System.out.println("Emp Id: " + emp.getEmpId() + ", Gross Salary: " + emp.getGrossSalary());
            }
        }

        scanner.close();
    }
}

