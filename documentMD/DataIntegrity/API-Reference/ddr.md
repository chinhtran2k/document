---
icon: dot
---

# DDR

Data Integrity SDK for manage ERC721

## Main function

---

### mintDDR

```ts
ddr.mintDDR(
  hashedData,
  ddrRawId,
  uri,
  patientDID,
  delegateKey,
  nonce
);
```

Create DDR for Patients

#### Parameters

1. [!badge variant="warning" text="hashedData"] - [!badge variant="warning" text="string"]: Data was hashed by the keccak256
2. [!badge variant="warning" text="ddrRawId"] - [!badge variant="warning" text="string"]: Id off-chain was sent from Pharumo
3. [!badge variant="warning" text="uri"] - [!badge variant="warning" text="string"] (optional): The uri of DDR
4. [!badge variant="warning" text="patientDID"] - [!badge variant="warning" text="string"]: Address of Patient was created from DID
5. [!badge variant="warning" text="delegateKey"] - [!badge variant="warning" text="string"]: Private key of delegateKey
6. [!badge variant="warning" text="nonce"] - [!badge variant="warning" text="number"] (optional): The nonce of account

#### Returns

1. [!badge variant="danger" text="receipt"] - [!badge variant="danger" text="object"]: A transaction receipt object, or null if no receipt was found. (check receipt).
2. [!badge variant="danger" text="eventLogs"] - [!badge variant="danger" text="array"]: An array of event logs of transactions.
3. [!badge variant="danger" text="ddrs"] - [!badge variant="danger" text="object"]: List of DDRs was minted

#### Example

```ts
ddr
  .mintDDR(
    "0x94f5115f6287e66e3fc9bbd6e4f621f7657efd488e304c810ce7d381b654f59f",
    "007",
    "Fill this text with necessary information",
    "0x7Aaf39BBD7Dd755EaA50F992522A4Eb3d8cd75a0",
    "24118478a12cd8e910ec3ae69edc8bda17c70754dd00d13f28dda0aa0f8644bb"
  )
  .then(console.log);
> {
  receipt: {
    root: "0x0000000000000000000000000000000000000000000000000000000000000000",
    cumulativeGasUsed: 794016,
    logsBloom:
      "0x00000000000000000081020400000000000000000000000000000000000000020000000000000000000000000000000000000000000001000000000000840000000014000000000000000008000000000000000000000000000000080000000000010000020040000000000000000800000000001040080000000010000000000000000000000000000000200000001000000800100800000010000000000000000000000000800010040000000000000000000000000000000000000000000000000002000000000000000000000000800000000020020000000000000020000000000000000000000000000000000000000000000000000000000000000000",
    logs: [[Object], [Object], [Object], [Object], [Object], [Object]],
    status: true,
    transactionHash:
      "0x83bf322c0d27e3cd6e94aa0bdf047564e2a65bea01d113db6724af9d3f10d313",
    transactionIndex: 0,
    blockHash:
      "0x1118c95adb3d657310f2bbb0630e934ba18ce54c4b5cd6f98d7e813607decec9",
    blockNumber: 1656748,
    gasUsed: 794016,
    contractAddress: null,
    from: "0x51C4B0487e16186da402daebE06C4cD71b5015c8",
    to: "0x00c041aeBDf546f8C4e9B8AEB098bEe047E01A2a",
  },
  eventLogs: [
    {
      name: "ExecutionRequested",
      events: [Array],
      address: "0x00c041aeBDf546f8C4e9B8AEB098bEe047E01A2a",
    },
    {
      name: "Approved",
      events: [Array],
      address: "0x00c041aeBDf546f8C4e9B8AEB098bEe047E01A2a",
    },
    {
      name: "Transfer",
      events: [Array],
      address: "0xd1ac3cb5FF3ea66198F5A848B2A9eA6615C73B36",
    },
    {
      name: "MintedDDR",
      events: [Array],
      address: "0xd1ac3cb5FF3ea66198F5A848B2A9eA6615C73B36",
    },
    {
      name: "DDRTokenLocked",
      events: [Array],
      address: "0xd1ac3cb5FF3ea66198F5A848B2A9eA6615C73B36",
    },
    {
      name: "Executed",
      events: [Array],
      address: "0x00c041aeBDf546f8C4e9B8AEB098bEe047E01A2a",
    },
  ],
  ddrs: [
    {
      tokenId: "5",
      ddrRawId: "007",
      hashValue:
        "0x02ef0a921ec25ee3e7a884130a32b34d77d2de58c5a052f3b8bb49bea02672a9",
    },
  ],
};
```

---

### mintBatchDDR

