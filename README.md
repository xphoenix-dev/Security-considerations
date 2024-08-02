# Multi-Signature Wallet Contract

This smart contract implements a multi-signature wallet, requiring multiple approvals to execute transactions. It ensures that funds are managed securely by a group of trusted individuals.

## Features

- Allows multiple owners to manage the wallet.
- Requires a specified number of confirmations to execute a transaction.
- Owners can submit, confirm, execute, and revoke transactions.

## How to Use

### Installation
1. Deploy the contract using [Remix](https://remix.ethereum.org/) or [Truffle](https://www.trufflesuite.com/).
2. Ensure that you set the initial owners and the number of required confirmations during deployment.

### Usage
1. **Submit a Transaction:**
   - Call `submitTransaction(address _to, uint256 _value, bytes memory _data)` to propose a transaction.
2. **Confirm a Transaction:**
   - Call `confirmTransaction(uint256 _txIndex)` to approve a proposed transaction.
3. **Execute a Transaction:**
   - Once the required confirmations are met, call `executeTransaction(uint256 _txIndex)` to execute the transaction.
4. **Revoke a Confirmation:**
   - If necessary, call `revokeConfirmation(uint256 _txIndex)` to withdraw your approval of a transaction.

### Example
```solidity
MultiSigWallet wallet = new MultiSigWallet([owner1, owner2, owner3], 2);
wallet.submitTransaction(recipientAddress, 10 ether, "");
wallet.confirmTransaction(0);
wallet.executeTransaction(0);
