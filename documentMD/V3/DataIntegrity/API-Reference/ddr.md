---
icon: dot
---

# DDR

This module use to mint/share/consent/lock DDR.

## Main function

---

### mintDDR

```ts
ddr.mintDDR(hashValue, ddrId, uri, patientDID, delegateKey, nonce?, isSimalate?);
```

Create DDR for Patients.

#### Parameters

1. [!badge variant="warning" text="hashValue"] - [!badge variant="warning" text="string"]: Data of DDR was hashed by the keccak256 from Pharumo.
2. [!badge variant="warning" text="ddrId"] - [!badge variant="warning" text="string"]: DID Id off-chain was sent from Pharumo.
3. [!badge variant="warning" text="uri"] - [!badge variant="warning" text="string"] (optional): The uri of DDR.
4. [!badge variant="warning" text="patientDID"] - [!badge variant="warning" text="string"]: Address of Patient was created from DID.
5. [!badge variant="warning" text="delegateKey"] - [!badge variant="warning" text="string"]: Private key of delegateKey.
6. [!badge variant="warning" text="nonce"] - [!badge variant="warning" text="number"] (optional): The nonce of account.
7. [!badge variant="warning" text="isSimulate"] - [!badge variant="warning" text="boolean"] (optional): Emulator status.

#### Returns

1. [!badge variant="danger" text="receipt"] - [!badge variant="danger" text="object"]: A transaction receipt object, or null if no receipt was found. (check receipt).
2. [!badge variant="danger" text="eventLogs"] - [!badge variant="danger" text="array"]: An array of event logs of transactions.
3. [!badge variant="danger" text="ddrs"] - [!badge variant="danger" text="object"]: List of DDRs was minted.

#### Example

```ts
ddr.mintDDR(
        "0x292383490336287f71b0803c84828243418c4e70fb392679f2c0e5abb0772177",
        "004",
        "PATIENT",
        "0x91a6eBbDF60316065a9b0ddBeBB10e0fb51F3218",
        "24118478a12cd8e910ec3ae69edc8bda17c70754dd00d13f28dda0aa0f8644bb"
    )
  .then(console.log);
> {
  receipt: {
    root: '0x0000000000000000000000000000000000000000000000000000000000000000',
    cumulativeGasUsed: 606473,
    logsBloom: '0x00000000000000000080020400000000400000000000000000001000000000000000000008000000000000000000000000000000000001000000000000040000000004000400000000000008000000000000000000040000000000000200000108000000020040000000000000000800000000001040000000000010
000000000040000000000000000000200000004000000080000000000010000000000000000000000000800010000000000000000000000000000000002000000000000000010002000000000000000100000000800000008000000000000000000060000000000000000000000000000000000000000000000000010000000000000000',
    logs: [ [Object], [Object], [Object], [Object], [Object], [Object] ],
    status: true,
    transactionHash: '0x751f90a54ce3f37d9999d80afa03652124c24318348ece917b1f4daf23d4e284',
    transactionIndex: 0,
    blockHash: '0x67c87882b06448f5296db7998c7fb54164f7b4839615e8d11ca3710295fd9a46',
    blockNumber: 2035158,
    gasUsed: 606473,
    contractAddress: null,
    from: '0x51C4B0487e16186da402daebE06C4cD71b5015c8',
    to: '0xb007880f85F038bBE3641736c23B1cc2e083e79a'
  },
  eventLogs: [
    {
      name: 'ExecutionRequested',
      events: [Array],
      address: '0xb007880f85F038bBE3641736c23B1cc2e083e79a'
    },
    {
      name: 'Approved',
      events: [Array],
      address: '0xb007880f85F038bBE3641736c23B1cc2e083e79a'
    },
    {
      name: 'Transfer',
      events: [Array],
      address: '0x49417fbd8830A333136d2Eb04eb4988eb11F03fF'
    },
    {
      name: 'MintedDDR',
      events: [Array],
      address: '0x49417fbd8830A333136d2Eb04eb4988eb11F03fF'
    },
    {
      name: 'DDRTokenLocked',
      events: [Array],
      address: '0x49417fbd8830A333136d2Eb04eb4988eb11F03fF'
    },
    {
      name: 'Executed',
      events: [Array],
      address: '0xb007880f85F038bBE3641736c23B1cc2e083e79a'
    }
  ],
  ddrs: [
    {
      tokenId: '4',
      patientDID: '0x7fc8cDB68e25B6Aa83Cbdf81B4adDBa3e58496be',
      ddrId: '004',
      hashValue: '0x292383490336287f71b0803c84828243418c4e70fb392679f2c0e5abb0772177'
    }
  ]
};
```