```ts
ddr.mintBatchDDR(
  hashedDatas,
  ddrRawIds,
  uris,
  patientDID,
  delegateKey,
  nonce
);
```

Create many DDRs for Patients

#### Parameters

1. [!badge variant="warning" text="hashedDatas"] - [!badge variant="warning" text="Array\<String>"]: List of datas were hashed by the keccak256
2. [!badge variant="warning" text="ddrRawIds"] - [!badge variant="warning" text="Array\<String>"]: List of ids offline was sent from Pharumo
3. [!badge variant="warning" text="uris"] - [!badge variant="warning" text="Array\<String>"]: List of uris of DDR
4. [!badge variant="warning" text="patientDID"] - [!badge variant="warning" text="string"]: Address of Patient was created from DID
5. [!badge variant="warning" text="delegateKey"] - [!badge variant="warning" text="string"]: Private key of delegateKey
6. [!badge variant="warning" text="nonce"] - [!badge variant="warning" text="number"] (optional): The nonce of account

#### Returns

1. [!badge variant="danger" text="receipt"] - [!badge variant="danger" text="object"]: A transaction receipt object, or null if no receipt was found. (check receipt).
2. [!badge variant="danger" text="eventLogs"] - [!badge variant="danger" text="array"]: An array of event logs of transactions.
3. [!badge variant="danger" text="ddrs"] - [!badge variant="danger" text="array"]: An array of object

#### Example

```ts
ddr.mintBatchDDR(
    [
      "0x6a5d6c0fb2e1fcead919f640d7ecbd5785ba9caaf45461c38a15893771f0d1a1",
      "0x7b4402c4fb2ba988bbaec633d4c68eca466f96ba75ff358006e264168524890d",
    ],
    ["09", "08"],
    ["uri1", "uri2"],
    "0x7Aaf39BBD7Dd755EaA50F992522A4Eb3d8cd75a0",
    "24118478a12cd8e910ec3ae69edc8bda17c70754dd00d13f28dda0aa0f8644bb"
  )
  .then(console.log);
> {
  receipt: {
    root: "0x0000000000000000000000000000000000000000000000000000000000000000",
    cumulativeGasUsed: 1504534,
    logsBloom:
      "0x0000000000000000000102400000000000000000000000000000000000000002000000000000000000000000000000000000000004000100002000000084000000000000000000080000000800000000000000000000000000000000000000400001000002004000000000002000080000000000104000000000001000000000000000008000000001000020000000000800000010000000000000000000000000000000000080000004000000000000000000000400002000000000000000000000000a000000000000000000000000802000000020020000000000000020000000000000000000000000000000000000000000800000040000000000000000",
    logs: [[Object], [Object], [Object], [Object], [Object], [Object]],
    status: true,
    transactionHash:
      "0x99e36320bebd87670cfcd692530ae9db6e7bc848d330846de927cdeae3dd296f",
    transactionIndex: 0,
    blockHash:
      "0xfae70507226decb837e385bdf92872ff68f1bf49d7b225fbc181b3ca617c4a9a",
    blockNumber: 1657481,
    gasUsed: 1504534,
    contractAddress: null,
    from: "0x51C4B0487e16186da402daebE06C4cD71b5015c8",
    to: "0x00c041aeBDf546f8C4e9B8AEB098bEe047E01A2a",
  },
  eventLogs: [
    {
      name: "ExecutionRequested",
      events: [Array],
      address: "0x00c041aeBDf546f8C4e9B8AEB098bEe047E01A2a",
    },
    {
      name: "Approved",
      events: [Array],
      address: "0x00c041aeBDf546f8C4e9B8AEB098bEe047E01A2a",
    },
    {
      name: "Transfer",
      events: [Array],
      address: "0xd1ac3cb5FF3ea66198F5A848B2A9eA6615C73B36",
    },
    {
      name: "Transfer",
      events: [Array],
      address: "0xd1ac3cb5FF3ea66198F5A848B2A9eA6615C73B36",
    },
    {
      name: "MintedBatchDDR",
      events: [Array],
      address: "0xd1ac3cb5FF3ea66198F5A848B2A9eA6615C73B36",
    },
    {
      name: "Executed",
      events: [Array],
      address: "0x00c041aeBDf546f8C4e9B8AEB098bEe047E01A2a",
    },
  ],
  ddrs: [
    {
      tokenId: "10",
      ddrRawId: "09",
      hashValue:
        "0x2fb8cc2fa1504ad1d348aa893604fe60a38f5d9ce0257ae2e34400600c4b12ae",
    },
    {
      tokenId: "11",
      ddrRawId: "08",
      hashValue:
        "0xa393f1efc2868f8134518c681b2f5e81314dfaeb7ad137ff4772191f56756a83",
    },
  ],
};
```

