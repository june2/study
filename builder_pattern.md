# The Problem

```java
public class BankAccount {
    private long accountNumber;
    private String owner;
    private double balance;
    public BankAccount(long accountNumber, String owner, double balance) {
        this.accountNumber = accountNumber;
        this.owner = owner;
        this.balance = balance;
    }
    //Getters and setters omitted for brevity.
}
```

```java
BankAccount account = new BankAccount(123L, "Bart", 100.00);
```
- This code is fine. However, If we had 10 different parameters, it would become very difficult to identify what's what in the constructor at a single glance. To make it worse, some of those values might be optional, which means that we'll need to create a bunch of overloaded constructors to deal with all possible combinations, or we'll have to pass nulls to our constructor.


# Builder Pattern

- Thus, there are two specific problems that we need to solve:
 - Too many constructor arguments.
 - Incorrect object state.

```java
public class BankAccount {
    public static class Builder {
        private long accountNumber; //This is important, so we'll pass it to the constructor.
        private String owner;
        private String branch;
        private double balance;
        private double interestRate;
        public Builder(long accountNumber) {
            this.accountNumber = accountNumber;
        }
        public Builder withOwner(String owner){
            this.owner = owner;
            return this;  //By returning the builder each time, we can create a fluent interface.
        }
        public Builder atBranch(String branch){
            this.branch = branch;
            return this;
        }
        public Builder openingBalance(double balance){
            this.balance = balance;
            return this;
        }
        public Builder atRate(double interestRate){
            this.interestRate = interestRate;
            return this;
        }
        public BankAccount build(){
            //Here we create the actual bank account object, which is always in a fully initialised state when it's returned.
            BankAccount account = new BankAccount();  //Since the builder is in the BankAccount class, we can invoke its private constructor.
            account.accountNumber = this.accountNumber;
            account.owner = this.owner;
            account.branch = this.branch;
            account.balance = this.balance;
            account.interestRate = this.interestRate;
            return account;
        }
    }
    //Fields omitted for brevity.
    private BankAccount() {
        //Constructor is now private.
    }
    //Getters and setters omitted for brevity.
}
```

# lombok

- We can simply use the builder pattern with lombok.

```java
@Getter
@Setter
@Builder
public class BankAccount {
    private long accountNumber;
    private String owner;
    private double balance;
}
```
