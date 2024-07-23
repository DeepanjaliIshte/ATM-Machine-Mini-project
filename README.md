 ATM-Machine-Mini-project

 Main Class: ATM


import java.util.HashMap;
import java.util.Scanner;
public class ATM
{
    public static void main(String[] args) {
        ATMOP atmop_obj = new ATMOP();
    }
}

<h3>1. Imports: </h3>
   - import java.util.HashMap;: Imports the HashMap class, which is used for storing key-value pairs.
   - import java.util.Scanner;: Imports the Scanner class, which is used for taking input from the user.

<h3>2. Public Class ATM:  </h3>
   - Defines the main class ATM.

<h3>3. Main Method: </h3>
   - The entry point of the program.
   - Creates an instance of ATMOP class, which will trigger the operations related to the ATM.

 Data Class

java
class Data {
    float balance;
}


<h3> 4. Data Class:</h3>
   - Defines a simple class Data with one attribute balance to store the balance of an account.<br>

<h2> ATM Operations Class: ATMOP </h2>

class ATMOP {
    HashMap<Integer, Data> map = new HashMap<Integer, Data>();
    Scanner scanner = new Scanner(System.in);

    public ATMOP() {
        System.out.println("Welcome to our ATM");
        op();
    }


<h3>5. ATMOP Class:</h3>
   - Contains the main operations for the ATM.

<h3>6. Attributes:</h3>
   - HashMap<Integer, Data> map: A map to store account data with the pin code as the key and Data object as the value.
   - Scanner scanner: An instance of Scanner for reading user input.

<h3>7. Constructor:</h3>
   - Prints a welcome message.
   - Calls the op() method to start the operation.

<h2> Operation Method: op</h2>

    public void op() {
        System.out.println("");
        System.out.println("Enter your pin-code");

        int pincode = scanner.nextInt();

        if (map.containsKey(pincode)) {
            Data obj = map.get(pincode);
            menu(obj);
        } else {
            System.out.println("");
            System.out.println("Please create account first");
            System.out.println("set your pin code");

            int setpin = scanner.nextInt();

            Data obj = new Data();
            if (Integer.toString(setpin).length() < 5 && Integer.toString(setpin).length() > 2) {
                obj.balance = 0;
                map.put(setpin, obj);
                menu(obj);
            } else {
                System.out.println("Invalid pin system terminate");
            }
        }
    }


<h3>8. op Method: </h3>
   - Prompts the user to enter their pin code.
   - If the pin code exists in the map, retrieves the Data object and calls menu(obj).
   - If the pin code does not exist, prompts the user to set a new pin code.
   - Validates the pin code length (must be 3-4 digits).
   - Initializes a new account with balance 0 and adds it to the map.
   - Calls menu(obj) with the new account.

<h2> Menu Method: menu</h2>
    public void menu(Data obj) {
        System.out.println("=====================================");
        System.out.println("Please enter valid number");
        System.out.println("1. Check balance");
        System.out.println("2. Deposit money");
        System.out.println("3. Withdraw money");
        System.out.println("4. Check another account");
        System.out.println("5. Exit");

        int x = scanner.nextInt();

        if (x == 1) {
            check_balance(obj);
        } else if (x == 2) {
            deposit(obj);
        } else if (x == 3) {
            withdraw(obj);
        } else if (x == 4) {
            op();
        } else if (x == 5) {
            System.out.println("Thank You...!!...");
            System.out.println("");
            op();
        } else {
            System.out.println("Please enter the valid number");
            System.out.println("");
            menu(obj);
        }
    }


<h3>9. menu Method:</h3>
   - Displays the ATM menu.
   - Prompts the user to choose an option.
   - Calls the corresponding method based on the user's choice.
   - Loops back to the menu if the input is invalid.

 <h2>Check Balance Method: check_balance</h2>

    private void check_balance(Data obj) {
        System.out.println("your balance " + obj.balance);
        System.out.println("");
        menu(obj);
    }


10. check_balance Method:
    - Prints the current balance of the account.
    - Calls menu(obj) to display the menu again.

  <h2> Deposit Method: deposit</h2>

    private void deposit(Data obj) {
        System.out.println("Enter your amount ");
        float a = scanner.nextFloat();
        obj.balance = obj.balance + a;
        System.out.println("Amount deposited successfully!!");
        System.out.println("");
        menu(obj);
    }


11. deposit Method:
    - Prompts the user to enter an amount to deposit.
    - Adds the amount to the account balance.
    - Prints a success message.
    - Calls menu(obj) to display the menu again.

 Withdraw Method: withdraw

java
    private void withdraw(Data obj) {
        System.out.println("Enter your Amount");
        float a = scanner.nextFloat();
        if (obj.balance >= a) {
            obj.balance = obj.balance - a;
            System.out.println("Amount withdrawn successfully!!");
            System.out.println("");
        } else {
            System.out.println("Insufficient balance");
        }
        menu(obj);
    }
}


12. withdraw Method:
    - Prompts the user to enter an amount to withdraw.</br>
    - Checks if the account has sufficient balance.</br>
    - If sufficient, deducts the amount from the balance and prints a success message.</br>
    - If not sufficient, prints an "Insufficient balance" message.</br>
    - Calls menu(obj) to display the menu again.</br>

<h3>Summary</h3>

- The ATM class contains the main method which initializes the ATMOP object.</br>
- The Data class holds the account balance.</br>
- The ATMOP class manages the ATM operations, including checking balance, depositing, and withdrawing money.</br>
- The op method handles account creation and pin validation.</br>
- The menu method displays the ATM menu and calls the appropriate method based on user input.</br>
- Helper methods (check_balance, deposit, withdraw) perform specific tasks and loop back to the menu for continuous operation.</br>
