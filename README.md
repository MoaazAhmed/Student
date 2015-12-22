# Student
package FatihSultanMehmetVakifUniversity;

public class Servies {


    public static double Grade(int[] arrayOfMarks) {

        double sum = 0;
        double GPA = 0;

        for (int i = 0; i < arrayOfMarks.length; i++) {
            sum += arrayOfMarks[i];
        }

        GPA = sum / arrayOfMarks.length;
        //GPA = GPA / 5;

        return GPA;
    }
    public static void print(int[] arrayOfMarks, Student object) {
        double GPA = Grade(arrayOfMarks);
        String grade = convert(GPA);

        System.out.println("/*********** student grade **************/");

        object.printInformation();
        for (int i = 0; i < arrayOfMarks.length; i++) {

            System.out.println("Mark Of subject " + (i + 1) + " : " + arrayOfMarks[i]);
        }
        System.out.println("GPA: " + grade);

    }

    public static String convert(double grade) {
        double points = 0;
        String result;
        if (grade > 85) {
            result = "A";
        } else if (grade > 75) {
            result = "B";
        } else if (grade > 65) {
            result = "C";
        } else if (grade > 50) {
            result = "D";
        } else {
            result = "Faild";
        }
        return result;
    }
}


public class Student extends Person {

    //Students id 

    private int id;
    //Students Name
    //private String Name;
    //students department 
    private String Department;
    ////Students GPA
    private float GPA;
    /*
     Initialization Student date
     */

    public Student() {
        this.id = 0;
        this.Name = "None";
        this.Department = "None";
        this.GPA = 0.0f;
    }
    /*
     Initialization Student date
     pid : Student id
     pname :Student name
     pdepartment : Student department
     pgpa : Student GPA
     NOT: (p) Stands for parameter
     */

    public Student(int pid, String pname, String pdepartment, float pgpa) {
        this.id = pid;
        this.Name = pname;
        this.Department = pdepartment;
        this.GPA = pgpa;

    }
   
    /*
     Change student id 
     pid :student id 
     */
    public void setId(int pid) {
        this.id = pid;
    }

    //get the current student id 

    public int getId() {
        return this.id;
    }
    /*
     Change student name 
     pid :student name 
     */

    public void setName(String pname) {
        this.Name = pname;
    }
    //get the current student name 

    public String getName() {
        return this.Name;
    }

    /*
     Change student deparment 
     pdepartment : student department
     */
    public void setDepartment(String pdepartment) {
        this.Department = pdepartment;
    }

    //get the current student department 

    public String getDepartment() {
        return this.Department;
    }
    /*
     Change student GPA 
     pid :student GPA 
     */

    public void setGPA(float pgpa) {
        this.GPA = pgpa;
    }
    //get the current student GPA 

    public float getGPA() {
        return this.GPA;
    }
    
@Override
    public void printInformation() {
        System.out.println("--------- " + this.Name + "'s Information " + " ---------");
        System.out.println("Department : " + this.Department);
        System.out.println("ID: " + this.id);
        System.out.println("GPA :" + this.GPA);
    }

    
     public void printInformation(Student std) {
        System.out.println("--------- " + std.Name + "'s Information " + " ---------");
        System.out.println("Department : " + std.Department);
        System.out.println("ID: " + std.id);
        System.out.println("GPA :" + std.GPA);
    }
}

public class Person {

   protected String Name;
   
   
   public void printInformation() {
        System.out.println("--------- " + this.Name + "'s Information " + " ---------");
    }
}

/*
 * To change this license header, choose License Headers in Project Properties.
 * To change this template file, choose Tools | Templates
 * and open the template in the editor.
 */
package FatihSultanMehmetVakifUniversity;

import java.util.Scanner;
import java.util.ArrayList;

public class Main1 {

//------------------------------------------------------------------------------
    public static void main(String[] args) {
        int numOfStudent, numOfSubject;

        try {
            Scanner input = new Scanner(System.in);
            System.out.print("Enter the number of student : ");
            numOfStudent = input.nextInt();
            //  Student[] arrayOfStudent = new Student[numOfStudent];
            ArrayList<Student> arrayOfStudent = new ArrayList<Student>();
            System.out.print("Please enter the number of subjects for a Student  : ");
            numOfSubject = input.nextInt();
            int[] arrayOfMarks = new int[numOfSubject];
            for (int i = 0; i < numOfStudent; i++) {

                Student std = new Student();
                // i wanna to make sure that the id has been entered currecctly (done)

                System.out.print("Please enter ID of student " + (i + 1) + ": ");
                std.setId(input.nextInt());

                //i wanna to make sure that the department has been entered currectly
                System.out.print("Please enter Name of student " + (i + 1) + ": ");
                std.setName(input.next());

                //i wanna to make sure that the department has been entered currectly
                System.out.print("Plaese enter Department of student " + (i + 1) + ": ");
                std.setDepartment(input.next());

                //i wanna to make sure that the GPA has been entered currectly
                for (int j = 0; j <= numOfSubject - 1; j++) {
                    System.out.print("Please enter mark Of subject " + (j + 1) + " : ");
                    arrayOfMarks[j] = input.nextInt();
                }

                //arrayOfSubject[i]=new Student();
                
                arrayOfStudent.add(std);
            }

            for (int i = 0; i < arrayOfStudent.size(); i++) {

                Servies.print(arrayOfMarks, arrayOfStudent.get(i));
            }

        } catch (Exception e) {
            System.out.println("Your error :" + e.getMessage());
            System.exit(0);
        }

    }
}