---

### mintBatchDDR

```ts
ddr.mintBatchDDR(hashValues, ddrIds, uris, patientDID, delegateKey, nonce?, isSimulate?);
```

Create many DDRs for Patients.
 
#### Parameters

1. [!badge variant="warning" text="hashValues"] - [!badge variant="warning" text="Array\<String>"]: List datas of DDR were hashed by the keccak256 from Pharumo.
2. [!badge variant="warning" text="ddrIds"] - [!badge variant="warning" text="Array\<String>"]: List of ids offline was sent from Pharumo.
3. [!badge variant="warning" text="uris"] - [!badge variant="warning" text="Array\<String>"]: List of uris of DDR.
4. [!badge variant="warning" text="patientDID"] - [!badge variant="warning" text="string"]: Address of Patient was created from DID.
5. [!badge variant="warning" text="delegateKey"] - [!badge variant="warning" text="string"]: Private key of delegateKey.
6. [!badge variant="warning" text="nonce"] - [!badge variant="warning" text="number"] (optional): The nonce of account.
7. [!badge variant="warning" text="isSimulate"] - [!badge variant="warning" text="boolean"] (optional): Emulator status.

#### Returns

1. [!badge variant="danger" text="receipt"] - [!badge variant="danger" text="object"]: A transaction receipt object, or null if no receipt was found. (check receipt).
2. [!badge variant="danger" text="eventLogs"] - [!badge variant="danger" text="array"]: An array of event logs of transactions.
3. [!badge variant="danger" text="ddrs"] - [!badge variant="danger" text="array"]: An array of object.

#### Example

```ts
ddr.mintBatchDDR(
        [
          "0xfa850c469e754b656ebf155b4b520e960d69baff52da021c9afbf26cb3a71c31",
          "0x94f5115f6287e66e3fc9bbd6e4f621f7657efd388e304c810ce7d381b654f59f",
          "0x292383490336287f71b0803c84828243418c4e70fb392679f2c0e5abb0772177"
        ],
        ["001","002","003"],
        ["xxx","yyy","zzz"],
        "0x91a6eBbDF60316065a9b0ddBeBB10e0fb51F3218",
        "24118478a12cd8e910ec3ae69edc8bda17c70754dd00d13f28dda0aa0f8644bb"
    )
  .then(console.log);
> {
    root: '0x0000000000000000000000000000000000000000000000000000000000000000',
    cumulativeGasUsed: 1516067,
    logsBloom: '0x04000000000000000000020000000000000000000000000000001000000000000000000008000000000000000000000000000000020001000000000000040002000000000000000000000008000000000000000000040000000000000200000100000000020040000000000000000800000000001040000000000010
020000000040000000000000000000200000004000042080000000000000000000000000000000000000801000000100010000000000000000800000000000000000400000000002000000000000000100000000800000000000000000000000000060000000000000000000000000000000000000000000008000010000000000000000',
    logs: [
      [Object], [Object],
      [Object], [Object],
      [Object], [Object],
      [Object]
    ],
    status: true,
    transactionHash: '0xf7f4245575c6824db9a66f703442cf39f5279044aad82e35a195ec597f2aefaa',
    transactionIndex: 0,
    blockHash: '0xb3d4f0d8d03bb5337d299a60bdc7cc8c67fb63d3852d3ebcb810499b711c0843',
    blockNumber: 2035122,
    gasUsed: 1516067,
    contractAddress: null,
    from: '0x51C4B0487e16186da402daebE06C4cD71b5015c8',
    to: '0xb007880f85F038bBE3641736c23B1cc2e083e79a'
  },
  eventLogs: [
    {
      name: 'ExecutionRequested',
      events: [Array],
      address: '0xb007880f85F038bBE3641736c23B1cc2e083e79a'
    },
    {
      name: 'Approved',
      events: [Array],
      address: '0xb007880f85F038bBE3641736c23B1cc2e083e79a'
    },
    {
      name: 'Transfer',
      events: [Array],
      address: '0x49417fbd8830A333136d2Eb04eb4988eb11F03fF'
    },
    {
      name: 'Transfer',
      events: [Array],
      address: '0x49417fbd8830A333136d2Eb04eb4988eb11F03fF'
    },
    {
      name: 'Transfer',
      events: [Array],
      address: '0x49417fbd8830A333136d2Eb04eb4988eb11F03fF'
    },
    {
      name: 'MintedBatchDDR',
      events: [Array],
      address: '0x49417fbd8830A333136d2Eb04eb4988eb11F03fF'
    },
    {
      name: 'Executed',
      events: [Array],
      address: '0xb007880f85F038bBE3641736c23B1cc2e083e79a'
    }
  ],
  ddrs: [
    {
      tokenId: '1',
      patientDID: '0x7fc8cDB68e25B6Aa83Cbdf81B4adDBa3e58496be',
      ddrId: '001',
      hashValue: '0xfa850c469e754b656ebf155b4b520e960d69baff52da021c9afbf26cb3a71c31'
    },
    {
      tokenId: '2',
      patientDID: '0x7fc8cDB68e25B6Aa83Cbdf81B4adDBa3e58496be',
      ddrId: '002',
      hashValue: '0x94f5115f6287e66e3fc9bbd6e4f621f7657efd388e304c810ce7d381b654f59f'
    },
    {
      tokenId: '3',
      patientDID: '0x7fc8cDB68e25B6Aa83Cbdf81B4adDBa3e58496be',
      ddrId: '003',
      hashValue: '0x292383490336287f71b0803c84828243418c4e70fb392679f2c0e5abb0772177'
    }
  ]
};
```

