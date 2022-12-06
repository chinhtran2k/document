---
icon: dot
---

# DIDmanager

DID manager SDK for manage DIDs

## Main function

---

### createDID

```ts
dids.createDID(claimKey, data, privateKeySigner, privateKey, nonce);
```

Create DID contract.

#### Parameters

1. [!badge variant="warning" text="claimKey"] - [!badge variant="warning" text="claimKey"]: DID type, default is `claimKey.PATIENT` (check [DID type](../Introduction.md/#did-type))
2. [!badge variant="warning" text="data"] - [!badge variant="warning" text="string"]: Init data for different claim, please use user id of off-chain side or use random number as id
3. [!badge variant="warning" text="privateKeySigner"] - [!badge variant="warning" text="string"]: Private key of signer of claimHolder, get this from server side
4. [!badge variant="warning" text="privateKey"] - [!badge variant="warning" text="string"]: Private key of contract creator - owner of identity contract which will be created
5. [!badge variant="warning" text="nonce"] - [!badge variant="warning" text="number"] (optional): The nonce of account

#### Returns

1. [!badge variant="danger" text="receipt"] - [!badge variant="danger" text="object"]: A transaction receipt object, or null if no receipt was found. (check [receipt](../../Wallet/API-Reference/Helper#signAndSendTransaction))
2. [!badge variant="danger" text="eventLogs"] - [!badge variant="danger" text="object"]: Event logs of transaction
3. [!badge variant="danger" text="claimId"] - [!badge variant="danger" text="string"]: Added claimId of DID contract

#### Example

```ts
dids.createDID(claimKeys.PATIENT,
    "PATIENT VERIFIED",
    signerKey,
    account.privateKey
  );
> {
  receipt: {
    root: '0x0000000000000000000000000000000000000000000000000000000000000000',
    cumulativeGasUsed: 2920716,
    logsBloom: '0x00000000000000000000000000000000000000000000000000000000000000000000040000000000400000000000000000000000000000000000000000040000000000000000000000000100000000000020000000040000000000000000001000000002000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000002000000000100000000000000000040020000000000000002000000000000100000000000000000000020000000000000000000000080000010000008000000000040080000000000000040000000000000000000000000000000000000000000000000',
    logs: [ [Object], [Object] ],
    status: true,
    transactionHash: '0x4a725f16727c8aef8089e844f7ed8f31c3ef849cbca5f8518821d115a0c7576e',
    transactionIndex: 0,
    blockHash: '0xf6c8d3101dea27dfe967dcf1d3f132913924367df2c3dcce5706a212ddcd6687',
    blockNumber: 1394116,
    gasUsed: 2920716,
    contractAddress: '0x7Aaf39BBD7Dd755EaA50F992522A4Eb3d8cd75a0',
    from: '0x51C4B0487e16186da402daebE06C4cD71b5015c8',
    to: null
  },
  eventLogs: [
    {
      name: 'ClaimAdded',
      events: [
        claimId: '0x68ab8d5ae723515a5b77cb01cddf832ce9c6acfca1ab7bfaf8b912eab7b1667a',
        claimKeys: '1',
        scheme: '1',
        issuer: '0x6beca9eb5ce6b2ad84910b952ea83109c277e30c',
        signature: '0xeed89b65dbd61e0c83165b1c9aaefe9c43dc624da5164864bad669c5f73b25a81aa24ea1bd29f1c4b857bf021a81f2805543a57a58ffd8d26df0c0535a980e881b',
        data: '0x50415449454e54205645524946494544',
        uri: ''
      ],
      address: '0x7Aaf39BBD7Dd755EaA50F992522A4Eb3d8cd75a0'
    }
  ],
  claimId: '0x68ab8d5ae723515a5b77cb01cddf832ce9c6acfca1ab7bfaf8b912eab7b1667a'
}

```

---

### addClaim

```ts
dids.addClaim(
  delegateKey,
  privateKeySigner,
  targetIdentity,
  claimKeys,
  scheme,
  issuer,
  data,
  [uri],
  nonce
);
```

Add claim to DID contract

#### Parameters

1. [!badge variant="warning" text="delegateKey"] - [!badge variant="warning" text="string"]: Private key of delegateKey
2. [!badge variant="warning" text="privateKeySigner"] - [!badge variant="warning" text="string"]: Private key of account that has permission to interact with DID
3. [!badge variant="warning" text="targetIdentity"] - [!badge variant="warning" text="string"]: DID contract address
4. [!badge variant="warning" text="claimKey"] - [!badge variant="warning" text="claimKey"]: The key of claim
5. [!badge variant="warning" text="scheme"] - [!badge variant="warning" text="number"]: The scheme of claim
6. [!badge variant="warning" text="issuer"] - [!badge variant="warning" text="string"]: The issuer address of claim
7. [!badge variant="warning" text="data"] - [!badge variant="warning" text="string"]: The raw data of claim
8. [!badge variant="warning" text="uri"] - [!badge variant="warning" text="string"] (optional): The uri of claim
9. [!badge variant="warning" text="nonce"] - [!badge variant="warning" text="number"] (optional): The nonce of account

#### Returns

1. [!badge variant="danger" text="receipt"] - [!badge variant="danger" text="object"]: A transaction receipt object, or null if no receipt was found. (check [receipt](../../Wallet/API-Reference/Helper#signAndSendTransaction))
2. [!badge variant="danger" text="eventLogs"] - [!badge variant="danger" text="object"]: Event logs of transaction
3. [!badge variant="danger" text="claimId"] - [!badge variant="danger" text="string"]: Added claimId of DID contract

#### Example

```ts
dids.addClaim(
  "24118478a12cd8e910ec3ae69edc8bda17c70754dd00d13f28dda0aa0f8644bb",
  "187bcbef9261e6c7eaefd8368e2b930a8bd7335cf541d8a05e9337beaf4c5f89",
  "0x7Aaf39BBD7Dd755EaA50F992522A4Eb3d8cd75a0",
  2,
  1,
  "0x6bECa9Eb5cE6b2Ad84910B952ea83109C277E30c",
  "PATIENT VERIFIED"
);
> {
  receipt: {
    root: '0x0000000000000000000000000000000000000000000000000000000000000000',
    cumulativeGasUsed: 404150,
    logsBloom: '0x04000000000000000000020000000000000000000000000040000000000000000000000000000000000000000000000000000000000001000000000000040000000000000000000000000000000000000020000000040000000000000000001001000000020040000000000000000800000000001040000000000000000000000000000080000000000000200000000000000000000000000000000002000000000000000000800000000100000000000000000002000000000000000000000000000008000020000000000000000000800080000000000008000040000060080000000000000040000000000000000000000000808000000000000000000000',
    logs: [ [Object], [Object], [Object], [Object] ],
    status: true,
    transactionHash: '0x2f722f67d70a431b67671564e1c6f98643d840c77008561f42d2044c34f316e5',
    transactionIndex: 0,
    blockHash: '0x2111d63c23c7a21487e3b301a85ceeb145d0c49c1db96edd57d4041a5151d04e',
    blockNumber: 1394371,
    gasUsed: 404150,
    contractAddress: null,
    from: '0x51C4B0487e16186da402daebE06C4cD71b5015c8',
    to: '0x7Aaf39BBD7Dd755EaA50F992522A4Eb3d8cd75a0'
  },
  eventLogs: [
    {
      name: 'ClaimAdded',
      events: [Array],
      address: '0x7Aaf39BBD7Dd755EaA50F992522A4Eb3d8cd75a0'
    }
  ],
  claimId: '0x2adc65fdd5682de590acc7ab63eead42dfb7a177458dee8937f9290bf49ceb88'
}
```

---

### removeClaim

```ts
dids.removeClaim(issuer, claimKey, targetIdentity, delegateKey, nonce);
```

Remove claim from DID contract

#### Parameters

1. [!badge variant="warning" text="issuer"] - [!badge variant="warning" text="string"]: Issuer (ClaimHolder) contract address
2. [!badge variant="warning" text="claimKey"] - [!badge variant="warning" text="claimKey"]: The key of claim
3. [!badge variant="warning" text="targetIdentity"] - [!badge variant="warning" text="string"]: DID contract address
4. [!badge variant="warning" text="delegateKey"] - [!badge variant="warning" text="string"]: Private key of delegateKey
5. [!badge variant="warning" text="nonce"] - [!badge variant="warning" text="number"] (optional): The nonce of account

#### Returns

1. [!badge variant="danger" text="receipt"] - [!badge variant="danger" text="object"]: A transaction receipt object, or null if no receipt was found. (check [receipt](../../Wallet/API-Reference/Helper#signAndSendTransaction))
2. [!badge variant="danger" text="eventLogs"] - [!badge variant="danger" text="object"]: Event logs of transaction

#### Example

```ts
dids.removeClaim("0x6bECa9Eb5cE6b2Ad84910B952ea83109C277E30c", 2, "0x7Aaf39BBD7Dd755EaA50F992522A4Eb3d8cd75a0", "24118478a12cd8e910ec3ae69edc8bda17c70754dd00d13f28dda0aa0f8644bb");
> {
  receipt: {
    root: '0x0000000000000000000000000000000000000000000000000000000000000000',
    cumulativeGasUsed: 112893,
    logsBloom: '0x04000000000000000000020000000000000000000000000040000000000000000000000000000000000000000000000000000000000001000000000000000000000000000100000000000000100000000000010000000000000000000000001009000000020040000000000000000800000000001040000000000000000000000000000080000000000000200000000000000000000000000000000000000000000000000000800000000100000000000000000002000000002000000000000000000008000000000000000000000000800080008000000008000040000020080000000000000040000000000000000000000000808000000000000000000000',
    logs: [ [Object], [Object], [Object], [Object] ],
    status: true,
    transactionHash: '0xd8dd4362bf8543cced2ef087f7fca84a9b34cc3046f8fced67d91ef53b7f53f6',
    transactionIndex: 0,
    blockHash: '0xd8d392966e18ff88adeec75e0ec9c10998418b9dd5acaa84e391b745b5d5e41a',
    blockNumber: 1394799,
    gasUsed: 112893,
    contractAddress: null,
    from: '0x51C4B0487e16186da402daebE06C4cD71b5015c8',
    to: '0x7Aaf39BBD7Dd755EaA50F992522A4Eb3d8cd75a0'
  },
  eventLogs: [
    {
      name: 'ClaimRemoved',
      events: [Array],
      address: '0x7Aaf39BBD7Dd755EaA50F992522A4Eb3d8cd75a0'
    }
  ]
}
```

---

### getClaim

```ts
dids.getClaim(identity, claimId);
```

Get claim detail of DID by claim id

#### Parameters

1. [!badge variant="warning" text="identity"] - [!badge variant="warning" text="string"]: DID contract address
2. [!badge variant="warning" text="claimId"] - [!badge variant="warning" text="string"]: The claim id

#### Returns

1. [!badge variant="danger" text="claimKeys"] - [!badge variant="danger" text="number"]: The claim key
2. [!badge variant="danger" text="scheme"] - [!badge variant="danger" text="Object"]: The claim scheme
3. [!badge variant="danger" text="issuer"] - [!badge variant="danger" text="Object"]: The claim issuer
4. [!badge variant="danger" text="signature"] - [!badge variant="danger" text="Object"]: A hex string of the signature
5. [!badge variant="danger" text="data"] - [!badge variant="danger" text="Object"]: A hex string of the data
6. [!badge variant="danger" text="uri"] - [!badge variant="danger" text="Object"]: URI of the claim

#### Example

```ts
dids.getClaim("0x7Aaf39BBD7Dd755EaA50F992522A4Eb3d8cd75a0", "0x68ab8d5ae723515a5b77cb01cddf832ce9c6acfca1ab7bfaf8b912eab7b1667a");
> {
  ...
  claimKeys: '1',
  scheme: '1',
  issuer: '0x6bECa9Eb5cE6b2Ad84910B952ea83109C277E30c',
  signature: '0xeed89b65dbd61e0c83165b1c9aaefe9c43dc624da5164864bad669c5f73b25a81aa24ea1bd29f1c4b857bf021a81f2805543a57a58ffd8d26df0c0535a980e881b',
  data: '0x50415449454e54205645524946494544',
  uri: ''
}

```

---

### getClaimIdsByType

```ts
dids.getClaimIdsByType(identity, claimKey);
```

Get claim ids of DID by claim key

#### Parameters

1. [!badge variant="warning" text="didAddress"] - [!badge variant="warning" text="string"]: DID contract address
2. [!badge variant="warning" text="claimKey"] - [!badge variant="warning" text="number"]: The key of claim

#### Returns

[!badge variant="danger" text="Array\<String>"]: Array of claim ids

#### Example

```ts
dids.getClaimIdsByType("0xece7519c282274542231d213a5919337c3f66686", 1);
> ["0x09d15692eec35970279cea4f6b0897861ee2cd6677411cc9f69348a19041edde"]
```

---

### addKey

```ts
dids.addKey(purpose, keyType, privateKeyAdd, delegateKey, targeIdentity, nonce);
```

Add key to Claim holder (only access for Management side)

#### Parameters

1. [!badge variant="warning" text="purpose"] - [!badge variant="warning" text="KeyPurposes"]: The key purpose (check [Key purpose](../Introduction.md/#key-purpose))
2. [!badge variant="warning" text="keyType"] - [!badge variant="warning" text="Schemes"]: The key type (check [Schemes](../Introduction.md/#schemes))
3. [!badge variant="warning" text="privateKeyAdd"] - [!badge variant="warning" text="string"]: The private key of account to add as key
4. [!badge variant="warning" text="delegateKey"] - [!badge variant="warning" text="string"]: Private key of delegateKey
5. [!badge variant="warning" text="targeIdentity"] - [!badge variant="warning" text="string"]: Target DID contract address
6. [!badge variant="warning" text="nonce"] - [!badge variant="warning" text="number"] (optional): The nonce of account

#### Returns

1. [!badge variant="danger" text="receipt"] - [!badge variant="danger" text="object"]: A transaction receipt object, or null if no receipt was found. (check [receipt](../../Wallet/API-Reference/Helper#signAndSendTransaction))
2. [!badge variant="danger" text="eventLogs"] - [!badge variant="danger" text="object"]: Event logs of transaction
3. [!badge variant="danger" text="keyAdded"] - [!badge variant="danger" text="string"]: Added key of DID contract

#### Example

```ts
dids.addKey(
  KeyPurposes.CLAIM_SIGNER,
  Schemes.ECDSA,
  "28d90c06971d80358c9d33dd755408f84ba67deb0dc2eab41036c5ad8ae245a4",
  "24118478a12cd8e910ec3ae69edc8bda17c70754dd00d13f28dda0aa0f8644bb",
  "0x235390558202F869D23191a2Ad48246679E619a8"
);
> {
  receipt: {
    root: '0x0000000000000000000000000000000000000000000000000000000000000000',
    cumulativeGasUsed: 114351,
    logsBloom: '0x00000000000000000000000040000000000000000000000000000000000000000000040000000000000000200000000000000000020000000000000000040000000000000000000000000100000000000000000000040000000000000000000002000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000010000000000000000000000000000000100000000000000000000000000000000000000800000000000000000400000000000000000000000000000000000000000000000000000200000000040000000000000000000000000000000001000000000000000000000000000000000',
    logs: [ [Object] ],
    status: true,
    transactionHash: '0x74c1766cd63881811471ec0c0813e13c4afdd4f14fd9a28da2215d8b8f4a0ebd',
    transactionIndex: 0,
    blockHash: '0x2b707c46ce44a615f04e13f8483779d1d958f4683eab849860865a2cdb59a5e0',
    blockNumber: 1395192,
    gasUsed: 114351,
    contractAddress: null,
    from: '0x51C4B0487e16186da402daebE06C4cD71b5015c8',
    to: '0x6bECa9Eb5cE6b2Ad84910B952ea83109C277E30c'
  },
  eventLogs: [
    {
      name: 'KeyAdded',
      events: [Array],
      address: '0x6bECa9Eb5cE6b2Ad84910B952ea83109C277E30c'
    }
  ],
  keyAdded: '0xa8275bd2f2fe9045d2cf8ac51b458741f1fda57c81e8a87c336194cb2b03a296'
}
```

---

### removeKey

```ts
dids.removeKey(keyRemove, delegateKey, targeIdentity, nonce);
```

Get owner of DID contract

#### Parameters

1. [!badge variant="warning" text="keyRemove"] - [!badge variant="warning" text="string"]: The key to remove
2. [!badge variant="warning" text="delegateKey"] - [!badge variant="warning" text="string"]: Private key of delegateKey
3. [!badge variant="warning" text="targeIdentity"] - [!badge variant="warning" text="string"]: Target DID contract address
4. [!badge variant="warning" text="nonce"] - [!badge variant="warning" text="number"] (optional): The nonce of account

#### Returns

1. [!badge variant="danger" text="receipt"] - [!badge variant="danger" text="object"]: A transaction receipt object, or null if no receipt was found. (check [receipt](../../Wallet/API-Reference/Helper#signAndSendTransaction))
2. [!badge variant="danger" text="eventLogs"] - [!badge variant="danger" text="object"]: Event logs of transaction

#### Example

```ts
const removekeyTx = await dids.removeKey(
    "0xa8275bd2f2fe9045d2cf8ac51b458741f1fda57c81e8a87c336194cb2b03a296",
    "24118478a12cd8e910ec3ae69edc8bda17c70754dd00d13f28dda0aa0f8644bb",
    "0x235390558202F869D23191a2Ad48246679E619a8"
  );
> {
  receipt: {
    root: '0x0000000000000000000000000000000000000000000000000000000000000000',
    cumulativeGasUsed: 21405,
    logsBloom: '0x00000000000000000000000040000000000000000000000000000000000000000000000000000000000000200000000000000000020000000000000000040000000000000000000000000000000000000000000000040000000000000000000002000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000010000000000000000000000000000000000000000000000000000000000000000000000800000000000000000400000000000000000000000000000000000000000000000000000200000040040000000000000002000000000000000001000000000000000000040000000000000',
    logs: [ [Object] ],
    status: true,
    transactionHash: '0xde3d640e5755597840f984af03d929fae35813210ee029878dcae30b27bf8e0b',
    transactionIndex: 0,
    blockHash: '0x9892a0015e6fd321799ce7f44abcff03c9203017cd32552e9de4a2600b0f5756',
    blockNumber: 1397121,
    gasUsed: 21405,
    contractAddress: null,
    from: '0x51C4B0487e16186da402daebE06C4cD71b5015c8',
    to: '0x6bECa9Eb5cE6b2Ad84910B952ea83109C277E30c'
  },
  eventLogs: [
    {
      name: 'KeyRemoved',
      events: [Array],
      address: '0x6bECa9Eb5cE6b2Ad84910B952ea83109C277E30c'
    }
  ]
}
```

---

### verifyCredential

```ts
dids.verifyClaim(identity, claimKey, nonce);
```

Check if DID has a claim of specific key (remember that our Claim Holder is static on server side)

#### Parameters

1. [!badge variant="warning" text="identity"] - [!badge variant="warning" text="string"]: DID contract address
2. [!badge variant="warning" text="claimKey"] - [!badge variant="warning" text="claimKey"]: The claim key

#### Returns

[!badge variant="danger" text="boolean"]: True if DID has a valid claim of specific key

#### Example

```ts
dids.verifyClaim("0xece7519c282274542231d213A5919337c3F66686", 1);
> true
```

## Utils

---

### addrToKey

```ts
dids.addrToKey(address);
```

Hash address to key by `keccak256`

#### Parameters

[!badge variant="warning" text="address"] - [!badge variant="warning" text="string"]: Address of account

#### Returns

[!badge variant="danger" text="string"]: The hash keccak256 of address

#### Example

```ts
dids.addrToKey("0x227E3b971F14d9ef9eB2A8C4309FddbE1E7EE140");
> "0xf2791dd4aae12b2e3964c26ffbc5c5c1e33c3500acdf9d5ae89cb95a08c0a7b5"
```
