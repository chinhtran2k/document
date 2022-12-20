---
icon: dot
---

# Provider

This module for Provider lock level

## Main function

---

### mintProvider

```ts
Provider.mintProvider(ProviderDID, accountId, uri, privateKey, nonce);
```

Mint and lock Provider

#### Parameters

1. [!badge variant="warning" text="ProviderDID"] - [!badge variant="warning" text="string"]: Address of Provider was created from DID
2. [!badge variant="warning" text="accountId"] - [!badge variant="warning" text="string"]: Address Id off-chain was sent from Pharumo
3. [!badge variant="warning" text="uri"] - [!badge variant="warning" text="string"]: The uri of Provider
4. [!badge variant="warning" text="privateKey"] - [!badge variant="warning" text="string"] : Private key of contract creator(admin)
5. [!badge variant="warning" text="nonce"] - [!badge variant="warning" text="number"] (optional): The nonce of account

#### Returns

1. [!badge variant="danger" text="receipt"] - [!badge variant="danger" text="object"]: A transaction receipt object, or null if no receipt was found. (check receipt).
2. [!badge variant="danger" text="eventLogs"] - [!badge variant="danger" text="object"]: Event logs of transactions.
3. [!badge variant="danger" text="tokenId"] - [!badge variant="danger" text="string"]: Id of Provider token.
3. [!badge variant="danger" text="hashValue"] - [!badge variant="danger" text="string"]: Data lock was hashed by the keccak256

#### Example

```ts
Provider.mintProvider(
    "0x9573Cda4F4f645764767561D1EF3b4b84647aC19",
    "01",
    "uri provider",
    "24118478a12cd8e910ec3ae69edc8bda17c70754dd00d13f28dda0aa0f8644bb"
  )
  .then(console.log);
> {
  receipt: {
    root: '0x0000000000000000000000000000000000000000000000000000000000000000',
    cumulativeGasUsed: 450294,
    logsBloom: '0x00000000000000000080000400000000800000000000000008000000000000000000000000000000000000000000000000000000000000000000000000040000000000000000000000000008000000000000000000040000000000000000000000000000020000000000000000000800000000000000000000000010008000000000000000000000000000000000000000000000000000000010000000000000000000000000000000000000000000000000002080001000000000400000000000000002000000000000000000000000004000000080000000000000000060000000000000000000000000000000000000000000000000000000000000000000',
    logs: [ [Object], [Object], [Object] ],
    status: true,
    transactionHash: '0x78cc7003da6efa313971b815a6e0446264940345ba33b62f2c4f0e7e253a0d4b',
    transactionIndex: 0,
    blockHash: '0xb4369c3db77c6b9645058a0cab7f3296a1acd0fff9c4f668549106f320741b7c',
    blockNumber: 1825514,
    gasUsed: 450294,
    contractAddress: null,
    from: '0x51C4B0487e16186da402daebE06C4cD71b5015c8',
    to: '0x8AE729C3C0e8a2D9C5a95A87278eF7d6e72b5F98'
  },
  eventLogs: [
    {
      name: 'Transfer',
      address: '0x8AE729C3C0e8a2D9C5a95A87278eF7d6e72b5F98'
    },
    {
      name: 'ProviderLockTokenMinted',
      events: [Array],
      address: '0x8AE729C3C0e8a2D9C5a95A87278eF7d6e72b5F98'
    },
    {
      name: 'ProviderTokenLocked',
      events: [Array],
      address: '0x8AE729C3C0e8a2D9C5a95A87278eF7d6e72b5F98'
    }
  ],
  tokenId: '1',
  hashValue: '0x413febeb7faf0762a3c79ac10354ff4096db8ac927d64e9a81355e5671a6d6b9'
}
```

---

### getListAddressOfProvider

```ts
Provider.getListAddressOfProvider();
```

Get List Address Of Provider

#### Parameters

None

#### Returns

[!badge variant="danger" text="String"]: List Address of Provider

#### Example

```ts
Provider.getListAddressOfProvider()
  .then(console.log);
> [ '0x9573Cda4F4f645764767561D1EF3b4b84647aC19' ]
```

---

### getListHashValueProvider

```ts
Provider.getListHashValueProvider(providerDID);
```

Get List Hash Value Of Provider

#### Parameters

1. [!badge variant="warning" text="providerDID"] - [!badge variant="warning" text="string"]: Address of Provider was created from DID

#### Returns

[!badge variant="danger" text="Array\<String>"]: Array of Hash Value

#### Example

```ts
Provider.getListHashValueProvider("0x9573Cda4F4f645764767561D1EF3b4b84647aC19").then(console.log);
> "0x413febeb7faf0762a3c79ac10354ff4096db8ac927d64e9a81355e5671a6d6b9"
```

---

---

### getHashClaim

```ts
patient.getHashClaim(providerDID);
```

Get Claim Data Was Hashed By Keccak256

#### Parameters

[!badge variant="warning" text="providerDID"] - [!badge variant="warning" text="string"]: Address of Provider was created from DID

#### Returns

[!badge variant="warning" text="hashedValue"] - [!badge variant="warning" text="string"]: Claim Data was hashed by keccak256
#### Example

```ts
patient.getHashClaim('0xd0a2926d4f07121c3a29EbdFF514556a82Cb9F7C').then(console.log);

> 0x2695156ad586fff58bd6938d09897d9b1392afd1f65d0a9310890250e46b7c29
```

---

