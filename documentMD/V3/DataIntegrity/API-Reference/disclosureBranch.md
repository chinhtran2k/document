---
icon: dot
---

# DisclosureBranch

This module for Consented Disclosure lock level

## Main function

---

### mintDDRBranch

```ts
mintDisclosureBranch(patientDID, providerDID, uri, privateKey, nonce?);
```

Mint Lock DisclosureBranch.

#### Parameters

1. [!badge variant="warning" text="patientDID"] - [!badge variant="warning" text="string"]: Address of patient was created from DID.
2. [!badge variant="warning" text="providerDID"] - [!badge variant="warning" text="string"]: Address of provider was created from DID.
3. [!badge variant="warning" text="uri"] - [!badge variant="warning" text="string"]: The uri of DisclosureBranch.
4. [!badge variant="warning" text="privateKey"] - [!badge variant="warning" text="string"] : Private key of contract creator(admin).
5. [!badge variant="warning" text="nonce"] - [!badge variant="warning" text="number"] (optional): The nonce of account.

#### Returns

1. [!badge variant="danger" text="receipt"] - [!badge variant="danger" text="object"]: A transaction receipt object, or null if no receipt was found. (check receipt).
2. [!badge variant="danger" text="eventLogs"] - [!badge variant="danger" text="object"]: Event logs of transactions.
3. [!badge variant="danger" text="tokenId"] - [!badge variant="danger" text="string"]: Id of DDRBranch token.
3. [!badge variant="danger" text="hashValue"] - [!badge variant="danger" text="string"]: Hash lock was hashed by the keccak256.

#### Example

```ts
disclosureBranch.mintDisclosureBranch("0x91a6eBbDF60316065a9b0ddBeBB10e0fb51F3218",
                                    "0x54fD56b9a4a8686F4855F5678F24DdFf196fC7CA",
                                    "xxx",
                                    "24118478a12cd8e910ec3ae69edc8bda17c70754dd00d13f28dda0aa0f8644bb")
  .then(console.log);
> {
  receipt: {
    root: '0x0000000000000000000000000000000000000000000000000000000000000000',
    cumulativeGasUsed: 873419,
    logsBloom: '0x00000000000000000080000400000000000000000000000000100000000000001000000000000000000000000000000000000000000000000000000000040000010000000000000000000008000000000000000000040000000000000000000000000000020200000000000000000800000000000010000000000010000000000000000000000000000000000000000000000000000000000010000000000000000000000000000000000000000000000000020000000000000000000000000000000002000000000000000000000000000000000000000000000000000060000000000000000000000000000000000000000000000000000000000000000000',
    logs: [ [Object], [Object] ],
    status: true,
    transactionHash: '0xd69569a667e18c51d00e5137bb62ddc1546e50e661e2d5ffe2b0c6a3ccd53f15',
    transactionIndex: 0,
    blockHash: '0x13253203038cc36c725f27c2854139bd0034763e58500806233fac49f5491f11',
    blockNumber: 1980449,
    gasUsed: 873419,
    contractAddress: null,
    from: '0x51C4B0487e16186da402daebE06C4cD71b5015c8',
    to: '0x41Cc3F52C322eF03f674FcDA1Da174f11ee43811'
  },
  eventLogs: [
    {
      name: 'Transfer',
      events: [Array],
      address: '0x41Cc3F52C322eF03f674FcDA1Da174f11ee43811'
    },
    {
      name: 'DisclosureLockTokenMinted',
      events: [Array],
      address: '0x41Cc3F52C322eF03f674FcDA1Da174f11ee43811'
    }
  ],
  tokenId: '1',
  hashValue: '0xa9cdea49d5fd6c57f8d0f3ae7a70501f485d1988f60489c97aad85fc079f7fa2'
}
```

---

### getListRootHashDisclosure

```ts
getListRootHashDisclosure();
```

Get List Root Hash Value Of DisclosureBranch.

#### Parameters

None.

#### Returns

[!badge variant="danger" text="Array\<String>"]: Array of Hash Value.

#### Example

```ts
disclosureBranch.getListRootHashDisclosure().then(console.log);
> [
  '0xa9cdea49d5fd6c57f8d0f3ae7a70501f485d1988f60489c97aad85fc079f7fa2',
  '0x23655f38d9037e5b5729ad85abd53c2a0a5e2f0635a6e40d36639ee78109d79b',
  '0xc97e95795801caa9eb4340b95a949a203c67f91c25f7a3e2d69fb72f72644259'
  ]
```

---

---

### getAllHashDDROfPatient

```ts
getAllHashDisclosureBranchOfPatient(patientDID);
```

Get All Hash Value DisclosureBranch Of Patient.

#### Parameters

[!badge variant="warning" text="patientDID"] - [!badge variant="warning" text="string"]: Address of patient was created from DID.

#### Returns

[!badge variant="danger" text="Array\<String>"] - [!badge variant="warning" text="string"]: Get all hash value Disclosure of patient.
#### Example

```ts
disclosureBranch.getAllHashDisclosureBranchOfPatient('0x91a6eBbDF60316065a9b0ddBeBB10e0fb51F3218').then(console.log);

> [
  '0xa9cdea49d5fd6c57f8d0f3ae7a70501f485d1988f60489c97aad85fc079f7fa2',
  '0xc97e95795801caa9eb4340b95a949a203c67f91c25f7a3e2d69fb72f72644259'
  ]
```

---

### getListTokenId

```ts
getListTokenId(patientDID);
```

Get All TokenID Disclosure Of Patient.

#### Parameters

[!badge variant="warning" text="patientDID"] - [!badge variant="warning" text="string"]: Address of Patient was created from DID

#### Returns

[!badge variant="danger" text="Array\<String>"] - [!badge variant="warning" text="string"]: Get all tokenId ddrBranch of patient.
#### Example

```ts
disclosureBranch.getListTokenId('0x91a6eBbDF60316065a9b0ddBeBB10e0fb51F3218').then(console.log);

> [ '1', '2' ]
```

---

### getListHashDisclosureOfProvider

```ts
getListHashDisclosureOfProvider(providerDID);
```

Get All TokenID Disclosure Of Provider.

#### Parameters

[!badge variant="warning" text="providerDID"] - [!badge variant="warning" text="string"]: Address of provider was created from DID

#### Returns

[!badge variant="danger" text="Array\<String>"] - [!badge variant="warning" text="string"]: Get all tokenId ddrBranch of patient.
#### Example

```ts
disclosureBranch.getListHashDisclosureOfProvider('0x91a6eBbDF60316065a9b0ddBeBB10e0fb51F3218').then(console.log);

> [ '0xa9cdea49d5fd6c57f8d0f3ae7a70501f485d1988f60489c97aad85fc079f7fa2', '0x23655f38d9037e5b5729ad85abd53c2a0a5e2f0635a6e40d36639ee78109d79b' ]
```

---

