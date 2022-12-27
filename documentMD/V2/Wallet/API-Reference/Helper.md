---
icon: dot
order: 1
---

# Helper function

Helper function for Wallet

---

### signAndSendTransaction

```ts
signAndSendTransaction(connection, data, to, privateKey, [nonce], isEstimate);
```

Sign and send transaction

#### Parameters

1. [!badge variant="warning" text="connection"] - [!badge variant="warning" text="Connection"]: Connection to interact with blockchain
2. [!badge variant="warning" text="data"] - [!badge variant="warning" text="string"]: The data of transaction
3. [!badge variant="warning" text="to"] - [!badge variant="warning" text="string"]: The address of receiver, it can be empty to create contract
4. [!badge variant="warning" text="privateKey"] - [!badge variant="warning" text="string"]: Private key of account to sign and send
5. [!badge variant="warning" text="nonce"] - [!badge variant="warning" text="number"] (optional): The nonce of account
6. [!badge variant="warning" text="isEstimate"] - [!badge variant="warning" text="boolean"] (optional): Estimate gas limit or not, default is `false`

#### Returns

[!badge variant="danger" text="receipt"] - [!badge variant="danger" text="object"]: A transaction receipt object, or null if no receipt was found.

- `status` - `Boolean`: `TRUE` if the transaction was successful, `FALSE` if the EVM reverted the transaction.
- `blockHash` 32 Bytes - `String`: Hash of the block where this transaction was in.
- `blockNumber` - `Number` (or `hex String`): Block number where this transaction was in.
- `transactionHash` 32 Bytes - `String`: Hash of the transaction.
- `transactionIndex`- `Number` (or `hex String`): Integer of the transactions index position in the block.
- `from` - `String`: Address of the sender.
- `to` - `String`: Address of the receiver. null when it’s a contract creation transaction.
- `contractAddress` - `String`: The contract address created, if the transaction was a contract creation, otherwise null.
- `cumulativeGasUsed` - `Number` (or `hex String`): The total amount of gas used when this transaction was executed in the block.
- `gasUsed` - `Number` (or `hex String`): The amount of gas used by this specific transaction alone.
- `logs` - `Array`: Array of log objects, which this transaction generated.

#### Example

```ts
> {
  nonce: 0,
  receipt: {
    transactionHash: '0xd06433e90341fa3e01fb443334d5ebb1e568887712074674b147c4bed8f00c66',
    transactionIndex: 0,
    blockHash: '0x3941967f9660339576accfe30775733199e19b69414ece1c7ec8e825622f0e95',
    blockNumber: 1,
    from: '0x32eb821d88f2e650d4732c4ce974a30bb4296949',
    to: '0xd627e4cfaed1026077abe9fd43aa750be925a077',
    gasUsed: 21000,
    cumulativeGasUsed: 21000,
    contractAddress: null,
    logs: [],
    status: true,
    logsBloom: '0x00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
  }
}
```

---

### sendSignedTransaction

```ts
sendSignedTransaction(connection, signedTx);
```

Send signed transaction

#### Parameters

1. [!badge variant="warning" text="connection"] - [!badge variant="warning" text="Connection"]: Connection to interact with blockchain
2. [!badge variant="warning" text="signedTx"] - [!badge variant="warning" text="SignedTransaction"]: The signed transaction

#### Returns

1. [!badge variant="danger" text="receipt"] - [!badge variant="danger" text="object"]: A transaction receipt object, or null if no receipt was found.

- `status` - `Boolean`: `TRUE` if the transaction was successful, `FALSE` if the EVM reverted the transaction.
- `blockHash` 32 Bytes - `String`: Hash of the block where this transaction was in.
- `blockNumber` - `Number` (or `hex String`): Block number where this transaction was in.
- `transactionHash` 32 Bytes - `String`: Hash of the transaction.
- `transactionIndex`- `Number` (or `hex String`): Integer of the transactions index position in the block.
- `from` - `String`: Address of the sender.
- `to` - `String`: Address of the receiver. null when it’s a contract creation transaction.
- `contractAddress` - `String`: The contract address created, if the transaction was a contract creation, otherwise null.
- `cumulativeGasUsed` - `Number` (or `hex String`): The total amount of gas used when this transaction was executed in the block.
- `gasUsed` - `Number` (or `hex String`): The amount of gas used by this specific transaction alone.
- `logs` - `Array`: Array of log objects, which this transaction generated.

2. [!badge variant="danger" text="eventLogs"] - [!badge variant="danger" text="Array\<any>"]: Event logs of transaction decode base on ABI

#### Example

```ts
> {
  receipt: {
    transactionHash: '0x123433e90341fa3e01fb443334d5ebb1e568887712074674b147c4bed8f00c66',
    transactionIndex: 0,
    blockHash: '0x4441967f9660339576accfe30775733199e19b69414ece1c7ec8e825622f0e95',
    blockNumber: 1,
    from: '0x3223821d88f2e650d4732c4ce974a30bb4296949',
    to: '0xd627e421aed1026077abe9fd43aa750be925a077',
    gasUsed: 21000,
    cumulativeGasUsed: 21000,
    contractAddress: null,
    logs: [],
    status: true,
    logsBloom: '0x00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
  }
  eventLogs: []
}
```

---

### checkIsContract

```ts
checkIsContract(connection, address);
```

Checks if the given address is a contract address.

#### Parameters

1. [!badge variant="warning" text="connection"] - [!badge variant="warning" text="Connection"]: Connection to interact with blockchain
2. [!badge variant="warning" text="address"] - [!badge variant="warning" text="string"]: The address to check

#### Returns

[!badge variant="danger" text="boolean"]: `true` if the address is a contract address, `false` otherwise.

#### Example

```ts
checkIsContract(connection, '0x6295ee1b4f6dd65047762f924ecd367c17eabf8f').then(console.log);
> true

```

---

### getMessageHash

```ts
getMessageHash(connection, data);
```

Get messageHash by fake signing transaction

#### Parameters

1. [!badge variant="warning" text="connection"] - [!badge variant="warning" text="Connection"]: Connection to interact with blockchain
2. [!badge variant="warning" text="data"] - [!badge variant="warning" text="object"]: Unsigned transaction

#### Returns

[!badge variant="danger" text="string"]: Message hash of transaction

#### Example

```ts
getMessageHash(
  connection,
  {
    to: "0x4390CDBBdf5ACD2c45906fF8eB3a051Bb83e5DBB",
    from: "0x2DB04a470E7058D8b0F3caf650127e538E6907e6",
    gas: 0x43aab,
    gasPrice: 0x00,
    nonce: 10,
    data: "0xb61d27f6000000000000000000000000ffd5c659b4d421fc03b500d9a4e5d91dab5080ef0000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000006000000000000000000000000000000000000000000000000000000000000001643b88f73700000000000000000000000000000000000000000000000000000000000000400000000000040000000000008a7c5cc8f8e3c43556d959b2aafa24edaabc0c8000000000000000000000000000000000000000000000000000000000000000080000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000",
  }
).then(console.log);
> "0xe14531122e105ff7e0b65e6259dc6093df6b540ef1e24d5a312b731342c7c531"

```
