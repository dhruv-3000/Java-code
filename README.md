# Java-code

import java.lang.*;
import java.io.*;
import java.util.Scanner;

import javax.swing.text.html.HTMLDocument.BlockElement;

class bloodDonor {
    int age, contactNumber;
    String name, address, bloodGroup, dateLast;

    public bloodDonor() {
        this.name = null;
        this.age = 0;
        this.address = null;
        this.contactNumber = 0;
        this.bloodGroup = null;
        this.dateLast = null;
    }

    public bloodDonor(String name, int age, String address, int contactNumber, String bloodGroup, String dateLast) {
        this.name = name;
        this.age = age;
        this.address = address;
        this.contactNumber = contactNumber;
        this.bloodGroup = bloodGroup;
        this.dateLast = dateLast;
    }
}

public class fileHandleing extends bloodDonor {
    public static void writetoFile(int n, bloodDonor array[]) {
        for (int i = 0; i < n; i++) {
            bloodDonor current = array[i];
            String s_age = Integer.toString(current.age);
            String s_contactNumber = Integer.toString(current.contactNumber);
            try {
                File fileObject = new File("details.txt");
                FileWriter cursor = new FileWriter(fileObject);
                cursor.write(current.name + "\n" + s_age + "\n" + current.address + "\n" + s_contactNumber + "\n"
                        + current.bloodGroup + "\n"
                        + current.dateLast + "\n");
                cursor.close();
            } catch (IOException e) {
                System.out.println("An error occurred.");
                e.printStackTrace();
            }
        }
    }

    public static void main(String args[]) {
        Scanner in = new Scanner(System.in);
        System.out.print("Enter number of donors to store details of: ");
        int n = in.nextInt();
        bloodDonor array[] = new bloodDonor[n];
        for (int i = 0; i < n; i++) {
            System.out.print("Enter name: ");
            String name = in.next();
            System.out.print("Enter age: ");
            int age = in.nextInt();
            System.out.print("Enter address: ");
            String address = in.next();
            System.out.print("Enter contact number: ");
            int contactNumber = in.nextInt();
            System.out.print("Enter blood group: ");
            String bloodGroup = in.next();
            System.out.print("Enter date of last donation: ");
            String dateLast = in.next();
            bloodDonor donor = new bloodDonor(name, age, address, contactNumber, bloodGroup, dateLast);
            array[i] = donor;
        }
        writetoFile(n, array);
    }
}
