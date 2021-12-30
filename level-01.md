# Level 1 - Hello Ethernaut
* Clicking on 'Get a New Instance' lets the contract be deployed in the Rinkeby Network and provides you an address the contract is deployed at
* Open "Developer Tools -> Console" 
* Explore the contract with the following commands and more through the console
  * `await contract.owner()` - Retrieve contract's owner
  * `await contract.abi` - Retrieves all the methods on the contract (ABI - Application Binary Interface moore similar to an API in the regular world)
* This level is pretty simple, it just exposes you interacting with contracts methods exposed through the abi
* `await contract.info()`
* `await contract.info1()`
* `await contract.info2('hello')` - If you send anything other than hello, this will return Wrong Parameter as the response
* `await contract.infoNum()` - This is a property on the contract for which the getter and setter methods are automatically defined in this case we are just calling the getter method
* `await contract.info42()` - This returns the name of the property you need to call next 
* `await contract.theMethodName()` - This is another property which returns the name of the method you need to call next
* `await contract.method7123949()` - The response tells you to find the password and use it as a param to authenticate
* `await contract.password()` - As we can see in the contract, password is a property, so, calling the password will retrieve the password
* `await contract.authenticate('ethernaut0')`

## You are done with level 1
