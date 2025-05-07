# Simple-banking-system-

#include <stdio.h>

struct BankAccount {
    int accountNumber;
    char name[50];
    float balance;
};

// Function to deposit money
void deposit(struct BankAccount *account, float amount) {
    if (amount > 0) {
        account->balance += amount;
        printf("Deposited ₹%.2f successfully.\n", amount);
    } else {
        printf("Invalid deposit amount.\n");
    }
}

// Function to withdraw money
void withdraw(struct BankAccount *account, float amount) {
    if (amount > account->balance) {
        printf("Insufficient balance.\n");
    } else if (amount <= 0) {
        printf("Invalid withdrawal amount.\n");
    } else {
        account->balance -= amount;
        printf("Withdrawn ₹%.2f successfully.\n", amount);
    }
}

// Function to check balance
void checkBalance(struct BankAccount account) {
    printf("Current balance: ₹%.2f\n", account.balance);
}

int main() {
    struct BankAccount user = {1001, "John Doe", 1000.0};
    int choice;
    float amount;

    do {
        printf("\n--- Simple Banking System ---\n");
        printf("1. Deposit\n");
        printf("2. Withdraw\n");
        printf("3. Check Balance\n");
        printf("4. Exit\n");
        printf("Enter your choice: ");
        scanf("%d", &choice);

        switch(choice) {
            case 1:
                printf("Enter amount to deposit: ₹");
                scanf("%f", &amount);
                deposit(&user, amount);
                break;
            case 2:
                printf("Enter amount to withdraw: ₹");
                scanf("%f", &amount);
                withdraw(&user, amount);
                break;
            case 3:
                checkBalance(user);
                break;
            case 4:
                printf("Thank you for using our banking system.\n");
                break;
            default:
                printf("Invalid choice.\n");
        }
    } while(choice != 4);

    return 0;
}
