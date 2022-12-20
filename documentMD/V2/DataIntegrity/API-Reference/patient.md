---
icon: dot
---

# Patient

This module for Patient lock level

## Main function

---

### mintPatient

```ts
patient.mintPatient(patientDID, uri, privateKey, nonce);
```

Mint and lock Patient

#### Parameters

1. [!badge variant="warning" text="patientDID"] - [!badge variant="warning" text="string"]: Address of Patient was created from DID
2. [!badge variant="warning" text="uri"] - [!badge variant="warning" text="string"]: The uri of patient
3. [!badge variant="warning" text="privateKey"] - [!badge variant="warning" text="string"] : Private key of contract creator(admin)
4. [!badge variant="warning" text="nonce"] - [!badge variant="warning" text="number"] (optional): The nonce of account

#### Returns

1. [!badge variant="danger" text="receipt"] - [!badge variant="danger" text="object"]: A transaction receipt object, or null if no receipt was found. (check receipt).
2. [!badge variant="danger" text="eventLogs"] - [!badge variant="danger" text="object"]: Event logs of transactions.
3. [!badge variant="danger" text="tokenId"] - [!badge variant="danger" text="string"]: Id of Patient token.

#### Example

```ts
patient.mintPatient(
    "0x7Aaf39BBD7Dd755EaA50F992522A4Eb3d8cd75a0",
    "gg",
    "24118478a12cd8e910ec3ae69edc8bda17c70754dd00d13f28dda0aa0f8644bb"
  )
  .then(console.log);
> {
  receipt: {
    root: "0x0000000000000000000000000000000000000000000000000000000000000000",
    cumulativeGasUsed: 1210878,
    logsBloom:
      "0x00000000000000000080040400000000000000000000000000000000200000000000000000000802000000000000000000000200000080000000000000000000000000000000000000000008000000000000000000000000000000000000000000000000020000000000000000000800000000000000000000000010000000000080000080000000000000000000000000000000000000000010000000000000000000000000000000000000000000000000000000000000000000000000000040000002000000000000000000000000000000000000000000000000000020000000000000000000000000000000000000000000000000000000000000000000",
    logs: [[Object], [Object]],
    status: true,
    transactionHash:
      "0x1eee8a69ab89b1206dee736b1115feccee41bbe43c8bb5fc9a6f204c66ab6bf3",
    transactionIndex: 0,
    blockHash:
      "0x9375085f4e86a80aed5734ce96fbf0317a77230e8dc0c476b82f93b4a949d659",
    blockNumber: 1654534,
    gasUsed: 1210878,
    contractAddress: null,
    from: "0x51C4B0487e16186da402daebE06C4cD71b5015c8",
    to: "0xBC5D5AFBeb63446a2C3BF1a72213Ca8E92fEdfFc",
  },
  eventLogs: [
    {
      name: "Transfer",
      events: [Array],
      address: "0xBC5D5AFBeb63446a2C3BF1a72213Ca8E92fEdfFc",
    },
    {
      name: "PatientLockTokenMinted",
      events: [Array],
      address: "0xBC5D5AFBeb63446a2C3BF1a72213Ca8E92fEdfFc",
    },
  ],
  tokenId: "8",
  hashValue: '0xd27c798b1a6acf164ecccc0c3a501a88f0007f350905663ffc4ee8911fc764c9'
}
```

---

### getPatientRootHashValue

```ts
patient.getPatientRootHashValue(patientDID);
```

Get The Hash Value Of Patient

#### Parameters

[!badge variant="warning" text="patientDID"] - [!badge variant="warning" text="string"]: Address of Patient was created from DID

#### Returns

[!badge variant="danger" text="String"]: Hash Value of Patient

#### Example

```ts
patient.getPatientRootHashValue("0x7Aaf39BBD7Dd755EaA50F992522A4Eb3d8cd75a0")
  .then(console.log);
> "0xf1b58baf6d7650f6e7571ee0393e50619d4da8b02864d118cc44e3a6d894cbae"
```

---

### getListRootHashValue

```ts
patient.getListRootHashValue();
```

Get List Of Hash Value

#### Parameters

None

#### Returns

[!badge variant="danger" text="Array\<String>"]: Array of Hash Value

#### Example

```ts
patient.getListRootHashValue().then(console.log);
>[
  "0xc599d44fdb3d96d54427a825cdcadb3dc2e89902d33bdb64272005a1fe9fb030",
  "0xc599d44fdb3d96d54427a825cdcadb3dc2e89902d33bdb64272005a1fe9fb030",
  "0xc599d44fdb3d96d54427a825cdcadb3dc2e89902d33bdb64272005a1fe9fb030",
  "0xc599d44fdb3d96d54427a825cdcadb3dc2e89902d33bdb64272005a1fe9fb030",
  "0xc599d44fdb3d96d54427a825cdcadb3dc2e89902d33bdb64272005a1fe9fb030",
  "0xc599d44fdb3d96d54427a825cdcadb3dc2e89902d33bdb64272005a1fe9fb030",
  "0xc599d44fdb3d96d54427a825cdcadb3dc2e89902d33bdb64272005a1fe9fb030",
  "0xf1b58baf6d7650f6e7571ee0393e50619d4da8b02864d118cc44e3a6d894cbae",
  "0xf1b58baf6d7650f6e7571ee0393e50619d4da8b02864d118cc44e3a6d894cbae",
]
```

---

---

### getHashClaim

```ts
patient.getHashClaim(patientDID);
```

Get Claim Data Was Hashed By Keccak256

#### Parameters

[!badge variant="warning" text="patientDID"] - [!badge variant="warning" text="string"]: Address of Patient was created from DID

#### Returns

[!badge variant="warning" text="hashedValue"] - [!badge variant="warning" text="string"]: Claim Data was hashed by keccak256
#### Example

```ts
patient.getHashClaim('0xd0a2926d4f07121c3a29EbdFF514556a82Cb9F7C').then(console.log);

> 0x2695156ad586fff58bd6938d09897d9b1392afd1f65d0a9310890250e46b7c29
```

---
