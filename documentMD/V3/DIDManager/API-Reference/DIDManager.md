---
icon: dot
---

# DIDmanager

DID manager SDK for manage DIDs

## Main function

---

### createDID

```ts
dids.createDID(accountType, accountID, privateKeySigner, privateKey, nonce);
```

Create DID contract. In this version, this function only accept `claimKey.ACCOUNT_TYPE` and `claimKey.ACCOUNT_ID` as `claimKey`, if you want to use new `claimKey`, please use `addClaim` function with a custom `claimKey`

#### Parameters

1. [!badge variant="warning" text="accountType"] - [!badge variant="warning" text="string"]: DID type, default is `PreDefinedClaimKeys.ACCOUNT_TYPE` (check [DID type - PreDefinedClaimKeys](../Introduction.md/#did-type---predefinedclaimkeys))
2. [!badge variant="warning" text="accountID"] - [!badge variant="warning" text="string"]: ID of account
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
    "ACCOUNT_TYPE", 
    "PATIENT", 
    "187bcbef9261e6c7eaefd8368e2b930a8bd7335cf541d8a05e9337beaf4c5f89", 
    "24118478a12cd8e910ec3ae69edc8bda17c70754dd00d13f28dda0aa0f8644bb"
  ).then(console.log);
> {
  receipt: {
    root: '0x0000000000000000000000000000000000000000000000000000000000000000',
    cumulativeGasUsed: 2430633,
    logsBloom: '0x00000000000000000000000000000000000000100002000000000002000000000000070000000000400000000000000000000000000000000000001000040000000000000001000000000100000000100000000000040000000000000000000000000000000000000000000000000000000000000000000000000000000000001000800000100000000000000000000004001800000000000000400000000000000100000000000000000040000000000000000000000000040000000000000000000000000000800000000000000000000000000810000000000000000040010004000000000100000000000000000000000000000000000000000000000000',
    logs: [ [Object], [Object], [Object] ],
    status: true,
    transactionHash: '0x1f844a36fafe54caa1bf2ec88a9e4b1a6d11cd4bb1f5fd3e62bef8af90f0cdbe',
    transactionIndex: 0,
    blockHash: '0xc0c90da6901b17dda48ffcf6712370bb7ba39cd58406a6c0359bbd930e7ce7c3',
    blockNumber: 1873984,
    gasUsed: 2430633,
    contractAddress: '0x9fed50f387178014C9B1eaF39751E2043A0a0e19',
    from: '0x51C4B0487e16186da402daebE06C4cD71b5015c8',
    to: null
  },
  eventLogs: [
    {
      name: 'ClaimAdded',
      address: '0x9fed50f387178014C9B1eaF39751E2043A0a0e19'
    },
    {
      name: 'ClaimAdded',
      events: [Array],
      address: '0x9fed50f387178014C9B1eaF39751E2043A0a0e19'
    }
  ],
  claimsAdded: [
    {
      claimId: '0x3588eb5f2fe80310944a7f3b4425b65fe2077e03e459507ccd391fb30271a310',
      claimKey: 'ACCOUNT_TYPE',
      claimData: '0x4143434f554e545f54595045'
    },
    {
      claimId: '0x61951cffbf424cebc589cbbffc4b509dba9912ceae53a97388841e0979720203',
      claimKey: 'ACCOUNT_ID',
      claimData: '0x50415449454e54'
    }
  ]
}
```

---

### addKey

```ts
dids.addKey(purpose, keyType, addressToAddAsKey, addressOfDelegateKey, targeDID, nonce);
```

Add key to Claim holder (only access for Management side).
!!! Warning "Warning"
In the first time you add key to a DID, that DID has no key execpt `MANAGEMENT`, you must use that `MANAGEMENT` key to do this function. After that, you can use `MANAGEMENT` key or `ACTION` key to add more key to DID.
!!!

#### Parameters

1. [!badge variant="warning" text="purpose"] - [!badge variant="warning" text="KeyPurposes"]: The key purpose (check [Key purpose](../Introduction.md/#key-purpose))
2. [!badge variant="warning" text="keyType"] - [!badge variant="warning" text="Schemes"]: The key type (check [Schemes](../Introduction.md/#schemes))
3. [!badge variant="warning" text="addressToAddAsKey"] - [!badge variant="warning" text="string"]: The address of indentity DID
4. [!badge variant="warning" text="addressOfDelegateKey"] - [!badge variant="warning" text="string"]: The address of delegate key
5. [!badge variant="warning" text="targeDID"] - [!badge variant="warning" text="string"]: Target DID contract address
6. [!badge variant="warning" text="nonce"] - [!badge variant="warning" text="number"] (optional): The nonce of account, use this if you want to use custom nonce

#### Returns

[!badge variant="danger" text="unSignedTx"] - [!badge variant="danger" text="object"]: Unsigned transaction which will be send to user to sign

```ts
dids.addKey(
      KeyPurposes.CLAIM_SIGNER,
      Schemes.ECDSA,
      "0xBC4238FbE2CC00C4a093907bCdb4694FEC00882c",
      "0x51C4B0487e16186da402daebE06C4cD71b5015c8",
      "0x746D98E18A9162DC51639CADBF3F516B6F21Fd81"
      ).then(console.log);
> {
  to: '0x746D98E18A9162DC51639CADBF3F516B6F21Fd81',
  from: '0x51C4B0487e16186da402daebE06C4cD71b5015c8',
  gas: 327151,
  gasPrice: '0',
  nonce: 3237,
  data: '0xb61d27f6000000000000000000000000746d98e18a9162dc51639cadbf3f516b6f21fd810000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000006000000000000000000000000000000000000000000000000000000000000000641d381240c3fdeaa9e9e5812c9f2c1b2ee7c1b8bf099537d8b8bade7aad445185aa4278ef0000000000000000000000000000000000000000000000000000000000000003000000000000000000000000000000000000000000000000000000000000000100000000000000000000000000000000000000000000000000000000'
}
```

---

### addKeyDelegateInCreateDID

```ts
dids.addKeyDelegateInCreateDID(privateKeyToAddAasKey, privateKey, targeDID, nonce);
```

Add delegate key to function CreateDID

#### Parameters

1. [!badge variant="warning" text="privateKeyToAddAasKey"] - [!badge variant="warning" text="KeyPurposes"]: The key purpose (check [Key purpose](../Introduction.md/#key-purpose))
2. [!badge variant="warning" text="privateKey"] - [!badge variant="warning" text="Schemes"]: The key type (check [Schemes](../Introduction.md/#schemes))
3. [!badge variant="warning" text="targeDID"] - [!badge variant="warning" text="string"]: Target DID contract address
4. [!badge variant="warning" text="nonce"] - [!badge variant="warning" text="number"] (optional): The nonce of account, use this if you want to use custom nonce

#### Returns

[!badge variant="danger" text="receipt"] - [!badge variant="danger" text="object"]:  A transaction receipt object, or null if no receipt was found. (check receipt)
```ts
dids.addKeyDelegateInCreateDID(
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
  }
}
```


---

### removeKey

```ts
dids.removeKey(keyRemove, addressOfDelegateKey, targeDID, nonce);
```

Get owner of DID contract

#### Parameters

1. [!badge variant="warning" text="keyRemove"] - [!badge variant="warning" text="string"]: The key to remove
2. [!badge variant="warning" text="addressOfDelegateKey"] - [!badge variant="warning" text="string"]: The address of delegate key
3. [!badge variant="warning" text="targeDID"] - [!badge variant="warning" text="string"]: Target DID contract address
4. [!badge variant="warning" text="nonce"] - [!badge variant="warning" text="number"] (optional): The nonce of account, use this if you want to use custom nonce

#### Returns

[!badge variant="danger" text="unSignedTx"] - [!badge variant="danger" text="object"]: Unsigned transaction which will be send to user to sign


#### Example

```ts
dids.removeKey(
    "0xBC4238FbE2CC00C4a093907bCdb4694FEC00882c",
    "0x51C4B0487e16186da402daebE06C4cD71b5015c8",
    "0x746D98E18A9162DC51639CADBF3F516B6F21Fd81")
    .then(console.log);
