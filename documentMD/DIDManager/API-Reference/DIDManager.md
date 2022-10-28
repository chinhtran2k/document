---
icon: dot
---

# DIDmanager

DID manager SDK for manage DIDs

## Main function

---

### createDID

```ts
dids.createDID(privateKey, didType);
```

Create DID contract by `privateKey`

#### Parameters

1. [!badge variant="warning" text="privateKey"] - [!badge variant="warning" text="string"]: Private key of account to create DID
2. [!badge variant="warning" text="didType"] - [!badge variant="warning" text="string"]: DID type, default is `ClaimType.PATIENT` (check [DID type](../Introduction.md/#did-type))

#### Returns

1. [!badge variant="danger" text="txHash"] - [!badge variant="danger" text="String"]: The created transaction hash.
2. [!badge variant="danger" text="didAddress"] - [!badge variant="danger" text="String"]: The created DID contract address.

#### Example

```ts
dids.createDID(privateKey, didType);
> {

    txHash: "0xe61615f256624577cb979f51a58ac158c7b34b7eb4598af3c8d2c50ca155d85c",
    didAddress: "0xece7519c282274542231d213A5919337c3F66686"

}

```

---

### addClaim

```ts
dids.addClaim(privateKey, didAddress, claimType, scheme, issuer, data, [uri]);
```

Add claim to DID contract

#### Parameters

1. [!badge variant="warning" text="privateKey"] - [!badge variant="warning" text="string"]: Private key of account that has permission to interact with DID
2. [!badge variant="warning" text="didAddress"] - [!badge variant="warning" text="string"]: DID contract address
3. [!badge variant="warning" text="claimType"] - [!badge variant="warning" text="number"]: The type of claim
4. [!badge variant="warning" text="scheme"] - [!badge variant="warning" text="number"]: The scheme of claim
5. [!badge variant="warning" text="issuer"] - [!badge variant="warning" text="string"]: The issuer address of claim
6. [!badge variant="warning" text="data"] - [!badge variant="warning" text="string"]: The raw data of claim
7. [!badge variant="warning" text="uri"] - [!badge variant="warning" text="string"] (optional): The uri of claim

#### Returns

1. [!badge variant="danger" text="txHash"] - [!badge variant="danger" text="String"]: The transaction hash.
2. [!badge variant="danger" text="claimId"] - [!badge variant="danger" text="String"]: The claim id.

#### Example

```ts
dids.addClaim(
  "24118478a12cd8e910ec3ae69edc8bda17c70754dd00d13f28dda0aa0f8644bb",
  "0xece7519c282274542231d213A5919337c3F66686",
  1,
  1,
  "0xece7519c282274542231d213A5919337c3F66686",
  "0x00",
  ""
);
> {
  txHash: "0x0b5b56505d9bc0fbe0d486781aef199448de3ea5957f8a0dcdb2fe64446bb4e1";
  claimId: "0x09d15692eec35970279cea4f6b0897861ee2cd6677411cc9f69348a19041edde";
}
```

---

### removeClaim

```ts
dids.removeClaim(privateKey, didAddress, claimId);
```

Remove claim from DID contract

#### Parameters

1. [!badge variant="warning" text="privateKey"] - [!badge variant="warning" text="string"]: Private key of account that has permission (check [Key purpose](../Introduction.md/#key-purpose)) to interact with DID
2. [!badge variant="warning" text="didAddress"] - [!badge variant="warning" text="string"]: DID contract address
3. [!badge variant="warning" text="claimId"] - [!badge variant="warning" text="string"]: The claim id

#### Returns

1. [!badge variant="danger" text="txHash"] - [!badge variant="danger" text="String"]: The transaction hash.
2. [!badge variant="danger" text="status"] - [!badge variant="danger" text="String"]: Success or fail.

#### Example

```ts
dids.removeClaim("24118478a12cd8e910ec3ae69edc8bda17c70754dd00d13f28dda0aa0f8644bb", "0xece7519c282274542231d213A5919337c3F66686", 1);
> {
  txHash: "0x0b5b56505d9bc0fbe0d486781aef199448de3ea5957f8a0dcdb2fe64446bb4e1";
  status: "true";
}
```

---

### getCredential

```ts
dids.getCredential(didAddress, claimId);
```

Get claim detail of DID by claim id

#### Parameters

1. [!badge variant="warning" text="didAddress"] - [!badge variant="warning" text="string"]: DID contract address
2. [!badge variant="warning" text="claimId"] - [!badge variant="warning" text="string"]: The claim id

#### Returns

1. [!badge variant="danger" text="claimType"] - [!badge variant="danger" text="number"]: The claim type
2. [!badge variant="danger" text="scheme"] - [!badge variant="danger" text="Object"]: The claim scheme
3. [!badge variant="danger" text="issuer"] - [!badge variant="danger" text="Object"]: The claim issuer
4. [!badge variant="danger" text="signature"] - [!badge variant="danger" text="Object"]: A hex string of the signature
5. [!badge variant="danger" text="data"] - [!badge variant="danger" text="Object"]: A hex string of the data
6. [!badge variant="danger" text="uri"] - [!badge variant="danger" text="Object"]: URI of the claim

#### Example

```ts
dids.getClaim("0xece7519c282274542231d213A5919337c3F66686", "0x09d15692eec35970279cea4f6b0897861ee2cd6677411cc9f69348a19041edde");
> {
    claimType: 1,
    scheme: 1,
    issuer: "0xece7519c282274542231d213a5919337c3f66686",
    signature: "0x00",
    data: "0x00",
    uri: ""
}

```

---

### getClaimIdsByType

```ts
dids.getClaimIdsByType(didAddress, claimType);
```

Get claim ids of DID by claim type

#### Parameters

1. [!badge variant="warning" text="didAddress"] - [!badge variant="warning" text="string"]: DID contract address
2. [!badge variant="warning" text="claimType"] - [!badge variant="warning" text="number"]: The claim type

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
dids.addKey(privateKey, didAddress, publicKey, purpose, keyType);
```

Add key to DID contract

#### Parameters

1. [!badge variant="warning" text="privateKey"] - [!badge variant="warning" text="string"]: Private key of account that has permission to interact with DID
2. [!badge variant="warning" text="didAddress"] - [!badge variant="warning" text="string"]: DID contract address
3. [!badge variant="warning" text="publicKey"] - [!badge variant="warning" text="string"]: The public key, a `keccak256` hash of the address of account we want to add to DID
4. [!badge variant="warning" text="purpose"] - [!badge variant="warning" text="number"]: The purpose of key (check [Key purpose](../Introduction.md/#key-purpose))
5. [!badge variant="warning" text="keyType"] - [!badge variant="warning" text="number"]: The type of key (check [Schemes](../Introduction.md/#schemes))

#### Returns

1. [!badge variant="danger" text="txHash"] - [!badge variant="danger" text="String"]: The transaction hash.
2. [!badge variant="danger" text="status"] - [!badge variant="danger" text="String"]: Success or fail.

#### Example

```ts
dids.addKey(
  "24118478a12cd8e910ec3ae69edc8bda17c70754dd00d13f28dda0aa0f8644bb",
  "0xece7519c282274542231d213A5919337c3F66686",
  "0xf2791dd4aae12b2e3964c26ffbc5c5c1e33c3500acdf9d5ae89cb95a08c0a7b5",
  3,
  1
);
> {
  txHash: "0x80142f0adb52a5778d591ceabda92bac030dfefb0d68e82c714b3440ce19d92e";
  status: "true";
}
```

---

### verifyCredential

```ts
dids.verifyCredential(didClaimHolder, didAddress, claimType);
```

Check if DID has a claim of specific type

#### Parameters

1. [!badge variant="warning" text="didClaimHolder"] - [!badge variant="warning" text="string"]: Claim holder (server-side DID) address
2. [!badge variant="warning" text="didAddress"] - [!badge variant="warning" text="string"]: DID contract address
3. [!badge variant="warning" text="claimType"] - [!badge variant="warning" text="number"]: The claim type

#### Returns

[!badge variant="danger" text="boolean"]: True if DID has a claim of specific type, false otherwise

#### Example

```ts
dids.checkClaim("0xece7519c282274542231d213a5919337c3f66686", "0xece7519c282274542231d213A5919337c3F66686", 1);
> true
```

---

### getOwner

```ts
dids.getOwner(didAddress);
```

Get owner of DID contract

#### Parameters

none

#### Returns

[!badge variant="danger" text="Object"]: The generated wallet.

#### Example

```ts

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
