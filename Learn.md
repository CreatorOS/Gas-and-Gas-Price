# Gas

Whenever we call a function that modifies a `state variable`, we need to pay. This is called gas.

## How much ether do you need to pay for a transaction?
How much ether do you need to pay for a transaction?
You pay `gas spent * gas price` amount of ether, where

- `gas` is a unit of computation (think of it as number of lines of code)
- `gas spent` is the total amount of `gas` used in a transaction (like number of lines of code executed in a function call. If you have a for loop that executes a line 10 times, gas will be spent for that line of code 10 times)
- `gas price` is how much `ether` you are willing to pay per `gas` (how much you must pay for executing one line of code? This is determined by demand and supply. If there is not much traffic on the Ethereum network, gas price is low. If there are a lot of people calling contract functions, the price is high.)

Transactions with higher gas price have higher priority to be included in a block (i.e. exectuted).

Unspent gas will be refunded. Sometimes you might be unsure of how much gas will be used in the function. You can send excess gas, some of it will be used to run the code and the remainder will be returned.

## Gas Limit

There are 2 upper bounds to the amount of gas you can spend

- `gas limit` max amount of gas you're willing to use for your transaction, set by you. If there is more gas used (e.g. an infinite loop), you will use at most this much gas.
- `block gas limit` max amount of gas allowed in a block, set by the network. Every transaction is collected in a block. There are a finite number of transactions that can be executed every block (every 10-12s). The number of transactions that will be included in this block is determined by how much gas all the transactions put together use - if the sum exceeds the block gas limit, some of the transactions will have to be ommitted or included in the next block.

## Testing gas limit

Let's write a function that will run until it runs out of gas.

- Using up all of the gas that you send causes your transaction to fail.
- State changes are undone.
- Gas spent are not refunded.

```
    uint public i = 0;

    function forever() public {
        while (true) {
            i += 1;
        }
    }
```

Here we have written a loop that will run untill it runs out of gas and the transaction fails.

Hit `Run` and you will see that the transaction fail logs in the output.