---

### sharedDDR

```ts
ddr.sharedDDR(ddrIds, patientDID, delegateKey, nonce?, isSimulate?);
```

Allow address of patient to access id of ddr.

#### Parameters

1. [!badge variant="warning" text="ddrIds"] - [!badge variant="warning" text="Array\<string>"]: Array of DDR Id off-chain was sent from Pharumo..
2. [!badge variant="warning" text="patientDID"] - [!badge variant="warning" text="string"]: Address of Patient was created from DID.
3. [!badge variant="warning" text="delegateKey"] - [!badge variant="warning" text="string"]: Private key of delegateKey.
4. [!badge variant="warning" text="nonce"] - [!badge variant="warning" text="number"] (optional): The nonce of account.
5. [!badge variant="warning" text="isSimulate"] - [!badge variant="warning" text="boolean"] (optional): Emulator status.

#### Returns

1. [!badge variant="danger" text="receipt"] - [!badge variant="danger" text="object"]: A transaction receipt object, or null if no receipt was found. (check receipt).
2. [!badge variant="danger" text="eventLogs"] - [!badge variant="danger" text="array"]: An array of event logs of transactions.

#### Example

```ts
ddr.sharedDDR(
        ["001","002","003"],
        "0x91a6eBbDF60316065a9b0ddBeBB10e0fb51F3218",
        "24118478a12cd8e910ec3ae69edc8bda17c70754dd00d13f28dda0aa0f8644bb"
    )
  .then(console.log);

>{
  receipt: {
    root: '0x0000000000000000000000000000000000000000000000000000000000000000',
    cumulativeGasUsed: 384463,
    logsBloom: '0x04000000000000000080020400000000000000080002000000000000000000000000000080000000000000000000000000000000800001000000000000200000000000000040000000000008000000000000000000000000000010020100000000000800020048000000000000000800000000001040200000000010000000000000000000000000000000200000004000002000000000000010000000080000020000000000800000000100080000000000002800000100000000080000400000000002000000000000000000000080800000000000000000000000000020000010002000040000000000000000000000000000008000000000000000000000',
    logs: [
      [Object], [Object],
      [Object], [Object],
      [Object], [Object],
      [Object]
    ],
    status: true,
    transactionHash: '0x2184e79bbe9db4cea86a4d7a467b6dc37a6589d16c0c4a03733e6c111e2d288f',
    transactionIndex: 0,
    blockHash: '0xf5ac2987e64a18588a445e744523310de3fc112545e01c109d264d02372368cc',
    blockNumber: 1980032,
    gasUsed: 384463,
    contractAddress: null,
    from: '0x51C4B0487e16186da402daebE06C4cD71b5015c8',
    to: '0x0365a7EEd6eaD34037F8E47c023aD9aa6C56F0cD'
  },
  eventLogs: [
    {
      name: 'ExecutionRequested',
      events: [Array],
      address: '0x0365a7EEd6eaD34037F8E47c023aD9aa6C56F0cD'
    },
    {
      name: 'Approved',
      events: [Array],
      address: '0x0365a7EEd6eaD34037F8E47c023aD9aa6C56F0cD'
    },
    {
      name: 'ApprovalShareDDR',
      events: [Array],
      address: '0xaD3dAf99B78936064E2C4841338766Cb61e7A6Bc'
    },
    {
      name: 'Approval',
      events: [Array],
      address: '0xDa46c687723751af0e7266A8A32eBe34E21070F0'
    },
    {
      name: 'Transfer',
      events: [Array],
      address: '0xDa46c687723751af0e7266A8A32eBe34E21070F0'
    },
    {
      name: 'AwardedToken',
      events: [Array],
      address: '0x1F8F8467478554CB8a0BB541E35b2Db7B5042648'
    },
    {
      name: 'Executed',
      events: [Array],
      address: '0x0365a7EEd6eaD34037F8E47c023aD9aa6C56F0cD'
    }
  ]
};
```

