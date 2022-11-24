---
icon: dot
---

# ERC20Proxy

Data Integrity SDK for manage ERC721

## Main function

---

### setAwardValue

```ts
erc20Proxy.setAwardValue(value, privateKey, nonce);
```

Set the value of award

#### Parameters

1. [!badge variant="warning" text="value"] - [!badge variant="warning" text="number"]: The value of award
2. [!badge variant="warning" text="privateKey"] - [!badge variant="warning" text="string"]: Private key of contract creator - owner of identity contract which will be created
3. [!badge variant="warning" text="nonce"] - [!badge variant="warning" text="number"] (optional): The nonce of account

#### Returns

1. [!badge variant="danger" text="receipt"] - [!badge variant="danger" text="object"]: A transaction receipt object, or null if no receipt was found. (check receipt).
2. [!badge variant="danger" text="eventLogs"] - [!badge variant="danger" text="object"]:Event logs of transactions.

#### Example

```ts
erc20Proxy.setAwardValue(
    10,
    "24118478a12cd8e910ec3ae69edc8bda17c70754dd00d13f28dda0aa0f8644bb"
  )
  .then(console.log);
>{
  receipt: {
    root: "0x0000000000000000000000000000000000000000000000000000000000000000",
    cumulativeGasUsed: 24549,
    logsBloom:
      "0x00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000020000000000000000000000000000000000000000000000000000000000000000000000000000100000000000000000004000000000000000000000000000000000000000000000000000000000000400000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000040000000000000002000000000000000",
    logs: [[Object]],
    status: true,
    transactionHash:
      "0x5df0588c37ed7009cea6374665656e87a8625900bfdbb59db4c44f26aeb6c49d",
    transactionIndex: 0,
    blockHash:
      "0x1fb4316f86a01ee35e3edd954a6cefbba35e945eb0549a42f04f836c91ce1365",
    blockNumber: 1655954,
    gasUsed: 24549,
    contractAddress: null,
    from: "0x51C4B0487e16186da402daebE06C4cD71b5015c8",
    to: "0x75857E84F32D99925E7f404eBBFa04c88c589Ede",
  },
  eventLogs: [
    {
      name: "ChangedAwardValue",
      events: [Array],
      address: "0x75857E84F32D99925E7f404eBBFa04c88c589Ede",
    },
  ],
};
```

---

### setTokenOwner

```ts
erc20Proxy.setTokenOwner(tokenOwner, privateKey, nonce);
```

Set owner for token

#### Parameters

1. [!badge variant="warning" text="tokenOwner"] - [!badge variant="warning" text="string"]: Address of owner
2. [!badge variant="warning" text="privateKey"] - [!badge variant="warning" text="string"]: Private key of contract creator - owner of identity contract which will be created
3. [!badge variant="warning" text="nonce"] - [!badge variant="warning" text="number"] (optional): The nonce of account

#### Returns

1. [!badge variant="danger" text="receipt"] - [!badge variant="danger" text="object"]: A transaction receipt object, or null if no receipt was found. (check receipt).
2. [!badge variant="danger" text="eventLogs"] - [!badge variant="danger" text="object"]: Event logs of transactions.

#### Example

```ts
erc20Proxy.setTokenOwner(
    "0x6A5078326AC0694Ed1059f5e96e9D5531b319cfE",
    "24118478a12cd8e910ec3ae69edc8bda17c70754dd00d13f28dda0aa0f8644bb"
    ).then(console.log);
> {
  receipt: {
    root: '0x0000000000000000000000000000000000000000000000000000000000000000',
    cumulativeGasUsed: 30742,
    logsBloom: '0x00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000001000000000000000000000000020000000000000000000000010000000000000000000000000000000000000000000000000000120000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000040000000000000000000000000000000',
    logs: [ [Object] ],
    status: true,
    transactionHash: '0x7f10107153f5f14fbe735eb395aa60a235928680e25de7b6b999d4aeaba70f70',
    transactionIndex: 0,
    blockHash: '0x77802ca84991daf245440445d4c689ea283763d3b8b43f749df820e9b9f5e6bd',
    blockNumber: 1654783,
    gasUsed: 30742,
    contractAddress: null,
    from: '0x51C4B0487e16186da402daebE06C4cD71b5015c8',
    to: '0x75857E84F32D99925E7f404eBBFa04c88c589Ede'
  },
  eventLogs: [
    {
      name: 'ChangedTokenOwner',
      events: [Array],
      address: '0x75857E84F32D99925E7f404eBBFa04c88c589Ede'
    }
  ]
}
```

---

### setPCOToken

```ts
ddr.setPCOToken(pcoAddress, privateKey, nonce);
```

Set owner for token

#### Parameters

1. [!badge variant="warning" text="pcoAddress"] - [!badge variant="warning" text="string"]: Address of pco
2. [!badge variant="warning" text="privateKey"] - [!badge variant="warning" text="string"]: Private key of contract creator - owner of identity contract which will be created
5. [!badge variant="warning" text="nonce"] - [!badge variant="warning" text="number"] (optional): The nonce of account

#### Returns

1. [!badge variant="danger" text="receipt"] - [!badge variant="danger" text="object"]: A transaction receipt object, or null if no receipt was found. (check receipt).
2. [!badge variant="danger" text="eventLogs"] - [!badge variant="danger" text="object"]:Event logs of transactions.

#### Example

