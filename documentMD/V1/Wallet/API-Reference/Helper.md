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