> {
  to: '0x746D98E18A9162DC51639CADBF3F516B6F21Fd81',
  from: '0x51C4B0487e16186da402daebE06C4cD71b5015c8',
  gas: 158014,
  gasPrice: '0',
  nonce: 3237,
  data: '0x862642f5bc4238fbe2cc00c4a093907bcdb4694fec00882c000000000000000000000000'
}
```

---

### addClaim

```ts
dids.addClaim(
  addressOfDelegateKey,
  privateKeySigner,
  targetDID,
  claimKey,
  scheme,
  issuer,
  data,
  uri,
  nonce
);
```

Add claim to DID contract

#### Parameters

1. [!badge variant="warning" text="addressOfDelegateKey"] - [!badge variant="warning" text="string"]: The address of delegate key
2. [!badge variant="warning" text="privateKeySigner"] - [!badge variant="warning" text="string"]: Private key of account that has permission to interact with DID
3. [!badge variant="warning" text="targetDID"] - [!badge variant="warning" text="string"]: DID contract address
4. [!badge variant="warning" text="claimKey"] - [!badge variant="warning" text="string"]: The key of claim, this can be any string
5. [!badge variant="warning" text="scheme"] - [!badge variant="warning" text="Schemes"]: The scheme of claim (check Schemes)
6. [!badge variant="warning" text="issuer"] - [!badge variant="warning" text="string"]: The issuer address of claim
7. [!badge variant="warning" text="data"] - [!badge variant="warning" text="string"]: The raw data of claim
8. [!badge variant="warning" text="uri"] - [!badge variant="warning" text="string"] (optional): The uri of claim
9. [!badge variant="warning" text="nonce"] - [!badge variant="warning" text="number"] (optional): The nonce of account
#### Returns

[!badge variant="danger" text="unSignedTx"] - [!badge variant="danger" text="object"]: Unsigned transaction which will be send to user to sign


#### Example

```ts
dids.addClaim(
  "0xBC4238FbE2CC00C4a093907bCdb4694FEC00882c", 
  "187bcbef9261e6c7eaefd8368e2b930a8bd7335cf541d8a05e9337beaf4c5f89", 
  "0x746D98E18A9162DC51639CADBF3F516B6F21Fd81", 
  "Name", 
  Schemes.ECDSA, 
  CONFIG.ClaimHolder.address, 
  "James"
).then(console.log);
> {
  to: '0x746D98E18A9162DC51639CADBF3F516B6F21Fd81',
  from: '0xBC4238FbE2CC00C4a093907bCdb4694FEC00882c',
  gas: 350396,
  gasPrice: '0',
  nonce: 35,
  data: '0xb61d27f6000000000000000000000000746d98e18a9162dc51639cadbf3f516b6f21fd810000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000006000000000000000000000000000000000000000000000000000000000000001e41ce9127300000000000000000000000000000000000000000000000000000000000000c000000000000000000000000000000000000000000000000000000000000000010000000000000000000000001f9d8e15a4e9ea2276df5a8af2c1991a4411bdff0000000000000000000000000000000000000000000000000000000000000100000000000000000000000000000000000000000000000000000000000000018000000000000000000000000000000000000000000000000000000000000001c000000000000000000000000000000000000000000000000000000000000000044e616d650000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000411528acc96a3ed57906614299ea3a787b1fda316f3237150d87dc20a22e76b6cd1eccc6b06993e3d716dba71cb31dfd457d8e536e10319286b006951b798deb4c1b000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000005486f616e67000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
}
```

---

### removeClaim

```ts
dids.removeClaim(issuer, claimKey, targetDID, addressOfDelegateKey, nonce);
```

Remove claim from DID contract

#### Parameters

1. [!badge variant="warning" text="issuer"] - [!badge variant="warning" text="string"]: Issuer (ClaimHolder) contract address, this is fixed in our system
2. [!badge variant="warning" text="claimKey"] - [!badge variant="warning" text="string"]: The key of claim
3. [!badge variant="warning" text="targetDID"] - [!badge variant="warning" text="string"]: Target DID contract address
4. [!badge variant="warning" text="addressOfDelegateKey"] - [!badge variant="warning" text="string"]: The address of delegate key
5. [!badge variant="warning" text="nonce"] - [!badge variant="warning" text="number"] (optional): The nonce of account

#### Returns

[!badge variant="danger" text="unSignedTx"] - [!badge variant="danger" text="object"]: Unsigned transaction which will be send to user to sign

#### Example

```ts
dids.removeClaim(
    CONFIG.ClaimHolder.address, 
    "Name", 
    "0x746D98E18A9162DC51639CADBF3F516B6F21Fd81", 
    "0xBC4238FbE2CC00C4a093907bCdb4694FEC00882c"
  ).then(console.log);