```ts
erc20Proxy.setPCOToken(
    "0x6A5078326AC0694Ed1059f5e96e9D5531b319cfE",
    "24118478a12cd8e910ec3ae69edc8bda17c70754dd00d13f28dda0aa0f8644bb")
    .then(console.log);
> {
  receipt: {
    root: '0x0000000000000000000000000000000000000000000000000000000000000000',
    cumulativeGasUsed: 29861,
    logsBloom: '0x00000000000000000000000000000000000000000000000000000000000000000000010000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000020000000000000000020000000000000000000000000000000000000000000000000000000000100000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000010000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000040000000000000000000000000000000',
    logs: [ [Object] ],
    status: true,
    transactionHash: '0x10f53cb56333bcb0a723666e1d580cdfd62f01a2d7d8347fdedd865c7fc56e48',
    transactionIndex: 0,
    blockHash: '0x989587d48cb7f14011a97699ce8acf5caa2acae0c0709f786edeb305f01a298c',
    blockNumber: 1655972,
    gasUsed: 29861,
    contractAddress: null,
    from: '0x51C4B0487e16186da402daebE06C4cD71b5015c8',
    to: '0x75857E84F32D99925E7f404eBBFa04c88c589Ede'
  },
  eventLogs: [
    {
      name: 'ChangedPCOToken',
      events: [Array],
      address: '0x75857E84F32D99925E7f404eBBFa04c88c589Ede'
    }
  ]
}

```

---

### awardToken

```ts
erc20Proxy.awardToken(to, privateKey, nonce);
```

Set the value of award

#### Parameters

1. [!badge variant="warning" text="to"] - [!badge variant="warning" text="string"]: The value of address want to receive token
2. [!badge variant="warning" text="privateKey"] - [!badge variant="warning" text="string"]: Private key of contract creator - owner of identity contract which will be created
3. [!badge variant="warning" text="nonce"] - [!badge variant="warning" text="number"] (optional): The nonce of account

#### Returns

1. [!badge variant="danger" text="receipt"] - [!badge variant="danger" text="object"]: A transaction receipt object, or null if no receipt was found. (check receipt).
2. [!badge variant="danger" text="eventLogs"] - [!badge variant="danger" text="object"]:Event logs of transactions.

#### Example

```ts
erc20Proxy
  .awardToken(
    "0x6A5078326AC0694Ed1059f5e96e9D5531b319cfE",
    "24118478a12cd8e910ec3ae69edc8bda17c70754dd00d13f28dda0aa0f8644bb"
  )
  .then(console.log);
> {
  receipt: {
    root: "0x0000000000000000000000000000000000000000000000000000000000000000",
    cumulativeGasUsed: 29803,
    logsBloom:
      "0x00000000000000000000000000000000000000000000000000000000000000000000000080000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000020000000000000000000000000000000000000000000000000000000000000000000000200000100000000000000000000000000000000000000000000000000000000000000000000000080000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000040000000000000000000000000000000",
    logs: [[Object]],
    status: true,
    transactionHash:
      "0x3c3c739a17c2ff51acffbd4bdd572201acf0baee71d2935b332b6636bf8e8407",
    transactionIndex: 0,
    blockHash:
      "0xfe692395854df4dd6f5a092dbe42ac472c6be4ff00f69a6ecb1668e9ed71258a",
    blockNumber: 1656077,
    gasUsed: 29803,
    contractAddress: null,
    from: "0x51C4B0487e16186da402daebE06C4cD71b5015c8",
    to: "0x75857E84F32D99925E7f404eBBFa04c88c589Ede",
  },
  eventLogs: [
    {
      name: "AwardedToken",
      events: [Array],
      address: "0x75857E84F32D99925E7f404eBBFa04c88c589Ede",
    },
  ],
};
```

---

### setDDRContract

```ts
erc20Proxy.setDDRContract(ddrAddress, privateKey, nonce);
```

Set address for ddr contract

#### Parameters

1. [!badge variant="warning" text="ddrAddress"] - [!badge variant="warning" text="string"]: The address of ddr
2. [!badge variant="warning" text="privateKey"] - [!badge variant="warning" text="string"]: Private key of contract creator - owner of identity contract which will be created
3. [!badge variant="warning" text="nonce"] - [!badge variant="warning" text="number"] (optional): The nonce of account

#### Returns

1. [!badge variant="danger" text="receipt"] - [!badge variant="danger" text="object"]: A transaction receipt object, or null if no receipt was found. (check receipt).
2. [!badge variant="danger" text="eventLogs"] - [!badge variant="danger" text="object"]: Event logs of transactions.

#### Example

```ts
erc20Proxy.setDDRContract(
    "0x51C4B0487e16186da402daebE06C4cD71b5015c8",
    "24118478a12cd8e910ec3ae69edc8bda17c70754dd00d13f28dda0aa0f8644bb"
  )
  .then(console.log);
> {
  receipt: {
    root: "0x0000000000000000000000000000000000000000000000000000000000000000",
    cumulativeGasUsed: 29884,
    logsBloom:
      "0x00000000000000000000000000000000000000000000000000000000000000400000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000020000000000000000000000000000000000000000000000000000000000000000000000000000100000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000100000000000000000000000000000000000000000000000000000000000040000000000000000000000008000000",
    logs: [[Object]],
    status: true,
    transactionHash:
      "0xaaa36701dfd601fcc53bcc10fbe5b2eb906c8b81cab05866b9ffbfe85fc44544",
    transactionIndex: 0,
    blockHash:
      "0x621b490d0eec0ef118c965b9d7aa62b7ae0760c17b5710a536e51c559458534a",
    blockNumber: 1656010,
    gasUsed: 29884,
    contractAddress: null,
    from: "0x51C4B0487e16186da402daebE06C4cD71b5015c8",
    to: "0x75857E84F32D99925E7f404eBBFa04c88c589Ede",
  },
  eventLogs: [
    {
      name: "ChangedDDR",
      events: [Array],
      address: "0x75857E84F32D99925E7f404eBBFa04c88c589Ede",
    },
  ],
};
```