---

### sharedDDR

```ts
ddr.sharedDDR(ddrTokenIds, patientDID, delegateKey, nonce);
```

Allow address of patient to access id of ddr

#### Parameters

1. [!badge variant="warning" text="ddrTokenIds"] - [!badge variant="warning" text="Array\<number>"]: Array of id token of ddr
2. [!badge variant="warning" text="patientDID"] - [!badge variant="warning" text="string"]: Address of Patient was created from DID
3. [!badge variant="warning" text="delegateKey"] - [!badge variant="warning" text="string"]: Private key of delegateKey
4. [!badge variant="warning" text="nonce"] - [!badge variant="warning" text="number"] (optional): The nonce of account

#### Returns

1. [!badge variant="danger" text="receipt"] - [!badge variant="danger" text="object"]: A transaction receipt object, or null if no receipt was found. (check receipt).
2. [!badge variant="danger" text="eventLogs"] - [!badge variant="danger" text="array"]: An array of event logs of transactions.

#### Example

```ts
ddr.sharedDDR(
    [1, 2],
    "0x51C4B0487e16186da402daebE06C4cD71b5015c8",
    "24118478a12cd8e910ec3ae69edc8bda17c70754dd00d13f28dda0aa0f8644bb"
  )
  .then(console.log);

>{
  receipt: {
    root: "0x0000000000000000000000000000000000000000000000000000000000000000",
    cumulativeGasUsed: 325253,
    logsBloom:
      "0x00000000000008000081020400000000000000000000000000000000000000020000000080000000000000000000000000001000000001000000000000e40000000020000040000000000008000001000000000000100000000000000000000000010000020040000000000000000800000040001040200000000010000000000000000000000000000000200000000000001002100000000010000004080000020000000000800000040000000000000000000000000100000000000000000000000002000000000000000000000000800000000020020000000100000028000010000000000000000000000000000000000000000000000000000000000000",
    logs: [
      [Object],
      [Object],
      [Object],
      [Object],
      [Object],
      [Object],
      [Object],
    ],
    status: true,
    transactionHash:
      "0xb1b19feca4952eb77dc82f6907423d4837b1e0f4f817fd6a690665fc3b106702",
    transactionIndex: 0,
    blockHash:
      "0x98950e23100786884b3bb3691aa6e56120c20878b2970c1dc2105518bfe93bc0",
    blockNumber: 1656770,
    gasUsed: 325253,
    contractAddress: null,
    from: "0x51C4B0487e16186da402daebE06C4cD71b5015c8",
    to: "0x00c041aeBDf546f8C4e9B8AEB098bEe047E01A2a",
  },
  eventLogs: [
    {
      name: "ExecutionRequested",
      events: [Array],
      address: "0x00c041aeBDf546f8C4e9B8AEB098bEe047E01A2a",
    },
    {
      name: "Approved",
      events: [Array],
      address: "0x00c041aeBDf546f8C4e9B8AEB098bEe047E01A2a",
    },
    {
      name: "ApprovalShareDDR",
      events: [Array],
      address: "0xd1ac3cb5FF3ea66198F5A848B2A9eA6615C73B36",
    },
    {
      name: "Approval",
      events: [Array],
      address: "0x1B5046D7bEA27987b4b03e8c4BC486C6ac425219",
    },
    {
      name: "Transfer",
      events: [Array],
      address: "0x1B5046D7bEA27987b4b03e8c4BC486C6ac425219",
    },
    {
      name: "Executed",
      events: [Array],
      address: "0x00c041aeBDf546f8C4e9B8AEB098bEe047E01A2a",
    },
  ],
};
```

---

### disclosureConsentDDR

```ts
ddr.disclosureConsentDDR(ddrTokenIds, providerDID, delegateKey, nonce);
```

Allow list ids of ddr to provider

#### Parameters

1. [!badge variant="warning" text="ddrTokenIds"] - [!badge variant="warning" text="Array\<number>"]: List ids token of ddr
2. [!badge variant="warning" text="patientDID"] - [!badge variant="warning" text="string"]: Address of Patient was created from DID
3. [!badge variant="warning" text="providerDID"] - [!badge variant="warning" text="string"]: The address of provider was created from DID
4. [!badge variant="warning" text="delegateKey"] - [!badge variant="warning" text="string"]: Private key of delegateKey belongs to Patient
5. [!badge variant="warning" text="nonce"] - [!badge variant="warning" text="number"] (optional): The nonce of account

#### Returns

