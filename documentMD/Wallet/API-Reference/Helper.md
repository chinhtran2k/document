---
icon: dot
---

# Helper function

Helper function for Wallet

---

### signAndSendTransaction

```ts
wallet.signAndSendTransaction(
  connection,
  data,
  to,
  privateKey,
  [nonce],
  isEstimate
);
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

[!badge variant="danger" text="Object"]: The signTransactionOutput include info about transaction.

#### Example

```ts
{
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