> {
  to: '0x746D98E18A9162DC51639CADBF3F516B6F21Fd81',
  from: '0xBC4238FbE2CC00C4a093907bCdb4694FEC00882c',
  gas: 138897,
  gasPrice: '0',
  nonce: 35,
  data: '0xb61d27f6000000000000000000000000746d98e18a9162dc51639cadbf3f516b6f21fd810000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000006000000000000000000000000000000000000000000000000000000000000000244eee424aa1ab56b51663b628566e325d868fce55c74186f6b7cd3f677ce1fe7de920ed3100000000000000000000000000000000000000000000000000000000'
}
```

---

### getClaimById

```ts
dids.getClaimById(accountDID, claimId);
```

Get claim detail of accountDID by claim id, this will be use to get specific claim if there are 2 claims with same key but from different issuer

#### Parameters

1. [!badge variant="warning" text="accountDID"] - [!badge variant="warning" text="string"]: DID contract address
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
dids.getClaimByKey(accountDID, claimKey);
```

Get claim detail of accountDID by claim id, this will be use to get specific claim, but the issuer is fixed in our system

#### Parameters

1. [!badge variant="warning" text="accountDID"] - [!badge variant="warning" text="string"]: DID contract address
3. [!badge variant="warning" text="claimKey"] - [!badge variant="warning" text="string"]: The claim key