1. [!badge variant="danger" text="receipt"] - [!badge variant="danger" text="object"]: A transaction receipt object, or null if no receipt was found. (check receipt).
2. [!badge variant="danger" text="eventLogs"] - [!badge variant="danger" text="array"]: An array of event logs of transactions.

#### Example

```ts
ddr.disclosureConsentDDR(
    [0, 1],
    "0x7Aaf39BBD7Dd755EaA50F992522A4Eb3d8cd75a0",
    "0x37C819C94EdfE048968A28215C73C4D1B8ceAb15",
    "24118478a12cd8e910ec3ae69edc8bda17c70754dd00d13f28dda0aa0f8644bb"
  )
  .then(console.log);
> {
  receipt: {
    root: "0x0000000000000000000000000000000000000000000000000000000000000000",
    cumulativeGasUsed: 308787,
    logsBloom:
      "0x00000000000008000081020400040000000000000000000000000080000000020000000080000800080000000000000000000000000001000000000000e00000000000000000000000000008000001000000000000100000000000000000000000000000020040000000000000000800000040001040200000000010000000000000000000000000000000200000000000001002100000000010000004080000020000000000800000040000000000000000000000000000000000000000000000000002000000000000000000000000800080000020000000000000000028080010000000000040020000000800000000000000000000000000000000000000",
    logs: [
      [Object],
      [Object],
      [Object],
      [Object],
      [Object],
      [Object],
      [Object],
    ],
    status: true,
    transactionHash:
      "0xd36bd4b080432a1fd6089a6b33e30897bc1cf095c9f95b328aaa246922bbba66",
    transactionIndex: 0,
    blockHash:
      "0xfb0e3be58d1964bcc935994ae22f126f5a6bb05a6a8479dbc4b22575014abd21",
    blockNumber: 1657328,
    gasUsed: 308787,
    contractAddress: null,
    from: "0x51C4B0487e16186da402daebE06C4cD71b5015c8",
    to: "0x7Aaf39BBD7Dd755EaA50F992522A4Eb3d8cd75a0",
  },
  eventLogs: [
    {
      name: "ExecutionRequested",
      events: [Array],
      address: "0x7Aaf39BBD7Dd755EaA50F992522A4Eb3d8cd75a0",
    },
    {
      name: "Approved",
      events: [Array],
      address: "0x7Aaf39BBD7Dd755EaA50F992522A4Eb3d8cd75a0",
    },
    {
      name: "ApprovalDisclosureConsentDDR",
      events: [Array],
      address: "0xd1ac3cb5FF3ea66198F5A848B2A9eA6615C73B36",
    },
    {
      name: "Approval",
      events: [Array],
      address: "0x1B5046D7bEA27987b4b03e8c4BC486C6ac425219",
    },
    {
      name: "Transfer",
      events: [Array],
      address: "0x1B5046D7bEA27987b4b03e8c4BC486C6ac425219",
    },
    {
      name: "Executed",
      events: [Array],
      address: "0x7Aaf39BBD7Dd755EaA50F992522A4Eb3d8cd75a0",
    },
  ],
};
```

---

### getShareDDR

```ts
ddr.getShareDDR(patientDID, ddrTokenId);
```

Check if this address of patient is allowed to contact DDR

#### Parameters

1. [!badge variant="warning" text="patientDID"] - [!badge variant="warning" text="string"]: Address of Patient was created from DID
2. [!badge variant="warning" text="ddrTokenId"] - [!badge variant="warning" text="number"]: Id token of DDR

#### Returns

[!badge variant="danger" text="boolean"] : Check if address is allowed or not

#### Example

```ts
ddr.getShareDDR("0x7Aaf39BBD7Dd755EaA50F992522A4Eb3d8cd75a0", 1).then(console.log);
> true;
```

---

### getConsentedDDR

```ts
ddr.getConsentedDDR(providerDID, ddrTokenId);
```

Check if this address of provideris allowed to watch ddr

#### Parameters

1. [!badge variant="warning" text="providerDID"] - [!badge variant="warning" text="string"]: The address of provider
2. [!badge variant="warning" text="ddrTokenId"] - [!badge variant="warning" text="number"]: Id token of ddr

#### Returns

[!badge variant="danger" text="boolean"] : Check if address is allowed or not

#### Example

```ts
ddr.getConsentedDDR("0x37C819C94EdfE048968A28215C73C4D1B8ceAb15", 1).then(console.log);
> true;
```

---

### getLockedDDR

```ts
ddr.getLockedDDR(ddrTokenId);
```

Check if this DDR is locked or not

#### Parameters

[!badge variant="warning" text="ddrTokenId"] - [!badge variant="warning" text="Number"]: Id token of ddr

