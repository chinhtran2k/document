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

1. [!badge variant="warning" text="patientDID"] - [!badge variant="warning" text="string"]: Address of patient was created from DID
2. [!badge variant="warning" text="uri"] - [!badge variant="warning" text="string"]: The uri of patient
3. [!badge variant="warning" text="privateKey"] - [!badge variant="warning" text="string"] : Private key of contract creator(admin)
4. [!badge variant="warning" text="nonce"] - [!badge variant="warning" text="number"] (optional): The nonce of account

#### Returns

1. [!badge variant="danger" text="receipt"] - [!badge variant="danger" text="object"]: A transaction receipt object, or null if no receipt was found. (check receipt).
2. [!badge variant="danger" text="eventLogs"] - [!badge variant="danger" text="object"]: Event logs of transactions.
3. [!badge variant="danger" text="tokenId"] - [!badge variant="danger" text="string"]: Id of Patient token.
4. [!badge variant="danger" text="hashValue"] - [!badge variant="danger" text="string"]: Hash lock was hashed by the keccak256.

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
    root: '0x0000000000000000000000000000000000000000000000000000000000000000',
    cumulativeGasUsed: 691847,
    logsBloom: '0x00000000000000000080040400000000000000000000000000000000000000000000000000000000000000000000000000000200000000000000000000040000000000000000000000000008020000000000000000040000000000000000000000000000020000000000000000000800000000000000000000000010
000000000000000080000000000000000000000000000000000000000010000000000080000000000000000000800000000000000000000000000000000000000000000000000002000000000000000000000000000000000000000000000000000060000000000000000000000000000000000000000000000000000000000000000000',
    logs: [ [Object], [Object] ],
    status: true,
    transactionHash: '0x322a70ccbf7dca1944ccf8081607a28d6aee0eb9f4fd656022ef6de69b978284',
    transactionIndex: 0,
    blockHash: '0x8ab5dbcb517c4cdd5c7885cceba6dbc2f99fc292f154aec4133bda78e4563ced',
    blockNumber: 1988310,
    gasUsed: 691847,
    contractAddress: null,
    from: '0x51C4B0487e16186da402daebE06C4cD71b5015c8',
    to: '0x709fA4284e17fD2729448F2EF162a1eB51A240DC'
  },
  eventLogs: [
    {
      name: 'Transfer',
      events: [Array],
      address: '0x709fA4284e17fD2729448F2EF162a1eB51A240DC'
    },
    {
      name: 'PatientLockTokenMinted',
      events: [Array],
      address: '0x709fA4284e17fD2729448F2EF162a1eB51A240DC'
    }
  ],
  tokenId: '1',
  hashValue: '0x182c94dc0e41f941c2327a5b500227d449e1ec85eedeea84e0740c54be2b42c1'
}
```

---

### getPatientRootHashValue

```ts
patient.getPatientRootHashValue(patientDID);
```

Get The Hash Value Of Patient

#### Parameters

[!badge variant="warning" text="patientDID"] - [!badge variant="warning" text="string"]: Address of patient was created from DID

#### Returns

[!badge variant="danger" text="String"]: Hash value of patient

#### Example

```ts
patient.getPatientRootHashValue("0x91a6eBbDF60316065a9b0ddBeBB10e0fb51F3218")
  .then(console.log);
> "0x182c94dc0e41f941c2327a5b500227d449e1ec85eedeea84e0740c54be2b42c1"
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
  '0x182c94dc0e41f941c2327a5b500227d449e1ec85eedeea84e0740c54be2b42c1',
  '0x49d59884178c25ac9d4122b49b94492f887374e8062f6f617729e0ca10bb4f14',
  '0xf2baf6d2f921e3bb7eb5e66d7a67d6caeaeb49691d0d681c3865d9b134f7e391'
]
```

---

---

### getListAddressPatient

```ts
patient.getListAddressPatient(patientDID);
```

Get All Address Of Patient.

#### Parameters

None

#### Returns

[!badge variant="danger" text="Array\<String>"]: Array address of patient.
#### Example

```ts
patient.getListAddressPatient().then(console.log);

> [ 
  '0x91a6eBbDF60316065a9b0ddBeBB10e0fb51F3218',
  '0xd0a2926d4f07121c3a29EbdFF514556a82Cb9F7C',
  '0x54fD56b9a4a8686F4855F5678F24DdFf196fC7CA'
   ]
```

---
