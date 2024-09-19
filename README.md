# Lab: 7.0.6

**Objective:**

- Understand the concept and importance of pass-by-value and pass-by-reference in Java development.
- Learn how to implement and distinguish between pass-by-value and pass-by-reference scenarios in a real-world banking
  application.
- Explore practical applications of these concepts in managing bank accounts and transactions.
- Identify common pitfalls and best practices when working with method arguments and object references in financial
  systems.
- Gain hands-on experience with a complete Java example that demonstrates both pass-by-value and pass-by-reference
  behavior in a banking context.

**Prerequisites:**

- Basic understanding of Java programming.
- Familiarity with object-oriented programming concepts.
- Understanding of primitive data types and objects in Java.

**What You'll Achieve:**

- Develop a solid understanding of how Java handles method arguments for primitives and objects in a banking context.
- Implement practical examples that demonstrate the difference between pass-by-value and pass-by-reference in financial
  transactions.
- Enhance your skills in managing object references and understanding memory management in Java, crucial for maintaining
  data integrity in banking systems.

**Assignment Details**

You are provided with the following `BankAccount` class:

```java
package academy.javapro.lab;

public class BankAccount {
    private String accountNumber;
    private double balance;
    private String ownerName;

    public BankAccount(String accountNumber, double initialBalance, String ownerName) {
        this.accountNumber = accountNumber;
        this.balance = initialBalance;
        this.ownerName = ownerName;
    }

    public double getBalance() {
        return balance;
    }

    public void deposit(double amount) {
        if (amount > 0) {
            balance += amount;
        }
    }

    public void withdraw(double amount) {
        if (amount > 0 && amount <= balance) {
            balance -= amount;
        }
    }

    public String getAccountNumber() {
        return accountNumber;
    }

    public String getOwnerName() {
        return ownerName;
    }

    public void setOwnerName(String name) {
        this.ownerName = name;
    }

    @Override
    public String toString() {
        return String.format("Account Number: %s, Owner: %s, Balance: $%.2f", 
                             accountNumber, ownerName, balance);
    }
}

```

1. Create a new class named `BankingOperations` with the following static methods:
    - `attemptToModifyBalance(BankAccount account, double amount)`: Attempts to modify the account balance directly (this should not work). 
    - `transferFunds(BankAccount fromAccount, BankAccount toAccount, double amount)`: Transfers funds between accounts. 
    - `updateAccountOwner(BankAccount account, String newOwner)`: Updates the account owner's name. 
    - `swapAccounts(BankAccount account1, BankAccount account2)`: Attempts to swap two accounts (this should not work as expected).
2. In the main method of `BankingOperations`:
   - Create two `BankAccount` objects.
   - Print their initial states.
   - Perform a series of operations using the methods you've created:
3. Implement the methods to demonstrate:
   - How object references (`BankAccount`) are passed by value.
   - How primitive types (double for amounts) are passed by value.
   - How modifying the object's state affects the original object, but reassigning the reference does not.
4. Add comments explaining the behavior observed in each step, particularly focusing on why certain operations affect the original objects and others don't.

**Example Output**

```
Initial account states:
Account 1: {Account Number: 1001, Owner: Alice, Balance: $1000.00}
Account 2: {Account Number: 1002, Owner: Bob, Balance: $500.00}

After attempting to modify Account 1 balance directly:
Account 1: {Account Number: 1001, Owner: Alice, Balance: $1000.00} // Unchanged

After transferring $300 from Account 1 to Account 2:
Account 1: {Account Number: 1001, Owner: Alice, Balance: $700.00}
Account 2: {Account Number: 1002, Owner: Bob, Balance: $800.00}

After updating Account 1 owner to "Alicia":
Account 1: {Account Number: 1001, Owner: Alicia, Balance: $700.00}

After attempting to swap accounts:
Account 1: {Account Number: 1001, Owner: Alicia, Balance: $700.00} // Unchanged
Account 2: {Account Number: 1002, Owner: Bob, Balance: $800.00} // Unchanged
```

**Starter Code**

The `BankingOperations.java` file contains the following starter code:

```java
public class BankingOperations {
    public static void main(String[] args) {
        // TODO: Create BankAccount objects and demonstrate operations
    }

    public static void attemptToModifyBalance(BankAccount account, double amount) {
        // TODO: Attempt to modify the balance directly (this should not work)
    }

    public static void transferFunds(BankAccount fromAccount, BankAccount toAccount, double amount) {
        // TODO: Implement fund transfer logic
    }

    public static void updateAccountOwner(BankAccount account, String newOwner) {
        // TODO: Implement owner update logic
    }

    public static void swapAccounts(BankAccount account1, BankAccount account2) {
        // TODO: Attempt to swap two accounts (this should not work as expected)
    }
}

```

**Hints**

- Remember that when you pass a `BankAccount` object to a method, you're passing the reference by value. This means you
  can call methods on the object to change its state, but reassigning the reference won't affect the original variable.
- In `attemptToModifyBalance`, you won't be able to change the balance directly because the `BankAccount` class
  encapsulates its data. You'll need to use the provided methods.
- For `transferFunds`, use the withdraw and deposit methods of the `BankAccount` objects.
- In `swapAccounts`, you'll find that swapping references inside the method doesn't affect the original references in
  the calling method.

**Submission Instructions**

1. Fork the repository
2. Clone your fork
3. Navigate into the repository
4. Implement the required methods in the `BankingOperations.java` file
5. Test your implementation with various inputs
6. Git add, commit, and push to your fork
7. Submit a pull request
    - Set the title of the pull request to your first name and last name
    - In the comment, briefly explain your implementation approach and any challenges you faced

Remember, the goal is to learn and have fun! Don't hesitate to ask for help if you get stuck.