# Level 5 - Token

## Goal of this contract is to acquire more tokens than what was provided to the sender (20 tokens)

## Solution

Based on the contract there are two functions 
1. For the checking the **balanceOf** the owner
2. **transfer** funds to another wallet and take funds off sender's balance

If you observe the **transfer** method you can see it has a statement checking the balance after substracting tokens you intend to transfer
`require(balances[msg.sender] - _value >= 0);` - These statement validates to true if you try to pass anything beyond 20 tokens because, using a '-' like this will cause an [overflow](https://docs.soliditylang.org/en/v0.5.10/security-considerations.html#underflow-overflow), returning the last digit of uint 256
`balances[msg.sender] -= _value;` - Based on the overflow logic this will end up with enormously huge number of tokens even though sender only had 20 tokens

So, all we need to do here is send any amount more than 20 to another wallet to end with a huge balance on your own

`await contract.transfer('to_address', 21)`



