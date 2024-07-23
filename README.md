 ## ATM-Machine-Mini-project

<h2>Summary</h2>

- The ATM class contains the main method which initializes the ATMOP object.</br>
- The Data class holds the account balance.</br>
- The ATMOP class manages the ATM operations, including checking balance, depositing, and withdrawing money.</br>
- The op method handles account creation and pin validation.</br>
- The menu method displays the ATM menu and calls the appropriate method based on user input.</br>
- Helper methods (check_balance, deposit, withdraw) perform specific tasks and loop back to the menu for continuous operation.</br>

<h2>Main Class: ATM</h2> 

<h6>
import java.util.HashMap;<br>
import java.util.Scanner;<br>
public class ATM<br>
{<br>
    public static void main(String[] args) {<br>
        ATMOP atmop_obj = new ATMOP();<br>
    }<br>
}<br>
</h6>
<h4>1. Imports: </h4>
   - import java.util.HashMap;: Imports the HashMap class, which is used for storing key-value pairs.<br>
   - import java.util.Scanner;: Imports the Scanner class, which is used for taking input from the user.<br>

<h4>2. Public Class ATM:  </h4>
   - Defines the main class ATM.<br>

<h4>3. Main Method: </h4>
   - The entry point of the program.<br>
   - Creates an instance of ATMOP class, which will trigger the operations related to the ATM.<br>

 <h2>Data Class</h2>

<h6>class Data <br>
       {<br>
          float balance;<br>
       }</h6><br>


<h4> 4. Data Class:</h4>
   - Defines a simple class Data with one attribute balance to store the balance of an account.<br>

<h2> ATM Operations Class: ATMOP </h2>
<h6>
class ATMOP {<br>
    HashMap<Integer, Data> map = new HashMap<Integer, Data>();<br>
    Scanner scanner = new Scanner(System.in);<br>
    public ATMOP() {<br>
        System.out.println("Welcome to our ATM");<br>
        op();<br>
    }<br>
</h6>

<h4>5. ATMOP Class:</h4>
   - Contains the main operations for the ATM.<br>

<h4>6. Attributes:</h4>
   - HashMap<Integer, Data> map: A map to store account data with the pin code as the key and Data object as the value.<br>
   - Scanner scanner: An instance of Scanner for reading user input.<br>

<h4>7. Constructor:</h4>
   - Prints a welcome message.<br>
   - Calls the op() method to start the operation.<br>

<h2> Operation Method: op</h2>
<h6>
    public void op() {<br>
        System.out.println("");<br>
        System.out.println("Enter your pin-code");<br>
 
        int pincode = scanner.nextInt();<br>

        if (map.containsKey(pincode)) {<br>
            Data obj = map.get(pincode);<br>
            menu(obj);<br>
        }<br>
        else {<br>
            System.out.println("");<br>
            System.out.println("Please create account first");<br>
            System.out.println("set your pin code");<br>

            int setpin = scanner.nextInt();<br>

            Data obj = new Data();<br>
            if (Integer.toString(setpin).length() < 5 && Integer.toString(setpin).length() > 2) {<br>
                obj.balance = 0;<br>
                map.put(setpin, obj);<br>
                menu(obj);<br>
            } else {<br>
                System.out.println("Invalid pin system terminate");<br>
            }<br>
        }<br>
    }<br>
</h6>
<h4>8. op Method: </h4>
   - Prompts the user to enter their pin code.<br>
   - If the pin code exists in the map, retrieves the Data object and calls menu(obj).<br>
   - If the pin code does not exist, prompts the user to set a new pin code.<br>
   - Validates the pin code length (must be 3-4 digits).<br>
   - Initializes a new account with balance 0 and adds it to the map.<br>
   - Calls menu(obj) with the new account.<br>

<h2> Menu Method: menu</h2>
<h6>
    public void menu(Data obj) {<br>
        System.out.println("=====================================");<br>
        System.out.println("Please enter valid number");<br>
        System.out.println("1. Check balance");<br>
        System.out.println("2. Deposit money");<br>
        System.out.println("3. Withdraw money");<br>
        System.out.println("4. Check another account");<br>
        System.out.println("5. Exit");<br>

        int x = scanner.nextInt();<br>

        if (x == 1) {<br>
            check_balance(obj);<br>
        } else if (x == 2) {<br>
            deposit(obj);<br>
        } else if (x == 3) {<br>
            withdraw(obj);<br>
        } else if (x == 4) {<br>
            op();<br>
        } else if (x == 5) {<br>
            System.out.println("Thank You...!!...");<br>
            System.out.println("");<br>
            op();<br>
        } else {<br>
            System.out.println("Please enter the valid number");<br>
            System.out.println("");<br>
            menu(obj);<br>
        }<br>
    }<br>
</h6>

<h4>9. menu Method:</h4>
   - Displays the ATM menu.<br>
   - Prompts the user to choose an option.<br>
   - Calls the corresponding method based on the user's choice.<br>
   - Loops back to the menu if the input is invalid.<br>

 <h2>Check Balance Method: check_balance</h2>

    private void check_balance(Data obj) {<br>
        System.out.println("your balance " + obj.balance);<br>
        System.out.println("");<br>
        menu(obj);<br>
    }<br>


<h4>10. check_balance Method:</h4><br>
    - Prints the current balance of the account.<br>
    - Calls menu(obj) to display the menu again.<br>

  <h2> Deposit Method: deposit</h2>
<h6>
    private void deposit(Data obj) {<br>
        System.out.println("Enter your amount ");<br>
        float a = scanner.nextFloat();<br>
        obj.balance = obj.balance + a;<br>
        System.out.println("Amount deposited successfully!!");<br>
        System.out.println("");<br>
        menu(obj);<br>
    }<br>
</h6>

<h4>11. deposit Method: </h4>
    - Prompts the user to enter an amount to deposit.<br>
    - Adds the amount to the account balance.<br>
    - Prints a success message.<br>
    - Calls menu(obj) to display the menu again.<br>

<h2> Withdraw Method: withdraw</h2>
<h6>
    private void withdraw(Data obj) {<br>
        System.out.println("Enter your Amount");<br>
        float a = scanner.nextFloat();<br>
        if (obj.balance >= a) {<br>
            obj.balance = obj.balance - a;<br>
            System.out.println("Amount withdrawn successfully!!");<br>
            System.out.println("");<br>
        } else {<br>
            System.out.println("Insufficient balance");<br>
        }<br>
        menu(obj);<br>
    }<br>
}<br>
</h6>

<h4>12. withdraw Method:</h4>
    - Prompts the user to enter an amount to withdraw.</br>
    - Checks if the account has sufficient balance.</br>
    - If sufficient, deducts the amount from the balance and prints a success message.</br>
    - If not sufficient, prints an "Insufficient balance" message.</br>
    - Calls menu(obj) to display the menu again.</br>