---

---

### getDDR

```ts
ddr.getDDR(patientDID, ddrId);
```

Get the ddr with certain ddr id.

#### Parameters

1. [!badge variant="warning" text="patientDID"] - [!badge variant="warning" text="string"]: Address of Patient was created from DID.
2. [!badge variant="warning" text="ddrId"] - [!badge variant="warning" text="string"]: DDR Id off-chain was sent from Pharumo.

#### Returns

1. [!badge variant="danger" text="tokenId"] - [!badge variant="danger" text="string"]: Token Id of ddr.
2. [!badge variant="danger" text="patientDID"] - [!badge variant="danger" text="string"]: Address of Patient was created from DID.
3. [!badge variant="danger" text="ddrId"] - [!badge variant="danger" text="string"]: DDR Id off-chain was sent from Pharumo.
4. [!badge variant="danger" text="hashValue"] - [!badge variant="danger" text="string"]: Data of DDR was hashed by the keccak256 from Pharumo.
5. [!badge variant="danger" text="didConsentedOf"] - [!badge variant="danger" text="string"]: Array providers address shared by patient.


#### Example

```ts
ddr.getDDR("0x91a6eBbDF60316065a9b0ddBeBB10e0fb51F3218","001")
  .then(console.log);
> Result {
  '0': '1',
  '1': '0x7fc8cDB68e25B6Aa83Cbdf81B4adDBa3e58496be',
  '2': '001',
  '3': '0xfa850c469e754b656ebf155b4b520e960d69baff52da021c9afbf26cb3a71c31',
  '4': [],
  tokenId: '1',
  patientDID: '0x7fc8cDB68e25B6Aa83Cbdf81B4adDBa3e58496be',
  ddrId: '001',
  hashValue: '0xfa850c469e754b656ebf155b4b520e960d69baff52da021c9afbf26cb3a71c31',
}
```
---
---

### getAllDDR

```ts
ddr.getAllDDR(patientDID);
```

Get all the ddr

#### Parameters

[!badge variant="warning" text="patientDID"] - [!badge variant="warning" text="string"]: Address of Patient was created from DID.


#### Returns

