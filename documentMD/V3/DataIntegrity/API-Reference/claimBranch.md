---
icon: dot
---

# ClaimBranch

This module for claim lock level.

## Main function

---

### mintClaim

```ts
claim.mintClaim(accountDID, accountId, uri, privateKey, nonce?, isSimulate?);
```

Mint and lock CLaim.

#### Parameters

1. [!badge variant="warning" text="accountDID"] - [!badge variant="warning" text="string"]: Address of provider/patient was created from DID.
2. [!badge variant="warning" text="accountId"] - [!badge variant="warning" text="string"]: Account Id off-chain was sent from Pharumo.
3. [!badge variant="warning" text="uri"] - [!badge variant="warning" text="string"]: The uri of provider/patient.
4. [!badge variant="warning" text="privateKey"] - [!badge variant="warning" text="string"] : Private key of contract creator(admin).
5. [!badge variant="warning" text="nonce"] - [!badge variant="warning" text="number"] (optional): The nonce of account.
6. [!badge variant="warning" text="isSimulate"] - [!badge variant="warning" text="boolean"] (optional): Emulator status.

#### Returns

1. [!badge variant="danger" text="receipt"] - [!badge variant="danger" text="object"]: A transaction receipt object, or null if no receipt was found (check receipt).
2. [!badge variant="danger" text="eventLogs"] - [!badge variant="danger" text="object"]: Event logs of transactions.
3. [!badge variant="danger" text="tokenId"] - [!badge variant="danger" text="string"]: Id of Provider token.
3. [!badge variant="danger" text="hashValue"] - [!badge variant="danger" text="string"]: Hash Value lock of claim was hashed by the keccak256.

#### Example

```ts
claim.mintClaim(
    "0xA3Eb367f4375Beb2ce4fE03C95Bd17E1B0E23A9c",
    "PT01",
    "uri accountDID",
    "24118478a12cd8e910ec3ae69edc8bda17c70754dd00d13f28dda0aa0f8644bb"
  )
  .then(console.log);
> {
    root: '0x0000000000000000000000000000000000000000000000000000000000000000',
    cumulativeGasUsed: 466453,
    logsBloom: '0x00000000000000000080000400000000004000000000000000000000000000000000000000000000000000000000000000000000000000000000000000040000000000000000000000000008000000000000000000040000000000000000000000000000021000000000004000000800000000000000000000000010000200000000000400000000010000000000000000000000000000000010000400000000000000000000000000000000000000000000000000000000000000000000000000000002000000000000000000000000000000000000000000000200080060000000000000000000000000000000000000000000000000000000000000000000',
    logs: [ [Object], [Object], [Object] ],
    status: true,
    transactionHash: '0x713bd596c7f2b29a7104d9c9f9e148f67d7910ef597b72b66ca98b61da9e0aaf',
    transactionIndex: 0,
    blockHash: '0x7ed708ebc2dd45b0e59934d1d95dbde1398f6abae6f6376093586a83546a6ff9',
    blockNumber: 1990457,
    gasUsed: 466453,
    contractAddress: null,
    from: '0x51C4B0487e16186da402daebE06C4cD71b5015c8',
    to: '0xCB805208DfA4966B14B1CfAf05a5d899ADF24d1b'
  },
  eventLogs: [
    {
      name: 'Transfer',
      events: [Array],
      address: '0xCB805208DfA4966B14B1CfAf05a5d899ADF24d1b'
    },
    {
      name: 'ClaimLockTokenMinted',
      events: [Array],
      address: '0xCB805208DfA4966B14B1CfAf05a5d899ADF24d1b'
    },
    {
      name: 'ClaimTokenLocked',
      events: [Array],
      address: '0xCB805208DfA4966B14B1CfAf05a5d899ADF24d1b'
    }
  ],
  tokenId: '1',
  hashValue: '0xb643a5262d05b758a3b8977bf5d3690c6b3622ca98391d8ff3131ef9f84d50db'
}
```

---

### getListAddressOfClaim

```ts
claim.getListAddressOfClaim();
```

Get list address Of Claim

#### Parameters

None

#### Returns

[!badge variant="danger" text="String"]: Array address of claim.

#### Example

```ts
claim.getListAddressOfClaim()
  .then(console.log);
> [
     '0x9573Cda4F4f645764767561D1EF3b4b84647aC19',
     '0xA3Eb367f4375Beb2ce4fE03C95Bd17E1B0E23A9c'
  ]
```

---

### getHashValueClaim

```ts
claim.getHashValueClaim(accountDID);
```

Get Hash Value Of Claim.

#### Parameters

1. [!badge variant="warning" text="accountDID"] - [!badge variant="warning" text="string"]: Address of provider/patient was created from DID.

#### Returns

[!badge variant="danger" text="String"]: hash data was hashed claim lv1 by the keccak256.

#### Example

```ts
claim.getHashValueClaim("0x9573Cda4F4f645764767561D1EF3b4b84647aC19").then(console.log);
> "0x413febeb7faf0762a3c79ac10354ff4096db8ac927d64e9a81355e5671a6d6b9"
```

---

---

### getHashClaim

```ts
patient.getHashClaim(accountDID);
```

Get Claim Data.

#### Parameters

[!badge variant="warning" text="accountDID"] - [!badge variant="warning" text="string"]: Address of provider/patient was created from DID

#### Returns

[!badge variant="warning" text="hashedValue"] - [!badge variant="warning" text="string"]: Hash claim lock
#### Example

```ts
patient.getHashClaim('0x9573Cda4F4f645764767561D1EF3b4b84647aC19').then(console.log);

> 0x2695156ad586fff58bd6938d09897d9b1392afd1f65d0a9310890250e46b7c29
```

---

