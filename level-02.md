# Level 02 - Fallback
## There are two problems we need to solve for this level
* Claim the ownership of the contract
* Reduce its balance to 0

### Claiming the ownership of the contract
If you observe the contract, there are two ways you can claim the ownership of the contract
1. Sending ether less than 0.001 ether to the `contribute()` and making sure msg.sender(immediate entity calling the contract, in this case you) contributions are more than owners, which is 1000 ether(based on the defined constuctor)
2. Or calling the [Fallback Function](https://docs.soliditylang.org/en/v0.5.10/contracts.html#fallback-function), which in this case is receive(). we also have to ensure contributions of sender is > 0

### Solution
`await contract.contribute({'value': toWei('0.0005', 'ether')})` - This will not set the ownership but will atleast set the contributions of sender to > 0 which is required for claiming ownership through the fallback function

`await contract.send(toWei('0.0005','ether'))` - This calls the fallback function and since we msg.sender has contributions > 0 based on the above step, owner is set to the msg.sender

### Reduce its balance to 0
`await contract.withdraw()`