1. [!badge variant="danger" text="tokenId"] - [!badge variant="danger" text="string"]: Token Id of ddr.
2. [!badge variant="danger" text="patientDID"] - [!badge variant="danger" text="string"]: Address of Patient was created from DID.
3. [!badge variant="danger" text="ddrId"] - [!badge variant="danger" text="string"]: DDR Id off-chain was sent from Pharumo.
4. [!badge variant="danger" text="hashValue"] - [!badge variant="danger" text="string"]: Data of DDR was hashed by the keccak256 from Pharumo.
5. [!badge variant="danger" text="didConsentedOf"] - [!badge variant="danger" text="string"]: Array providers address shared by patient.


#### Example

```ts
ddr.getAllDDR("0xd0a2926d4f07121c3a29EbdFF514556a82Cb9F7C")
  .then(console.log);

> [
  Result {
    '0': '1',
    '1': '0x7fc8cDB68e25B6Aa83Cbdf81B4adDBa3e58496be',
    '2': '001',
    '3': '0xfa850c469e754b656ebf155b4b520e960d69baff52da021c9afbf26cb3a71c31',
    '4': [],
    tokenId: '1',
    patientDID: '0x7fc8cDB68e25B6Aa83Cbdf81B4adDBa3e58496be',
    ddrId: '001',
    hashValue: '0xfa850c469e754b656ebf155b4b520e960d69baff52da021c9afbf26cb3a71c31',
    didConsentedOf: []
  },
  Result {
    '0': '2',
    '1': '0x7fc8cDB68e25B6Aa83Cbdf81B4adDBa3e58496be',
    '2': '002',
    '3': '0x94f5115f6287e66e3fc9bbd6e4f621f7657efd388e304c810ce7d381b654f59f',
    '4': [],
    tokenId: '2',
    patientDID: '0x7fc8cDB68e25B6Aa83Cbdf81B4adDBa3e58496be',
    ddrId: '002',
    hashValue: '0x94f5115f6287e66e3fc9bbd6e4f621f7657efd388e304c810ce7d381b654f59f',
    didConsentedOf: []
  },
  Result {
    '0': '3',
    '1': '0x7fc8cDB68e25B6Aa83Cbdf81B4adDBa3e58496be',
    '2': '003',
    '3': '0x292383490336287f71b0803c84828243418c4e70fb392679f2c0e5abb0772177',
    '4': [],
    tokenId: '3',
    patientDID: '0x7fc8cDB68e25B6Aa83Cbdf81B4adDBa3e58496be',
    ddrId: '003',
    hashValue: '0x292383490336287f71b0803c84828243418c4e70fb392679f2c0e5abb0772177',
  },
  Result {
    '0': '4',
    '1': '0x7fc8cDB68e25B6Aa83Cbdf81B4adDBa3e58496be',
    '2': '004',
    '3': '0x292383490336287f71b0803c84828243418c4e70fb392679f2c0e5abb0772177',
    '4': [],
    tokenId: '4',
    patientDID: '0x7fc8cDB68e25B6Aa83Cbdf81B4adDBa3e58496be',
    ddrId: '004',
    hashValue: '0x292383490336287f71b0803c84828243418c4e70fb392679f2c0e5abb0772177',
  }
]
```
---

### consentDisclosureDDR

```ts
ddr.consentDisclosureDDR(ddrIds, providerDID, patientDID, addressOfDelegateKey, nonce);
```

Allow list ids of ddr to provider.

#### Parameters

1. [!badge variant="warning" text="ddrIds"] - [!badge variant="warning" text="Array\<string>"]: List of DDR id.
3. [!badge variant="warning" text="providerDID"] - [!badge variant="warning" text="string"]: The address of provider was created from DID.
2. [!badge variant="warning" text="patientDID"] - [!badge variant="warning" text="string"]: Address of Patient was created from DID.
4. [!badge variant="warning" text="addressOfDelegateKey"] - [!badge variant="warning" text="string"]: The address of delegate key.
5. [!badge variant="warning" text="nonce"] - [!badge variant="warning" text="number"] (optional): The nonce of account.

#### Returns

1. [!badge variant="danger" text="receipt"] - [!badge variant="danger" text="object"]: A transaction receipt object, or null if no receipt was found. (check receipt).
2. [!badge variant="danger" text="eventLogs"] - [!badge variant="danger" text="array"]: An array of event logs of transactions.

