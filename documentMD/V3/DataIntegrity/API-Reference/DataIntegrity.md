---
icon: dot
---

# DataIntegrity

This module use for check integrity of data.

## Main function

---

### checkIntegritySingleDDR

```ts
dataIntegrity.checkIntegritySingleDDR(
  patientDID,
  ddrId,
  hashedData,
);
```

Check The Integrity Of Single DDR.

#### Parameters

1. [!badge variant="warning" text="patientDID"] - [!badge variant="warning" text="string"]: DID Address of Patient was created which has owner owns the DDR.
2. [!badge variant="warning" text="ddrId"] - [!badge variant="warning" text="string"]: DDR ID off-chain was sent from Pharumo.
3. [!badge variant="warning" text="hashedData"] - [!badge variant="warning" text="string"]: The data of DDR that was hashed by keccak256.

#### Returns

[!badge variant="danger" text="boolean"]: true if the data is valid, false if the data is invalid.

#### Example

```ts
dataIntegrity.checkIntegritySingleDDR(
    "0x35Db94bf8f1773B71AA121ffDb9f527a0fe64bba",
    "0001",
    "0xf00814e2e916628483aef34d34f1f63cee0d8b67a2c7fbea160d2b5d188534c9"),
    .then(console.log);

> true
```
---

### checkIntegritySingleClaim

```ts
dataIntegrity.checkIntegritySingleClaim(
  accountDID,
  claimIssuer,
  claimKey,
  hashClaimOffChain,
);
```

Check The Integrity Of Single Claim.

#### Parameters

1. [!badge variant="warning" text="accountDID"] - [!badge variant="warning" text="string"]: Address of provider/patient was created from DID.
2. [!badge variant="warning" text="claimIssuer"] - [!badge variant="warning" text="string"]: The issuer address of claim.
3. [!badge variant="warning" text="claimKey"] - [!badge variant="warning" text="string"]: The claim key of claim.
4. [!badge variant="warning" text="hashClaimOffChain"] - [!badge variant="warning" text="string"]: hash value off chain of claim from DB.

#### Returns

[!badge variant="danger" text="boolean"]: true if the data is valid, false if the data is invalid

#### Example

```ts
dataIntegrity.checkIntegritySingleClaim(
    "0x35Db94bf8f1773B71AA121ffDb9f527a0fe64bba",
    "0x6BCf373913ac17a3b0E58c23b3548D553e37b376",
    "ACCOUNT_TYPE",
    "0xb643a5262d05b758a3b8977bf5d3690c6b3622ca98391d8ff3131ef9f84d50db")
    .then(console.log);

> true
```

---

### checkIntegritySingleClaimBranch

```ts
dataIntegrity.checkIntegritySingleClaimBranch(
  tokenId,
  accountId,
  hashClaimBranchOffChain,
);
```

Check The Integrity Of Single Claim.

#### Parameters

1. [!badge variant="warning" text="tokenId"] - [!badge variant="warning" text="number"]: tokenId of claim branch.
2. [!badge variant="warning" text="accountDID"] - [!badge variant="warning" text="string"]: Address of provider/patient was created from DID.
3. [!badge variant="warning" text="hashClaimBranchOffChain"] - [!badge variant="warning" text="string"]: hash value off-chain of claim branch from DB.

#### Returns

[!badge variant="danger" text="boolean"]: true if the data is valid, false if the data is invalid

#### Example

```ts
dataIntegrity.checkIntegritySingleClaimBranch(
    1,
    "0x6BCf373913ac17a3b0E58c23b3548D553e37b376",
    "0xb643a5262d05b758a3b8977bf5d3690c6b3622ca98391d8ff3131ef9f84d50db")
    .then(console.log);

> true
```

---

### checkIntegritySingleDDRBranch

```ts
dataIntegrity.checkIntegritySingleDDRBranch(tokenId, patientDID, hashDDRBranchOffChain);
```

Check the integrity of single ddrBranch.

#### Parameters

1. [!badge variant="warning" text="tokenId"] - [!badge variant="warning" text="number"]: Token Id of lock ddrBranch.
2. [!badge variant="warning" text="patientDID"] - [!badge variant="warning" text="string"]:  Address of patient was created from DID.
3. [!badge variant="warning" text="hashDDRBranchOffChain"] - [!badge variant="warning" text="string"]: data hash off-chain of ddr branch from DB.


#### Returns

[!badge variant="danger" text="boolean"]: true if the data is valid, false if the data is invalid.

#### Example

```ts
dataIntegrity.checkIntegritySingleDDRBranch(
   1,
   "0xCB805208DfA4966B14B1CfAf05a5d899ADF24d1b",
   "0xf2baf6d2f921e3bb7eb5e66d7a67d6caeaeb49691d0d681c3865d9b134f7e391")
).then(console.log);

> true
```
---


### checkIntegritySingleDisclosureBranch

```ts
dataIntegrity.checkIntegritySingleDisclosureBranch(tokenId, patientDID, hashDisclosureBranchOffChain);
```

Check the integrity of single disclosureBranch.

#### Parameters

1. [!badge variant="warning" text="tokenId"] - [!badge variant="warning" text="number"]: Token Id of lock disclouseBranch.
2. [!badge variant="warning" text="patientDID"] - [!badge variant="warning" text="string"]:  Address of patient was created from DID.
3. [!badge variant="warning" text="hashDisclosureBranchOffChain"] - [!badge variant="warning" text="string"]: hash value off-chain of disclouse branch from DB.


#### Returns

[!badge variant="danger" text="boolean"]: true if the data is valid, false if the data is invalid.

#### Example

```ts
dataIntegrity.checkIntegritySingleDisclosureBranch(
   "1",
   "0x7f97Db6245E35234Da84E46C7F42E4F722855237",
   "0xf2baf6d2f921e3bb7eb5e66d7a67d6caeaeb49691d0d681c3865d9b134f7e391")
).then(console.log);

> true
```
---

### checkIntegritySinglePatient

```ts
dataIntegrity.checkIntegritySinglePatient(
  tokenId,
  patientDID,
  hashPatientOffChain
);
```

Check the integrity of single patient

#### Parameters
1. [!badge variant="warning" text="tokenId"] - [!badge variant="warning" text="string"]: tokenId of patient lock .
2. [!badge variant="warning" text="patientDID"] - [!badge variant="warning" text="string"]: DID Address of Patient which owner owns all the DDRs
3. [!badge variant="warning" text="hashPatientOffChain"] - [!badge variant="warning" text="string"]: hash value off-chain of patient from DB.

#### Returns

[!badge variant="danger" text="boolean"]: true if the data is valid, false if the data is invalid

#### Example

```ts
dataIntegrity.checkIntegritySinglePatient(
    1,
    "0x7f97Db6245E35234Da84E46C7F42E4F722855237",
    "0xb643a5262d05b758a3b8977bf5d3690c6b3622ca98391d8ff3131ef9f84d50db",
).then(console.log);

> true
```

---
### checkIntegrityStudy

```ts
dataIntegrity.checkIntegrityStudy(
  rootHashValuesPatient,
);
```

Check the integrity study

#### Parameters

1. [!badge variant="warning" text="rootHashValuesPatient"] - [!badge variant="warning" text="string"]: hash value off-chain of poc study from DB.

#### Returns

[!badge variant="danger" text="boolean"]: true if the data is valid, false if the data is invalid

#### Example

```ts
dataIntegrity.checkIntegrityStudy(
  "0xc599d44fdb3d96d54427a825cdcadb3dc2e89902d33bdb64272005a1fe9fb030"  // This is just example, data can be alike
  )
  .then(console.log);

> true
```

---
