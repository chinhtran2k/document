---
icon: dot
---

# DDRBranch

This module for DDRBranch lock level

## Main function

---

### mintDDRBranch

```ts
mintDDRBranch(patientDID, uri, privateKey, nonce?);
```

Mint Lock DDRBranch.

#### Parameters

1. [!badge variant="warning" text="patientDID"] - [!badge variant="warning" text="string"]: Address of Patient was created from DID.
2. [!badge variant="warning" text="uri"] - [!badge variant="warning" text="string"]: The uri of DDRBranch.
3. [!badge variant="warning" text="privateKey"] - [!badge variant="warning" text="string"] : Private key of contract creator(admin).
4. [!badge variant="warning" text="nonce"] - [!badge variant="warning" text="number"] (optional): The nonce of account.

#### Returns

1. [!badge variant="danger" text="receipt"] - [!badge variant="danger" text="object"]: A transaction receipt object, or null if no receipt was found. (check receipt).
2. [!badge variant="danger" text="eventLogs"] - [!badge variant="danger" text="object"]: Event logs of transactions.
3. [!badge variant="danger" text="tokenId"] - [!badge variant="danger" text="string"]: Id of DDRBranch token.
3. [!badge variant="danger" text="hashValue"] - [!badge variant="danger" text="string"]: Data lock was hashed by the keccak256.

#### Example

```ts
ddrBranch.mintDDRBranch("0x91a6eBbDF60316065a9b0ddBeBB10e0fb51F3218",
                        "xxx",
                        "24118478a12cd8e910ec3ae69edc8bda17c70754dd00d13f28dda0aa0f8644bb")
  .then(console.log);
> {
  receipt: {
    root: '0x0000000000000000000000000000000000000000000000000000000000000000',
    cumulativeGasUsed: 870955,
    logsBloom: '0x000000400000000000800004000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000400000000000000000000000000080000000000000000000400000000000000000000000000000a0000000000000000000800000000000000000000000010000000010000000000000000000000000000000000000000040000000010000000000000000000000000000000000000000000000000000000000000000000000000000000000002000000000000000002000000000000000000000000000000000060000000000000000000000080000000000000000000000000000000000000000000',
    logs: [ [Object], [Object] ],
    status: true,
    transactionHash: '0x4e1f2bbf65f02d41848b1319cee892bd6b8080f90bfd8fa08f87974f4bf3e632',
    transactionIndex: 0,
    blockHash: '0xafc95c196d2e559d62ec3885ffc5b262456cdfd663f344a238263352da7d4864',
    blockNumber: 1980129,
    gasUsed: 870955,
    contractAddress: null,
    from: '0x51C4B0487e16186da402daebE06C4cD71b5015c8',
    to: '0x6A6a35681485B696b37536434F1d02C5D95ed601'
  },
  eventLogs: [
    {
      name: 'Transfer',
      events: [Array],
      address: '0x6A6a35681485B696b37536434F1d02C5D95ed601'
    },
    {
      name: 'DDRBranchLockTokenMinted',
      events: [Array],
      address: '0x6A6a35681485B696b37536434F1d02C5D95ed601'
    }
  ],
  tokenId: '1',
  hashValue: '0x2eadc11ccd60248cc645917801e0ec1c98f911bb18da8e43578373dbec33aa99'
}
```

---

### getListRootHashDDR

```ts
getListRootHashDDR();
```

Get List Root Hash Value Of DDRBranch.

#### Parameters

None.

#### Returns

[!badge variant="danger" text="Array\<String>"]: Array of Hash Value.

#### Example

```ts
ddrBranch.getListRootHashDDR().then(console.log);
> [
  '0x2eadc11ccd60248cc645917801e0ec1c98f911bb18da8e43578373dbec33aa99',
  '0x483db9b9ed09826ac41db149e18f28e009de096483f1851cea0db7e17cacdf9d',
  '0xb078fc58f56dd0124442fae3e143e0ec69938d171694856bdf09602f7f9f07af'
  ]
```

---

---

### getAllHashDDROfPatient

```ts
getAllHashDDROfPatient(Patient);
```

Get All Hash Value DDRBranh Of Patient.

#### Parameters

[!badge variant="warning" text="patientDID"] - [!badge variant="warning" text="string"]: Address of PatientDID was created from DID.

#### Returns

[!badge variant="danger" text="Array\<String>"] - [!badge variant="warning" text="string"]: Get all hash value ddrBranch of patient.
#### Example

```ts
patient.getAllHashDDROfPatient('0x91a6eBbDF60316065a9b0ddBeBB10e0fb51F3218').then(console.log);

> [
  '0x2eadc11ccd60248cc645917801e0ec1c98f911bb18da8e43578373dbec33aa99',
  '0xb078fc58f56dd0124442fae3e143e0ec69938d171694856bdf09602f7f9f07af'
  ]
```

---

### getListTokenId

```ts
getListTokenId(patientDID);
```

Get All TokenID DDRBranh Of Patient.

#### Parameters

[!badge variant="warning" text="patientDID"] - [!badge variant="warning" text="string"]: Address of PatientDID was created from DID.

#### Returns

[!badge variant="danger" text="Array\<String>"] - [!badge variant="warning" text="string"]: Get all tokenId ddrBranch of patient.
#### Example

```ts
patient.getListTokenId('0x91a6eBbDF60316065a9b0ddBeBB10e0fb51F3218').then(console.log);

> [ '1', '2' ]
```

---