#### Example

```ts
ddr.consentDisclosureDDR(
    ["A001", "A002"],
    "0x7Aaf39BBD7Dd755EaA50F992522A4Eb3d8cd75a0",
    "0x37C819C94EdfE048968A28215C73C4D1B8ceAb15",
    "24118478a12cd8e910ec3ae69edc8bda17c70754dd00d13f28dda0aa0f8644bb"
  )
  .then(console.log);
> {
  to: '0x91a6eBbDF60316065a9b0ddBeBB10e0fb51F3218',
  from: '0x51C4B0487e16186da402daebE06C4cD71b5015c8',
  gas: 650658,
  gasPrice: '0',
  nonce: 3953,
  data: '0xb61d27f6000000000000000000000000ad3daf99b78936064e2c4841338766cb61e7a6bc0000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000006000000000000000000000000000000000000000000000000000000000000000c43b88f7370000000000000000000000000000000000000000000000000000000000000040000000000000000000000000180e111d0a48cc4ad80be7e2f113d556a1c751d0000000000000000000000000000000000000000000000000000000000000000300000000000000000000000000000000000000000000000000000000000000010000000000000000000000000000000000000000000000000000000000000002000000000000000000000000000000000000000000000000000000000000000300000000000000000000000000000000000000000000000000000000'
};
```

---

### getShareDDR

```ts
ddr.getShareDDR(patientDID, ddrId);
```

Check if this address of patient is allowed to contact DDR.

#### Parameters

1. [!badge variant="warning" text="patientDID"] - [!badge variant="warning" text="string"]: Address of Patient was created from DID.
2. [!badge variant="warning" text="ddrId"] - [!badge variant="warning" text="string"]: Id of DDR.

#### Returns

[!badge variant="danger" text="boolean"] : Check if address is allowed or not.

#### Example

```ts
ddr.getShareDDR("0x7Aaf39BBD7Dd755EaA50F992522A4Eb3d8cd75a0", "A001").then(console.log);
> true;
```

---

### getConsentedDDR

```ts
ddr.getConsentedDDR(providerDID, patientDID, ddrId);
```

Check if this address of provideris allowed to watch ddr.

#### Parameters

1. [!badge variant="warning" text="providerDID"] - [!badge variant="warning" text="string"]: The DID address of provider.
2. [!badge variant="warning" text="patientDID"] - [!badge variant="warning" text="string"]: The DID address of patient.
3. [!badge variant="warning" text="ddrId"] - [!badge variant="warning" text="number"]: Id of ddr.

#### Returns

[!badge variant="danger" text="boolean"] : Check if address is allowed or not.

#### Example

```ts
ddr.getConsentedDDR("0x37C819C94EdfE048968A28215C73C4D1B8ceAb15", "0x7Aaf39BBD7Dd755EaA50F992522A4Eb3d8cd75a0", "A001").then(console.log);
> true;
```

---

### getLockedDDR

```ts
ddr.getLockedDDR(patientDID, ddrId);
```

Check if this DDR is locked or not

#### Parameters

1. [!badge variant="warning" text="patientDID"] - [!badge variant="warning" text="string"]: The DID address of patient.
2. [!badge variant="warning" text="ddrId"] - [!badge variant="warning" text="string"]: Id of ddr.

#### Returns

[!badge variant="danger" text="Boolean"] : True is locked and false is unlocked.

#### Example

```ts
ddr.getLockedDDR("0x7Aaf39BBD7Dd755EaA50F992522A4Eb3d8cd75a0", "A001").then(console.log);
> true;
```

---

### setERC20Proxy

```ts
ddr.setERC20Proxy(addressErc20Proxy, privateKey, nonce);
```

Call contract ERC20Proxy to DDR

#### Parameters

1. [!badge variant="warning" text="addressErc20Proxy"] - [!badge variant="warning" text="string"]: Address of contract ERC20Proxy.
2. [!badge variant="warning" text="privateKey"] - [!badge variant="warning" text="string"]: Private key of contract creator(admin).
3. [!badge variant="warning" text="nonce"] - [!badge variant="warning" text="number"] (optional): The nonce of account.

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
```
