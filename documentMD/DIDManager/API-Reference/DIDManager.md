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

Create DID contract. In this version, this function only accept `claimKey.PATIENT` and `claimKey.PROVIDER` as `claimKey`, if you want to use new `claimKey`, please use `addClaim` function with a custom `claimKey`

#### Parameters

1. [!badge variant="warning" text="claimKey"] - [!badge variant="warning" text="PreDefinedClaimKeys"]: DID type, default is `PreDefinedClaimKeys.PATIENT` (check [DID type - PreDefinedClaimKeys](../Introduction.md/#did-type---predefinedclaimkeys))
2. [!badge variant="warning" text="data"] - [!badge variant="warning" text="string"]: When create DID, we suggest using `PharumoID` as data for this field
3. [!badge variant="warning" text="privateKeySigner"] - [!badge variant="warning" text="string"]: Private key of `CLAIM_SIGNER` of claimHolder, this is fixed in backend server side
4. [!badge variant="warning" text="privateKey"] - [!badge variant="warning" text="string"]: Private key of DID contract creator - owner of DID contract which will be created
5. [!badge variant="warning" text="nonce"] - [!badge variant="warning" text="number"] (optional): The nonce of account, use this if you want to use custom nonce

#### Returns

1. [!badge variant="danger" text="receipt"] - [!badge variant="danger" text="object"]: A transaction receipt object, or null if no receipt was found. (check [receipt](../../Wallet/API-Reference/Helper#signAndSendTransaction))
2. [!badge variant="danger" text="eventLogs"] - [!badge variant="danger" text="object"]: Decoded Event logs of transaction
3. [!badge variant="danger" text="claimAdded"] - [!badge variant="danger" text="string"]: Added claim of DID contract
   - [!badge variant="danger" text="claimId"] - [!badge variant="danger" text="string"]: ID of added claim
   - [!badge variant="danger" text="claimKey"] - [!badge variant="danger" text="string"]: Key of added claim
   - [!badge variant="danger" text="claimData"] - [!badge variant="danger" text="string"]: Data (value) of added claim in hex string, convert it back to string for original data

#### Example

```ts
dids.createDID(
    PreDefinedClaimKeys.PATIENT,
    "PID0000001",
    "187bcbef9261e6c7eaefd8368e2b930a8bd7335cf541d8a05e9337beaf4c5f89", // This is an example of CLAIM_SIGNER of ClaimHolder, we will use env.CLAIM_SIGNER_PRIVATE_KEY in other function
    "147ba01ee975ff771486759b75206a128babdef687aed85c15c13dbb28f038cf"
  ).then(console.log);
> {
  receipt: {
    root: '0x0000000000000000000000000000000000000000000000000000000000000000',
    cumulativeGasUsed: 2126580,
    logsBloom: '0x00000000000000000000040000000000000000000000000000000000400000004020040000000010000000000000000000000000000000000000000000040000000000000000000000000100000000104000000000040000100000000000000000000000080000000000000000000040100000000000000000000001000001000000000000000000100000000000000004000800000000000000000000000000000100000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000008000000000000000000000040000010000000000000000000000000000000000000000000000000000000000000',
    logs: [ [Object], [Object] ],
    status: true,
    transactionHash: '0x8bda5a5437423e07689ddbf4047e5ee0df871f106ba1a2dec59871f42fe7409a',
    transactionIndex: 0,
    blockHash: '0x8089639aff92ddf7b925f94920f4f9aa6e60523b99a0541251941eaefa0eb4b5',
    blockNumber: 248003,
    gasUsed: 2126580,
    contractAddress: '0xeAB6D21DC3e1eA9441D20EEDfD9133cf37732724',
    from: '0xDff2F881875808d1F3eC776569c28f0d737DA058',
    to: null
  },
  eventLogs: [
    {
      name: 'ClaimAdded',
      events: [Array],
      address: '0xeAB6D21DC3e1eA9441D20EEDfD9133cf37732724'
    }
  ],
  claimAdded: {
    claimId: '0xc0c63df202a84a78e7719944e1efe86f979adf5beb0cc4415438dc1da044f459',
    claimKey: 'PATIENT',
    claimData: '0x50494430303030303031'
  }
}

```

---

### addKey

```ts
dids.addKey(purpose, keyType, privateKeyAdd, delegateKey, targeDID, nonce);
```

Add key to Claim holder (only access for Management side).
!!! Warning "Warning"
In the first time you add key to a DID, that DID has no key execpt `MANAGEMENT`, you must use that `MANAGEMENT` key to do this function. After that, you can use `MANAGEMENT` key or `ACTION` key to add more key to DID.
!!!

#### Parameters

1. [!badge variant="warning" text="purpose"] - [!badge variant="warning" text="KeyPurposes"]: The key purpose (check [Key purpose](../Introduction.md/#key-purpose))
2. [!badge variant="warning" text="keyType"] - [!badge variant="warning" text="Schemes"]: The key type (check [Schemes](../Introduction.md/#schemes))
3. [!badge variant="warning" text="privateKeyAdd"] - [!badge variant="warning" text="string"]: The private key of account to add as key
4. [!badge variant="warning" text="delegateKey"] - [!badge variant="warning" text="string"]: Private key of `DELEGATE_KEY` or `MANAGEMENT` key in first time
5. [!badge variant="warning" text="targeDID"] - [!badge variant="warning" text="string"]: Target DID contract address
6. [!badge variant="warning" text="nonce"] - [!badge variant="warning" text="number"] (optional): The nonce of account, use this if you want to use custom nonce

#### Returns

1. [!badge variant="danger" text="receipt"] - [!badge variant="danger" text="object"]: A transaction receipt object, or null if no receipt was found. (check [receipt](../../Wallet/API-Reference/Helper#signAndSendTransaction))
2. [!badge variant="danger" text="eventLogs"] - [!badge variant="danger" text="object"]: Event logs of transaction
3. [!badge variant="danger" text="keyAdded"] - [!badge variant="danger" text="string"]: Added key of DID contract

#### Example

```ts
dids.addKey(
    KeyPurposes.DELEGATE_KEY,
    Schemes.ECDSA,
    "dbed7d737aac4bc51f876336183cb73d295c7b9528eb734a69ebf9bbca613cc8", //This is just a sample key, do not use in production
    "147ba01ee975ff771486759b75206a128babdef687aed85c15c13dbb28f038cf",
    "0xeAB6D21DC3e1eA9441D20EEDfD9133cf37732724"
  ).then(console.log);
> {
  receipt: {
    root: '0x0000000000000000000000000000000000000000000000000000000000000000',
    cumulativeGasUsed: 327151,
    logsBloom: '0x04000000000008000000020000000000000000000000000000000000000000000020040000000000000000000000000000000000000001000000000000040000000000000000000000000100000000000000000000040000100000000000000000000000020040000000000000000800000000001040000000000000000000000000000000000000000000200000000000200000000000000000000000000000000100000000800000000100000000000000000000000000000000000000000000002000000001000000000000000000800008000000000000000000000060000000000000000000000000000008000000000400008000000000000000000000',
    logs: [ [Object], [Object], [Object], [Object] ],
    status: true,
    transactionHash: '0xc9ffd6c07850efc28c2a191104c459749cb902e1c761a0883ad752490f287c55',
    transactionIndex: 0,
    blockHash: '0xbc8b6482306ad61ddae9651ae457f63a990585d23346902a67974e23fd71919a',
    blockNumber: 248190,
    gasUsed: 327151,
    contractAddress: null,
    from: '0xDff2F881875808d1F3eC776569c28f0d737DA058',
    to: '0xeAB6D21DC3e1eA9441D20EEDfD9133cf37732724'
  },
  eventLogs: [
    {
      name: 'KeyAdded',
      events: [Array],
      address: '0xeAB6D21DC3e1eA9441D20EEDfD9133cf37732724'
    }
  ],
  keyAdded: '0x155c1c7686bd19ce88adb6a4af3cbc3a3caf489f62d0e06b901cb6d2a3400719'
}
```

---

### removeKey

```ts
dids.removeKey(keyRemove, delegateKey, targeDID, nonce);
```

Get owner of DID contract

#### Parameters

1. [!badge variant="warning" text="keyRemove"] - [!badge variant="warning" text="string"]: The key to remove
2. [!badge variant="warning" text="delegateKey"] - [!badge variant="warning" text="string"]: Private key of `DELEGATE_KEY` or `MANAGEMENT` key
3. [!badge variant="warning" text="targeDID"] - [!badge variant="warning" text="string"]: Target DID contract address
4. [!badge variant="warning" text="nonce"] - [!badge variant="warning" text="number"] (optional): The nonce of account, use this if you want to use custom nonce

#### Returns

1. [!badge variant="danger" text="receipt"] - [!badge variant="danger" text="object"]: A transaction receipt object, or null if no receipt was found. (check [receipt](../../Wallet/API-Reference/Helper#signAndSendTransaction))
2. [!badge variant="danger" text="eventLogs"] - [!badge variant="danger" text="object"]: Event logs of transaction

#### Example

```ts
dids.removeKey(
    "0xa8275bd2f2fe9045d2cf8ac51b458741f1fda57c81e8a87c336194cb2b03a296",
    "dbed7d737aac4bc51f876336183cb73d295c7b9528eb734a69ebf9bbca613cc8",
    "0xeAB6D21DC3e1eA9441D20EEDfD9133cf37732724"
  ).then(console.log);
> {
  receipt: {
    root: '0x0000000000000000000000000000000000000000000000000000000000000000',
    cumulativeGasUsed: 21145,
    logsBloom: '0x04000000000000000000000000000000000000000000000000000000000000000020000000000000000000000000000000000000000000000000000000040000000000000000000000000000000000000000000000040000100000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000200000000000000000000000000000000000000000000000000100000000000000000000000000000000000000000000000000000001000000000000000000000008000000000000000000040040000000000000002000000000000000000000000400008000000040000000000000',
    logs: [ [Object] ],
    status: true,
    transactionHash: '0x9cb15f8b62ea04728b1ef962a2b82afd55757ace233117103e753864201f662d',
    transactionIndex: 0,
    blockHash: '0xb9b60c1c20be44d7c7ce68283b35c0a20e520e1644cb1d524558b9fd4d6f23cc',
    blockNumber: 248302,
    gasUsed: 21145,
    contractAddress: null,
    from: '0xB981494fFE0dBd29137ff6bAa8bC494c827CFf3D',
    to: '0xeAB6D21DC3e1eA9441D20EEDfD9133cf37732724'
  },
  eventLogs: [
    {
      name: 'KeyRemoved',
      events: [Array],
      address: '0xeAB6D21DC3e1eA9441D20EEDfD9133cf37732724'
    }
  ]
}
```

---

### addClaim

```ts
dids.addClaim(
  delegateKey,
  privateKeySigner,
  targetDID,
  claimKey,
  scheme,
  issuer,
  data,
  [uri],
  nonce
);
```

Add claim to DID contract

#### Parameters

1. [!badge variant="warning" text="delegateKey"] - [!badge variant="warning" text="string"]: Private key of `DELEGATE_KEY` or `MANAGEMENT` key
2. [!badge variant="warning" text="privateKeySigner"] - [!badge variant="warning" text="string"]: Private key of account that has permission to interact with DID
3. [!badge variant="warning" text="targetDID"] - [!badge variant="warning" text="string"]: DID contract address
4. [!badge variant="warning" text="claimKey"] - [!badge variant="warning" text="string"]: The key of claim, this can be any string
5. [!badge variant="warning" text="scheme"] - [!badge variant="warning" text="Schemes"]: The scheme of claim (check [Schemes](../Introduction#schemes))
6. [!badge variant="warning" text="issuer"] - [!badge variant="warning" text="string"]: The issuer address of claim
7. [!badge variant="warning" text="data"] - [!badge variant="warning" text="string"]: The raw data of claim
8. [!badge variant="warning" text="uri"] - [!badge variant="warning" text="string"] (optional): The uri of claim
9. [!badge variant="warning" text="nonce"] - [!badge variant="warning" text="number"] (optional): The nonce of account

#### Returns

1. [!badge variant="danger" text="receipt"] - [!badge variant="danger" text="object"]: A transaction receipt object, or null if no receipt was found. (check [receipt](../../Wallet/API-Reference/Helper#signAndSendTransaction))
2. [!badge variant="danger" text="eventLogs"] - [!badge variant="danger" text="object"]: Decoded Event logs of transaction
3. [!badge variant="danger" text="claimAdded"] - [!badge variant="danger" text="string"]: Added claim of DID contract
   - [!badge variant="danger" text="claimId"] - [!badge variant="danger" text="string"]: ID of added claim
   - [!badge variant="danger" text="claimKey"] - [!badge variant="danger" text="string"]: Key of added claim
   - [!badge variant="danger" text="claimData"] - [!badge variant="danger" text="string"]: Data (value) of added claim in hex string, convert it back to string for original data

#### Example

```ts
dids.addClaim(
  "dbed7d737aac4bc51f876336183cb73d295c7b9528eb734a69ebf9bbca613cc8",
  env.CLAIM_SIGNER_PRIVATE_KEY,
  "0xeAB6D21DC3e1eA9441D20EEDfD9133cf37732724",
  "Name",
  Schemes.ECDSA,
  CONFIG.ClaimHolder.address,
  "James"
).then(console.log);
> {
  receipt: {
    root: '0x0000000000000000000000000000000000000000000000000000000000000000',
    cumulativeGasUsed: 671342,
    logsBloom: '0x04000000000008000000020000000010000020000000000000000000000000000020000000000010000000000000000000000010000001000000000008000000000000000000000000000000000000100000040000000000100000000000000000000000020040000000000000000800000000001040000000000000000001000000000000000000000000200008000004000800000000000000000000000000000000000000800000000100000000000000000000000000000000000000000000002000000000000000000000000000800008000000000000000000000020000010000000000000000000000008000000000000008000000000000000000000',
    logs: [ [Object], [Object], [Object], [Object] ],
    status: true,
    transactionHash: '0xacd0a965c0a142ad7a5440a930d9cdea111e06deaa68c55b5661642d02157663',
    transactionIndex: 0,
    blockHash: '0x4339713f7736d46cb1a53d6c1d50a9c4ff999a103f995088bcb116356f13c219',
    blockNumber: 248369,
    gasUsed: 671342,
    contractAddress: null,
    from: '0xB981494fFE0dBd29137ff6bAa8bC494c827CFf3D',
    to: '0xeAB6D21DC3e1eA9441D20EEDfD9133cf37732724'
  },
  eventLogs: [
    {
      name: 'ClaimAdded',
      events: [Array],
      address: '0xeAB6D21DC3e1eA9441D20EEDfD9133cf37732724'
    }
  ],
  claimAdded: {
    claimId: '0xa42a10be08f648452f1d1e956b9c169331da201bd0b331860314c904ca2cce89',
    claimKey: 'Name',
    claimData: '0x4a616d6573'
  }
}
```

---

### removeClaim

```ts
dids.removeClaim(issuer, claimKey, targetDID, delegateKey, nonce);
```

Remove claim from DID contract

#### Parameters

1. [!badge variant="warning" text="issuer"] - [!badge variant="warning" text="string"]: Issuer (ClaimHolder) contract address, this is fixed in our system
2. [!badge variant="warning" text="claimKey"] - [!badge variant="warning" text="string"]: The key of claim
3. [!badge variant="warning" text="targetDID"] - [!badge variant="warning" text="string"]: Target DID contract address
4. [!badge variant="warning" text="delegateKey"] - [!badge variant="warning" text="string"]: Private key of `DELEGATE_KEY` or `MANAGEMENT`
5. [!badge variant="warning" text="nonce"] - [!badge variant="warning" text="number"] (optional): The nonce of account

#### Returns

1. [!badge variant="danger" text="receipt"] - [!badge variant="danger" text="object"]: A transaction receipt object, or null if no receipt was found. (check [receipt](../../Wallet/API-Reference/Helper#signAndSendTransaction))
2. [!badge variant="danger" text="eventLogs"] - [!badge variant="danger" text="object"]: Event logs of transaction

#### Example

```ts
dids.removeClaim(
    CONFIG.ClaimHolder.address,
    "Name",
    "0xeAB6D21DC3e1eA9441D20EEDfD9133cf37732724",
    "147ba01ee975ff771486759b75206a128babdef687aed85c15c13dbb28f038cf"
  ).then(console.log);
> {
  receipt: {
    root: '0x0000000000000000000000000000000000000000000000000000000000000000',
    cumulativeGasUsed: 111563,
    logsBloom: '0x00000000000048000000020000000410000020000000000000000000000000000020000000000010000000000000000000000010020001000000000008000000000000000000000000000000000000000000040000000000100000000000000000000000020040000000000000000800000000001040000000000000000001000000000000000000000000200008000000000000000000000000000000000000000000000000800000000000000000000000000000800000000000000000400000002000000000000000000000000000800008000000000000000000000020000010000000002000000000000008000000000000000000000000000000000000',
    logs: [ [Object], [Object], [Object], [Object] ],
    status: true,
    transactionHash: '0xb48dcf66778f27af2cd9a6f608a05066bc14440980cea1e3906b0d863860093e',
    transactionIndex: 0,
    blockHash: '0xc2ebba7b6b6fd4ac8a2bc3966a149381b9b3a9e24920a04bdb14b6403f6fbe70',
    blockNumber: 248423,
    gasUsed: 111563,
    contractAddress: null,
    from: '0xDff2F881875808d1F3eC776569c28f0d737DA058',
    to: '0xeAB6D21DC3e1eA9441D20EEDfD9133cf37732724'
  },
  eventLogs: [
    {
      name: 'ClaimRemoved',
      events: [Array],
      address: '0xeAB6D21DC3e1eA9441D20EEDfD9133cf37732724'
    }
  ]
}
```

---

### getClaimById

```ts
dids.getClaimById(did, claimId);
```

Get claim detail of DID by claim id, this will be use to get specific claim if there are 2 claims with same key but from different issuer

#### Parameters

1. [!badge variant="warning" text="did"] - [!badge variant="warning" text="string"]: DID contract address
2. [!badge variant="warning" text="claimId"] - [!badge variant="warning" text="string"]: The claim id

#### Returns

1. [!badge variant="danger" text="claimKeys"] - [!badge variant="danger" text="string"]: The claim key
2. [!badge variant="danger" text="scheme"] - [!badge variant="danger" text="string"]: The claim scheme, this return a `string` but it's actually `number`, please parse it to `number`
3. [!badge variant="danger" text="issuer"] - [!badge variant="danger" text="string"]: The claim issuer
4. [!badge variant="danger" text="signature"] - [!badge variant="danger" text="string"]: A hex string of the signature
5. [!badge variant="danger" text="data"] - [!badge variant="danger" text="string"]: A hex string of the data
6. [!badge variant="danger" text="uri"] - [!badge variant="danger" text="string"]: URI of the claim

#### Example

```ts
dids.getClaimById(
      "0xeAB6D21DC3e1eA9441D20EEDfD9133cf37732724",
      "0xa42a10be08f648452f1d1e956b9c169331da201bd0b331860314c904ca2cce89"
    )
    .then(console.log);
> {
  '0': 'Name',
  '1': '1',
  '2': '0x863098D2fC21309846F7eaF3dD96002A10d43E4d',
  '3': '0x9a29a083adb1fdac15f018f717289a0cf1d6ef2ac3309382dc58f52c4766148a361748338600c3cfe971bca98ee1c00ed4e30b0f0e0080681899dc1ce29d3e901b',
  '4': '0x4a616d6573',
  '5': '',
  // You can ignore above properties
  claimKey: 'Name',
  scheme: '1',
  issuer: '0x863098D2fC21309846F7eaF3dD96002A10d43E4d',
  signature: '0x9a29a083adb1fdac15f018f717289a0cf1d6ef2ac3309382dc58f52c4766148a361748338600c3cfe971bca98ee1c00ed4e30b0f0e0080681899dc1ce29d3e901b',
  data: '0x4a616d6573',
  uri: ''
}

```

### getClaimByKey

```ts
dids.getClaimById(did, claimKey);
```

Get claim detail of DID by claim id, this will be use to get specific claim, but the issuer is fixed in our system

#### Parameters

1. [!badge variant="warning" text="did"] - [!badge variant="warning" text="string"]: DID contract address
2. [!badge variant="warning" text="claimKey"] - [!badge variant="warning" text="string"]: The claim key

#### Returns

1. [!badge variant="danger" text="claimKeys"] - [!badge variant="danger" text="string"]: The claim key
2. [!badge variant="danger" text="scheme"] - [!badge variant="danger" text="string"]: The claim scheme, this return a `string` but it's actually `number`, please parse it to `number`
3. [!badge variant="danger" text="issuer"] - [!badge variant="danger" text="string"]: The claim issuer
4. [!badge variant="danger" text="signature"] - [!badge variant="danger" text="string"]: A hex string of the signature
5. [!badge variant="danger" text="data"] - [!badge variant="danger" text="string"]: A hex string of the data
6. [!badge variant="danger" text="uri"] - [!badge variant="danger" text="string"]: URI of the claim

#### Example

```ts
dids.getClaimById(
      "0xeAB6D21DC3e1eA9441D20EEDfD9133cf37732724",
      "0xa42a10be08f648452f1d1e956b9c169331da201bd0b331860314c904ca2cce89"
    )
    .then(console.log);
> {
  '0': 'Name',
  '1': '1',
  '2': '0x863098D2fC21309846F7eaF3dD96002A10d43E4d',
  '3': '0x9a29a083adb1fdac15f018f717289a0cf1d6ef2ac3309382dc58f52c4766148a361748338600c3cfe971bca98ee1c00ed4e30b0f0e0080681899dc1ce29d3e901b',
  '4': '0x4a616d6573',
  '5': '',
  // You can ignore above properties
  claimKey: 'Name',
  scheme: '1',
  issuer: '0x863098D2fC21309846F7eaF3dD96002A10d43E4d',
  signature: '0x9a29a083adb1fdac15f018f717289a0cf1d6ef2ac3309382dc58f52c4766148a361748338600c3cfe971bca98ee1c00ed4e30b0f0e0080681899dc1ce29d3e901b',
  data: '0x4a616d6573',
  uri: ''
}

```

---

### getClaimIdsByKey

```ts
dids.getClaimIdsByKey(did, claimKey);
```

Get claim ids of DID by claim key

#### Parameters

1. [!badge variant="warning" text="didAddress"] - [!badge variant="warning" text="string"]: DID contract address
2. [!badge variant="warning" text="claimKey"] - [!badge variant="warning" text="string"]: The key of claim

#### Returns

[!badge variant="danger" text="Array\<String>"]: Array of claim ids

#### Example

```ts
dids.getClaimIdsByKey("0xeAB6D21DC3e1eA9441D20EEDfD9133cf37732724", "Name")
    .then(console.log);
> [
  '0xa42a10be08f648452f1d1e956b9c169331da201bd0b331860314c904ca2cce89'
]
```

---

### getClaimsKeyOwned

```ts
dids.getClaimsKeyOwned(did);
```

Get list of claim keys owned by DID

#### Parameters

[!badge variant="warning" text="didAddress"] - [!badge variant="warning" text="string"]: DID contract address

#### Returns

[!badge variant="danger" text="Array\<String>"]: Array of claim keys

#### Example

```ts
dids.getClaimsKeyOwned("0xeAB6D21DC3e1eA9441D20EEDfD9133cf37732724")
    .then(console.log);
> [ 'PATIENT', 'Name' ]
```

---

### getAllClaimsOwned

```ts
dids.getAllClaimsOwned(did);
```

Get list of all claims owned by DID

#### Parameters

[!badge variant="warning" text="didAddress"] - [!badge variant="warning" text="string"]: DID contract address

#### Returns

[!badge variant="danger" text="Array\<String>"]: Array of claim

#### Example

```ts
dids.getAllClaimsOwned("0xeAB6D21DC3e1eA9441D20EEDfD9133cf37732724")
    .then(console.log);
> [
  Result {
    ...
    claimKey: 'PATIENT',
    scheme: '1',
    issuer: '0x863098D2fC21309846F7eaF3dD96002A10d43E4d',
    signature: '0x127119341f4a63bce4ae4fb9430379aa4da7004ea9dafd592344fdfd7ddbe6fd6cc985c9ee4174a5c1c7ca90bb925952ecdeee12c8a3110b304db47c2d97d0fc1b',
    data: '0x50494430303030303031',
    uri: ''
  },
  Result {
    ...
    claimKey: 'Name',
    scheme: '1',
    issuer: '0x863098D2fC21309846F7eaF3dD96002A10d43E4d',
    signature: '0x9a29a083adb1fdac15f018f717289a0cf1d6ef2ac3309382dc58f52c4766148a361748338600c3cfe971bca98ee1c00ed4e30b0f0e0080681899dc1ce29d3e901b',
    data: '0x4a616d6573',
    uri: ''
  },
  Result {
    ...
    claimKey: 'Job',
    scheme: '1',
    issuer: '0x863098D2fC21309846F7eaF3dD96002A10d43E4d',
    signature: '0x4f0fddbbb4c801bdb3971a6ad92b7ccf56b9389366f3a8d8d902e369d098dd241ed4dba851dd3a587b1b842c385ec0d85ff6b9ccced22d70660e3ea408f3dfd71b',
    data: '0x446f63746f72',
    uri: ''
  }
]
```

---

### verifyClaim

```ts
dids.verifyClaim(did, claimKey);
```

Check if DID has a valid claim key issued by our system

#### Parameters

1. [!badge variant="warning" text="did"] - [!badge variant="warning" text="string"]: DID contract address
2. [!badge variant="warning" text="claimKey"] - [!badge variant="warning" text="claimKey"]: The claim key

#### Returns

[!badge variant="danger" text="boolean"]: True if DID has a valid claim key, false otherwise

#### Example

```ts
dids.verifyClaim("0xeAB6D21DC3e1eA9441D20EEDfD9133cf37732724", "Name");
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
