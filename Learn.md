# Gas

As show earlier, each state changing call to the smart contracts costs some ether which is called gas.

## How much ether do you need to pay for a transaction?

You pay `gas spent \* gas price` amount of ether, where

- `gas` is a unit of computation
- `gas` spent is the total amount of `gas` used in a transaction
- `gas price` is how much `ether` you are willing to pay per `gas`

Transactions with higher gas price have higher priority to be included in a block.

Unspent gas will be refunded.

## Gas Limit

There are 2 upper bounds to the amount of gas you can spend

- `gas limit` (max amount of gas you're willing to use for your transaction, set by you)
- `block gas limit` (max amount of gas allowed in a block, set by the network)

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
