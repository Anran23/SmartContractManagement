# Assessment Smart Contract

This repository contains the `Assessment` smart contract, designed to manage a simple account with deposit, withdrawal, and balance "burning" functionality. The contract enforces strict ownership rules and demonstrates Solidity's error-handling mechanisms.

---

## Features

- **Owner-Only Operations**: Only the contract owner can perform deposits, withdrawals, or burns.
- **Deposit Funds**: Increase the account balance by depositing funds.
- **Withdraw Funds**: Reduce the account balance by withdrawing funds.
- **Burn Funds**: Reduce the balance without transferring the amount (e.g., for testing or locking purposes).
- **Balance Tracking**: Query the current balance at any time.

---

## Smart Contract Overview

### **State Variables**
- `owner`: The address of the contract owner. Only this address can perform certain operations.
- `balance`: The current balance of the account.

### **Events**
- `Deposit`: Emitted when funds are deposited.
- `Withdraw`: Emitted when funds are withdrawn.

### **Functions**
1. **`getBalance()`**
   - Returns the current balance of the contract.
   - **Visibility**: `public view`.

2. **`deposit(uint256 _amount)`**
   - Allows the owner to deposit funds into the contract.
   - **Validation**:
     - The caller must be the contract owner.
     - The deposit amount must be greater than 0.
   - Emits a `Deposit` event.

3. **`withdraw(uint256 _amount)`**
   - Allows the owner to withdraw funds from the contract.
   - **Validation**:
     - The caller must be the contract owner.
     - The withdrawal amount must be greater than 0.
     - The balance must be sufficient for the withdrawal.
   - Emits a `Withdraw` event.

4. **`burn(uint256 _amount)`**
   - Reduces the balance without transferring funds to another address.
   - **Validation**:
     - The burn amount must not exceed the current balance.
   - Emits a `Withdraw` event.

---

## Constructor

```solidity
constructor(uint256 initBalance) payable
