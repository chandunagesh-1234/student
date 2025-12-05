
import java.util.Scanner;

class BankAccount {
    private String name;
    private int accountNumber;
    private double balance;

    // Constructor
    BankAccount(String name, int accNo, double balance) {
        this.name = name;
        this.accountNumber = accNo;
        this.balance = balance;
    }

    // Deposit method
    void deposit(double amount) {
        balance += amount;
        System.out.println("Amount Deposited: " + amount);
        System.out.println("Updated Balance: " + balance);
    }

    // Withdraw method
    void withdraw(double amount) {
        if (amount > balance) {
            System.out.println("Insufficient Balance!");
        } else {
            balance -= amount;
            System.out.println("Amount Withdrawn: " + amount);
            System.out.println("Updated Balance: " + balance);
        }
    }

    // Check Balance
    void checkBalance() {
        System.out.println("Current Balance: " + balance);
    }
}

public class BankManager {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        // Creating account
        System.out.print("Enter Name: ");
        String name = sc.nextLine();

        System.out.print("Enter Account Number: ");
        int accNo = sc.nextInt();

        System.out.print("Enter Initial Balance: ");
        double balance = sc.nextDouble();

        BankAccount customer = new BankAccount(name, accNo, balance);

        int choice;
        do {
            System.out.println("\n--- BANK MANAGER MENU ---");
            System.out.println("1. Deposit");
            System.out.println("2. Withdraw");
            System.out.println("3. Check Balance");
            System.out.println("4. Exit");
            System.out.print("Enter your choice: ");
            choice = sc.nextInt();

            switch(choice) {
                case 1:
                    System.out.print("Enter amount to deposit: ");
                    customer.deposit(sc.nextDouble());
                    break;

                case 2:
                    System.out.print("Enter amount to withdraw: ");
                    customer.withdraw(sc.nextDouble());
                    break;

                case 3:
                    customer.checkBalance();
                    break;

                case 4:
                    System.out.println("Thank you for using Bank Manager!");
                    break;

                default:
                    System.out.println("Invalid Choice!");
            }
        } while(choice != 4);

        sc.close();
    }
}
