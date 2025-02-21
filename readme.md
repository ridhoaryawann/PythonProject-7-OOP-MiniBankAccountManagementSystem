# Bank Account Management System - Python Project #7

![Bank Account Header](docs/header.png)

This Python program implements a bank account management system with different account types and functionalities for deposits, withdrawals, and transfers.  It also includes custom exception handling for insufficient funds.

## Features

*   **BankAccount:** A basic bank account with functionalities for:
    *   Creating an account with an initial balance and account name.
    *   Retrieving the current balance.
    *   Depositing funds.
    *   Withdrawing funds (with insufficient funds check).
    *   Transferring funds between accounts.
*   **InterestRewardsAcct:** An interest-bearing account that rewards deposits with a 5% bonus.
*   **SavingAcct:** A savings account that charges a fee of $5 for each withdrawal. It inherits from `InterestRewardsAcct`, so it also earns interest on deposits.
*   **Custom Exception:** `BalanceException` is raised when a withdrawal or transfer exceeds the available balance.

## Usage

1.  **Clone the repository (if applicable):**  If this code is in a repository, clone it to your local machine.

2.  **Save the code:** Save the provided Python code as a file named `bank_accounts.py` (or any name you prefer).

3.  **Run the code:** You can run the code directly from your terminal using:

    ```bash
    python your_script_name.py  # Replace your_script_name.py with the name of your script
    ```
    Or, you can import and use the classes in another Python script:

    ```python
    from bank_accounts import *

    # Create accounts
    dave = BankAccount(1000, "Dave")
    sara = BankAccount(2000, "Sara")
    jim = InterestRewardsAcct(1000, "Jim")
    blaze = SavingAcct(1000, "Blaze")

    # Perform operations (see examples below)
    dave.getBalance()
    sara.deposit(500)
    # ...and so on
    ```

## Examples

```python
from bank_accounts import *

# Create accounts
dave = BankAccount(1000, "Dave")
sara = BankAccount(2000, "Sara")
jim = InterestRewardsAcct(1000, "Jim")
blaze = SavingAcct(1000, "Blaze")

# Deposit
sara.deposit(500)  # Sara's balance will be 2500

# Withdraw (insufficient funds)
dave.withdraw(10000)  # Will raise a BalanceException

# Withdraw (sufficient funds)
dave.withdraw(100)   # Dave's balance will be 900

# Transfer (insufficient funds)
dave.transfer(10000, sara) # Will raise a BalanceException

# Transfer (sufficient funds)
dave.transfer(100, sara)  # Dave's balance will be 800, Sara's will be 2600

# Interest Rewards Account Deposit
jim.deposit(100) #Jim's balance will be 1105 (1000 + 100*1.05)

# Saving Account Withdraw
blaze.withdraw(100) #Blaze's balance will be 895 (1000-100-5)

# Transfer from Savings Account
blaze.transfer(100, sara) #Blaze's balance will be 790 (895-100-5), Sara's will be 2700