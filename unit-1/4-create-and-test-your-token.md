# 4 Create and Test Your Token


Here we will create a token program of our own.

## [screenshot required] Create a token contract

For this demo, our desired features are following:

- Mint Function: Able to mint user specific `amount` of `token` to the one who called the mint function.
- Transfer Function: Able to transfer other user (`recipient`) specific `amount` of the `token` that was minted using mint function.

### Step one: define your token record

Define a token struct with an owner and balance

```leo
record Token {
    // The token owner, any record must be defined with the `owner` field.
    owner: address,
    // Token balance of the user.
    balance: u32,
}
```

### Step two: define mint function
Define a mint transition that takes a balance and returns a token record.

```leo
transition mint(amount: u32) -> Token {
    return Token {
        owner: self.caller,
        balance: amount,
    };
}
```

### Step three: define transfer function
Define a transfer transition that takes a receiver, amount and token and returns two tokens records

```leo
transition transfer(receiver: address, transfer_amount: u32, input: Token) -> (Token, Token) {
    let sender_balance: u32 = input.balance - transfer_amount;
    let recipient: Token = Token {
        owner: receiver,
        balance: transfer_amount,
    };

    let sender: Token  = Token {
        owner: self.caller,
        balance: sender_balance
    };

    return (recipient, sender);
}
```

### Final Step: overview of your main.leo file
This is what your leo.main file output

```leo
program [your_token_name].aleo {
// Step one: define your token record
record Token {
    // The token owner, any record must be defined with the `owner` field.
    owner: address,
    // Token balance of the user.
    balance: u32,
}

// Step two: define mint function
transition mint(amount: u32) -> Token {
    return Token {
        owner: self.caller,
        balance: amount,
    };
}

// Step three: define transfer function
transition transfer(receiver: address, transfer_amount: u32, input: Token) -> (Token, Token) {
    let sender_balance: u32 = input.balance - transfer_amount;
    let recipient: Token = Token {
        owner: receiver,
        balance: transfer_amount,
    };

    let sender: Token = Token {
        owner: self.caller,
        balance: sender_balance,
    };

    return (recipient, sender);
}
}
```

## Test Program

### [screenshot required] Test Mint function

Build Leo.
```bash
leo build

Ensure you see "Leo ✅ Compiled '[your_token_name].aleo' into Aleo instructions"
```

First Test Mint Function.
```bash
leo run mint 100u32

Ensure you see:

       Leo ✅ Compiled 'your_token_name.aleo' into Aleo instructions

⛓  Constraints

 •  '[your_token_name].aleo/mint' - 2,020 constraints (called 1 time)

➡️  Output

 • {
  owner: [number].private,
  balance: 100u32.private,
  _nonce: [number]group.public
}

```

The output should be a record of new 100 tokens.

### [screenshot required] Test Transfer function

Then go ahead and test Transfer Function, let's transfer 10 tokens to other address.
```bash
leo run transfer <recipient's address> 10u32 "<Token Record>"
```

This is an example of the Test Transfer function: 
```bash
leo run transfer aleo1qqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqq9d 10u32 "{ owner: aleo1abcdefgh..., balance: 100u32.private }"
```

Then the output should be two record where 10 tokens are owned under recipient's address, and remaining 90 tokens are owned by the original owner.

This is an example output you should see:
```bash
{
  "recipient": {
    "owner": "aleo1xyz...",
    "balance": 10u32.private
  },
  "sender": {
    "owner": "aleo1...",
    "balance": 90u32.private
  }
}
```

Notes:
- Remember to replace <recipient's address> field to actual address of the recipient.
- input token record should be the one that is returned after you minted. 
- the record logged on terminal usually has ".private", ".public" keywords after all properties of the record. Those are just indicators to show whether certain properties of the record is public or private.