#### Returns

1. [!badge variant="danger" text="claimKeys"] - [!badge variant="danger" text="string"]: The claim key
2. [!badge variant="danger" text="scheme"] - [!badge variant="danger" text="string"]: The claim scheme, this return a `string` but it's actually `number`, please parse it to `number`
3. [!badge variant="danger" text="issuer"] - [!badge variant="danger" text="string"]: The claim issuer
4. [!badge variant="danger" text="signature"] - [!badge variant="danger" text="string"]: A hex string of the signature
5. [!badge variant="danger" text="data"] - [!badge variant="danger" text="string"]: A hex string of the data
6. [!badge variant="danger" text="uri"] - [!badge variant="danger" text="string"]: URI of the claim

#### Example

```ts
dids.getClaimByKey(
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
  issuer: '0xbf69608B714EEDD31199ce2DC21A64D09153A641',
  signature: '0x9a29a083adb1fdac15f018f717289a0cf1d6ef2ac3309382dc58f52c4766148a361748338600c3cfe971bca98ee1c00ed4e30b0f0e0080681899dc1ce29d3e901b',
  data: '0x4a616d6573',
  uri: ''
}

```

---

### getClaimIdsByKey

```ts
dids.getClaimIdsByKey(accountDID, claimKey);
```

Get claim ids of accountDID by claim key

#### Parameters

1. [!badge variant="warning" text="accountDID"] - [!badge variant="warning" text="string"]: DID contract address
2. [!badge variant="warning" text="claimKey"] - [!badge variant="warning" text="string"]: The key of claim

#### Returns

[!badge variant="danger" text="Array\<String>"]: Array of claim ids

#### Example

```ts
dids.getClaimIdsByKey("0xeAB6D21DC3e1eA9441D20EEDfD9133cf37732724", "ACCOUNT_TYPE")
    .then(console.log);
> [
  '0xa42a10be08f648452f1d1e956b9c169331da201bd0b331860314c904ca2cce89'
]
```

---

### getClaimsKeyOwnedByIssuer

```ts
dids.getClaimsKeyOwnedByIssuer(accountDID, issuer);
```

Get list of claim keys owned by accountDID

#### Parameters

1. [!badge variant="warning" text="accountDID"] - [!badge variant="warning" text="string"]: DID contract address
2. [!badge variant="danger" text="issuer"] - [!badge variant="danger" text="string"]: The claim issuer

#### Returns

[!badge variant="danger" text="Array\<String>"]: Array of claim keys

#### Example

```ts
dids.getClaimsKeyOwnedByIssuer(
  "0xeAB6D21DC3e1eA9441D20EEDfD9133cf37732724",
  "0xbf69608B714EEDD31199ce2DC21A64D09153A641"
).then(console.log);
> [ 'ACCOUNT_TYPE', 'ACCOUNT_ID' ]
```