#### Returns

[!badge variant="danger" text="Boolean"] : True is locked and false is unlocked

#### Example

```ts
ddr.getLockedDDR(1).then(console.log);
> true;
```

---
### setERC20Proxy

```ts
ddr.setERC20Proxy(addressErc20Proxy, privateKey, nonce);
```

Call contract ERC20Proxy to DDR

#### Parameters

1. [!badge variant="warning" text="addressErc20Proxy"] - [!badge variant="warning" text="string"]: Address of contract ERC20Proxy
2. [!badge variant="warning" text="privateKey"] - [!badge variant="warning" text="string"]: Private key of contract creator(admin)
4. [!badge variant="warning" text="nonce"] - [!badge variant="warning" text="number"] (optional): The nonce of account

#### Returns
[!badge variant="danger" text="eventLogs"] - [!badge variant="danger" text="array"]: An array of event logs of transactions.

#### Example

```ts
ddr.setERC20Proxy(
    "0x0aFd617eDf6b1309fF492450Ea7E45e0AaB6Af3A",
    "24118478a12cd8e910ec3ae69edc8bda17c70754dd00d13f28dda0aa0f8644bb"
  )
  .then(console.log);

> root: '0x0000000000000000000000000000000000000000000000000000000000000000',
  cumulativeGasUsed: 165564,
  logsBloom: '0x04000000000000000000020000000000000000000000000000000000000000000000000000000000000000000000010000000000000001000000000000000000800000000000000000000000000000000001000000020000100000000000000000000000020040000000000008000800000000001040000000000000000000000000000020000000000000000000000000000000000000000000000000000000000000000000800000000100000000000000000000000000000a00000000000000000000000000000000000000000000000000000000000000000000000020000000000000000000000000000000000000000000008000000000000000000000',
  logs: [
    {
      address: '0x35Db94bf8f1773B71AA121ffDb9f527a0fe64bba',
      topics: [Array],
      data: '0x000000000000000000000000000000000000000000000000000000000000002000000000000000000000000000000000000000000000000000000000000000245004a4b70000000000000000000000000afd617edf6b1309ff492450ea7e45e0aab6af3a00000000000000000000000000000000000000000000000000000000',
      blockNumber: 154115,
      transactionHash: '0x0fa6b903732a580ce6bafcf9b866e3ab36669ace1c55f916a9dffa71bc6d3de2',
      transactionIndex: 0,
      blockHash: '0xa291832878833290b8f885046e1d7d4aac7aea83fd815e78740b0a67eb80376e',
      logIndex: 0,
      removed: false,
      id: 'log_bd040a19'
    },
    {
      address: '0x35Db94bf8f1773B71AA121ffDb9f527a0fe64bba',
      topics: [Array],
      data: '0x0000000000000000000000000000000000000000000000000000000000000001',
      blockNumber: 154115,
      transactionHash: '0x0fa6b903732a580ce6bafcf9b866e3ab36669ace1c55f916a9dffa71bc6d3de2',
      transactionIndex: 1,
      blockHash: '0xa291832878833290b8f885046e1d7d4aac7aea83fd815e78740b0a67eb80376e',
      logIndex: 1,
      removed: false,
      id: 'log_89665ab4'
    },
    {
      address: '0x35Db94bf8f1773B71AA121ffDb9f527a0fe64bba',
      topics: [Array],
      data: '0x000000000000000000000000000000000000000000000000000000000000002000000000000000000000000000000000000000000000000000000000000000245004a4b70000000000000000000000000afd617edf6b1309ff492450ea7e45e0aab6af3a00000000000000000000000000000000000000000000000000000000',
      blockNumber: 154115,
      transactionHash: '0x0fa6b903732a580ce6bafcf9b866e3ab36669ace1c55f916a9dffa71bc6d3de2',
      transactionIndex: 2,
      blockHash: '0xa291832878833290b8f885046e1d7d4aac7aea83fd815e78740b0a67eb80376e',
      logIndex: 2,
      removed: false,
      id: 'log_c8803e2c'
    }
  ],
  status: true,
  transactionHash: '0x0fa6b903732a580ce6bafcf9b866e3ab36669ace1c55f916a9dffa71bc6d3de2',
  transactionIndex: 0,
  blockHash: '0xa291832878833290b8f885046e1d7d4aac7aea83fd815e78740b0a67eb80376e',
  blockNumber: 154115,
  gasUsed: 165564,
  contractAddress: null,
  from: '0x51C4B0487e16186da402daebE06C4cD71b5015c8',
  to: '0x35Db94bf8f1773B71AA121ffDb9f527a0fe64bba'
}

---