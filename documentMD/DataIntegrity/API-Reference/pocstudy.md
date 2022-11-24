---
icon: dot
---

# POCStudy

Data Integrity SDK for manage ERC721

## Main function

---

### mintPOCStudy

```ts
ddr.mintPOCStudy(uri, message, privateKey, nonce);
```

Create POC

#### Parameters

1. [!badge variant="warning" text="uri"] - [!badge variant="warning" text="string"]: The uri
2. [!badge variant="warning" text="message"] - [!badge variant="warning" text="string"]: The message was sent from Pharumo
3. [!badge variant="warning" text="privateKey"] - [!badge variant="warning" text="string"]: Private key of contract creator - owner of identity contract which will be created
4. [!badge variant="warning" text="nonce"] - [!badge variant="warning" text="number"] (optional): The nonce of account

#### Returns

1. [!badge variant="danger" text="receipt"] - [!badge variant="danger" text="object"]: A transaction receipt object, or null if no receipt was found. (check receipt).
2. [!badge variant="danger" text="eventLogs"] - [!badge variant="danger" text="object"]:Event logs of transactions.
3. [!badge variant="danger" text="tokenId"]: tokenId was generated.

#### Example

```ts
pocStudy.mintPOCStudy('ggwp',
        "i am dev blockchain",
        "24118478a12cd8e910ec3ae69edc8bda17c70754dd00d13f28dda0aa0f8644bb")
        .then(console.log);
> {
  receipt: {
    root: '0x0000000000000000000000000000000000000000000000000000000000000000',
    cumulativeGasUsed: 1080775,
    logsBloom: '0x00000000000000000080000400000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000040000000000000000000000008008000000000000004000040000001000000000000000000000820000000000000000000800200000000000000000000010000000000000000000000000000000000000000000000000000000000010000000000000000000000000000000000000000000000000000000000000000000000000000000000002000000000000000000000000000000000000000000000000000070000000000000000000000000000000000000000000000000000000000000000000',
    logs: [ [Object], [Object] ],
    status: true,
    transactionHash: '0x9d50cdc5d13ccbc951b8a419596a4d6f79f6b3153e79a94c2166f614059a7562',
    transactionIndex: 0,
    blockHash: '0x3f9b3a03baea8868dcff1b229abac5d250058d380c69a055b750e8f6c782c5d2',
    blockNumber: 1654583,
    gasUsed: 1080775,
    contractAddress: null,
    from: '0x51C4B0487e16186da402daebE06C4cD71b5015c8',
    to: '0xE8918359122d7C4ab91186689D49FfbE55566E07'
  },
  eventLogs: [
    {
      name: 'Transfer',
      events: [Array],
      address: '0xE8918359122d7C4ab91186689D49FfbE55566E07'
    },
    {
      name: 'LockedPOCPatient',
      events: [Array],
      address: '0xE8918359122d7C4ab91186689D49FfbE55566E07'
    }
  ],
  tokenId: '1'
}
```

---

### getRootHashPOCPatient

```ts
pocStudy.getRootHashPOCPatient();
```

Get Root Hash Value

#### Parameters

None

#### Returns

[!badge variant="danger" text="String"]: Hash Value of Root Patient .

#### Example

```ts
pocStudy.getRootHashPOCPatient().then(console.log);
> "0xac25ffa90fbec2aa0a500be3e3f0643323c9c9c2c62aa5d685b7a50011d80c78"
```

---

### getRootNodeIdPOCPatient

```ts
pocStudy.getRootNodeIdPOCPatient();
```

Get Hash Value of Root Node Patient

#### Parameters

None

#### Returns

[!badge variant="danger" text="String"]: Hash Value of Root Node Patient

#### Example

```ts
pocStudy.getRootNodeIdPOCPatient().then(console.log);
> "0xc9c0421f4fc69e49a6f8d43cade8d3768bb9968fc0b6c831170a4984933edf1e"
```