---

### getAllClaimsOwnedByIssuer

```ts
dids.getAllClaimsOwnedByIssuer(accountDID, issuer);
```

Get list of all claims owned by accountDID

#### Parameters

1. [!badge variant="warning" text="accountDID"] - [!badge variant="warning" text="string"]: DID contract address
2. [!badge variant="danger" text="issuer"] - [!badge variant="danger" text="string"]: The claim issuer


#### Returns

[!badge variant="danger" text="Array\<String>"]: Array of claim

#### Example

```ts
dids.getAllClaimsOwnedByIssuer("0xeAB6D21DC3e1eA9441D20EEDfD9133cf37732724")
    .then(console.log);
> [
  Result {
    ...
    claimKey: 'ACCOUNT_TYPE',
    scheme: '1',
    issuer: '0x863098D2fC21309846F7eaF3dD96002A10d43E4d',
    signature: '0x127119341f4a63bce4ae4fb9430379aa4da7004ea9dafd592344fdfd7ddbe6fd6cc985c9ee4174a5c1c7ca90bb925952ecdeee12c8a3110b304db47c2d97d0fc1b',
    data: '0x50494430303030303031',
    uri: ''
  },
  Result {
    ...
    claimKey: 'ACCOUNT_ID',
    scheme: '1',
    issuer: '0x863098D2fC21309846F7eaF3dD96002A10d43E4d',
    signature: '0x9a29a083adb1fdac15f018f717289a0cf1d6ef2ac3309382dc58f52c4766148a361748338600c3cfe971bca98ee1c00ed4e30b0f0e0080681899dc1ce29d3e901b',
    data: '0x4a616d6573',
    uri: ''
  },
]
```

---

### verifyClaim

```ts
dids.verifyClaim(accountDID, claimKey, claimValue);
```

Check if accountDID has a valid claim key issued by our system

#### Parameters

1. [!badge variant="warning" text="accountDID"] - [!badge variant="warning" text="string"]: DID contract address
2. [!badge variant="warning" text="claimKey"] - [!badge variant="warning" text="claimKey"]: The claim key
3. [!badge variant="warning" text="claimValue"] - [!badge variant="warning" text="claimKey"]: The claim value

#### Returns

[!badge variant="danger" text="boolean"]: True if accountDID has a valid claim key, false otherwise

#### Example

```ts
dids.verifyClaim("0x9fed50f387178014C9B1eaF39751E2043A0a0e19", "ACCOUNT_TYPE", "PATIENT");
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
---

### getClaimsKeyOwnedByIssuer

```ts
dids.getClaimsKeyOwnedByIssuer(accountDID, issuer);
```

Get list of claim keys owned by accountDID

#### Parameters

1. [!badge variant="warning" text="accountDID"] - [!badge variant="warning" text="string"]: DID contract address
2. [!badge variant="danger" text="issuer"] - [!badge variant="danger" text="string"]: The claim issuer

#### Returns

[!badge variant="danger" text="Array\<String>"]: Array of claim keys

#### Example

```ts
dids.getClaimsKeyOwnedByIssuer(
  "0xeAB6D21DC3e1eA9441D20EEDfD9133cf37732724",
  "0xbf69608B714EEDD31199ce2DC21A64D09153A641"
).then(console.log);
> [ 'ACCOUNT_TYPE', 'ACCOUNT_ID' ]
```

---

### getHashClaim

```ts
dids.getHashClaim(accountDID, claimId);
```

Get list of all claims owned by accountDID

#### Parameters

1. [!badge variant="warning" text="accountDID"] - [!badge variant="warning" text="string"]: DID contract address.
2. [!badge variant="warning" text="claimId"] - [!badge variant="danger" text="string"]: claimId of DID.


#### Returns

[!badge variant="danger" text="String"]: hash value of claim

#### Example

```ts
dids.getAllClaimsOwnedByIssuer("0xeAB6D21DC3e1eA9441D20EEDfD9133cf37732724", "0xe52a4c9d0575970a000dd1a8372fb50c24cb1dc558269f582c609ff8568845ea)
    .then(console.log);
> 0x856b65949b3a8ea8936fd02df953da7c8c1c3d66a7da09835e0a4e4fc3bfc842
```
