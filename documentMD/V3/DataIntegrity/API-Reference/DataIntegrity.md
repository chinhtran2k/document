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
  ddrConsentedTo
);
```

Check The Integrity Of Single DDR.

#### Parameters

1. [!badge variant="warning" text="patientDID"] - [!badge variant="warning" text="string"]: DID Address of Patient was created which has owner owns the DDR.
2. [!badge variant="warning" text="ddrId"] - [!badge variant="warning" text="string"]: DDR ID off-chain was sent from Pharumo.
3. [!badge variant="warning" text="hashedData"] - [!badge variant="warning" text="string"]: The data of DDR that was hashed by keccak256.
4. [!badge variant="warning" text="ddrConsentedTo"] - [!badge variant="warning" text="Array\<string>"]: List of Provider which DDR consented to.

#### Returns

[!badge variant="danger" text="boolean"]: true if the data is valid, false if the data is invalid.

#### Example

```ts
dataIntegrity.checkIntegritySingleDDR(
    "0x35Db94bf8f1773B71AA121ffDb9f527a0fe64bba",
    "0001",
    "0xf00814e2e916628483aef34d34f1f63cee0d8b67a2c7fbea160d2b5d188534c9"),
    ["0xcA03F19695aee47057246615c059F94b0c2734e9"]
    .then(console.log);

> true
```
---

### checkIntegritySingleClaim

```ts
dataIntegrity.checkIntegritySingleDDR(
  claimDID,
  tokenId,
  accountId,
  hashedDataClaim,
);
```

Check The Integrity Of Single Claim.

#### Parameters

1. [!badge variant="warning" text="claimDID"] - [!badge variant="warning" text="string"]: Address of provider/patient was created from DID.
2. [!badge variant="warning" text="tokenId"] - [!badge variant="warning" text="string"]: Token Id of lock claim.
3. [!badge variant="warning" text="accountId"] - [!badge variant="warning" text="string"]: Account Id off-chain was sent from Pharumo.
4. [!badge variant="warning" text="hashedData"] - [!badge variant="warning" text="string"]: The data of claim.

#### Returns

[!badge variant="danger" text="boolean"]: true if the data is valid, false if the data is invalid

#### Example

```ts
dataIntegrity.checkIntegritySingleClaim(
    "0x35Db94bf8f1773B71AA121ffDb9f527a0fe64bba",
    "1",
    "PT01",
    "0xb643a5262d05b758a3b8977bf5d3690c6b3622ca98391d8ff3131ef9f84d50db")
    .then(console.log);

> true
```

---

### checkIntegritySingleDDRBranch

```ts
dataIntegrity.checkIntegritySingleDDRBranch(tokenId, patientDID, ddrsId, ddrHashedData);
```

Check the integrity of single ddrBranch.

#### Parameters

1. [!badge variant="warning" text="tokenId"] - [!badge variant="warning" text="string"]: Token Id of lock ddrBranch.
1. [!badge variant="warning" text="patientDID"] - [!badge variant="warning" text="string"]:  Address of provider/patient was created from DID.
2. [!badge variant="warning" text="ddrsId"] - [!badge variant="warning" text="Array\<string>"]: Array of raw DDR ID of DDRs belong to the patient.
2. [!badge variant="warning" text="ddrHashedData"] - [!badge variant="warning" text="Array\<string>"]: List data hash of ddr.


#### Returns

[!badge variant="danger" text="boolean"]: true if the data is valid, false if the data is invalid.

#### Example

```ts
dataIntegrity.checkIntegritySingleProvider(
   "1",
   "0xCB805208DfA4966B14B1CfAf05a5d899ADF24d1b",
   ["001","002"],
   ["0xf2baf6d2f921e3bb7eb5e66d7a67d6caeaeb49691d0d681c3865d9b134f7e391","0x62522366c86c332551d7e9d5ff0a1dad81bc17b0b7ad7ed5756ceaf11dedeccd"])
).then(console.log);

> true
```
---


### checkIntegritySingleDisclosureBranch

```ts
dataIntegrity.checkIntegritySingleDisclosureBranch(tokenId, patientDID, providerDID, ddrsId, ddrHashedData);
```

Check the integrity of single disclosureBranch.

#### Parameters

1. [!badge variant="warning" text="tokenId"] - [!badge variant="warning" text="string"]: Token Id of lock ddrBranch.
2. [!badge variant="warning" text="patientDID"] - [!badge variant="warning" text="string"]:  Address of patient was created from DID.
3. [!badge variant="warning" text="providerDID"] - [!badge variant="warning" text="string"]:  Address of provider was created from DID.
4. [!badge variant="warning" text="ddrsId"] - [!badge variant="warning" text="Array\<string>"]: Array of raw DDR ID of DDRs belong to the patient.
5. [!badge variant="warning" text="ddrHashedData"] - [!badge variant="warning" text="Array\<string>"]: List data hash of ddr.


#### Returns

[!badge variant="danger" text="boolean"]: true if the data is valid, false if the data is invalid.

#### Example

```ts
dataIntegrity.checkIntegritySingleProvider(
   "1",
   "0x7f97Db6245E35234Da84E46C7F42E4F722855237",
   "0xCB805208DfA4966B14B1CfAf05a5d899ADF24d1b",
   ["001","002"],
   ["0xf2baf6d2f921e3bb7eb5e66d7a67d6caeaeb49691d0d681c3865d9b134f7e391","0x62522366c86c332551d7e9d5ff0a1dad81bc17b0b7ad7ed5756ceaf11dedeccd"])
).then(console.log);

> true
```
---

### checkIntegritySinglePatient

```ts
dataIntegrity.checkIntegritySinglePatient(
  tokenId,
  patientDID,
  hashClaim,
  ddrBranchHashs,
  disclosureBranchHashs
);
```

Check the integrity of single patient

#### Parameters
1. [!badge variant="warning" text="tokenId"] - [!badge variant="warning" text="string"]: tokenId of patient lock .
2. [!badge variant="warning" text="patientDID"] - [!badge variant="warning" text="string"]: DID Address of Patient which owner owns all the DDRs
3. [!badge variant="warning" text="hashClaim"] - [!badge variant="warning" text="string"]: The data claim was hashed by the keccak256.
4. [!badge variant="warning" text="ddrBranchHashs"] - [!badge variant="warning" text="Array\<string>"]: Array hashvalue of ddrBranch lock.
5. [!badge variant="warning" text="disclosureBranchHashs"] - [!badge variant="warning" text="Array\<string>"]: Array hashvalue of disclosureBranch lock.

#### Returns

[!badge variant="danger" text="boolean"]: true if the data is valid, false if the data is invalid

#### Example

```ts
dataIntegrity.checkIntegritySinglePatient(
    "1",
    "0x7f97Db6245E35234Da84E46C7F42E4F722855237",
    "0xb643a5262d05b758a3b8977bf5d3690c6b3622ca98391d8ff3131ef9f84d50db",
    Array.from([
      "0xf00814e2e916628483aef34d34f1f63cee0d8b67a2c7fbea160d2b5d188534c9",
      "0x46f910e6fdee1489ecdcb31fd30eb4b8a2b0c6ddac7e252d1ef3c59d02f09c5e",
      "0xd81a12bbbd8e1ada2e7ea6a82ec3b9b54464675977ed8af94b15320c698cac6d",
    ]),
    Array.from([
      Array.from(["0xf7c4348c5d7fb312cf30866a9b68d58bd6b1c70bab4fe20880ed3afddd7f516f"]),
      Array.from(["0xadf565076c326f51e03ae342d301ceabe6b5fe5062c541a401d753585a45026c"]),
      Array.from(["0x4c765aa3a21a7e0e28f295222871c3b32bf526de25a87b008ef58c344988e946"])
    ])
).then(console.log);

> true
```

---
### checkIntegrityStudy

```ts
dataIntegrity.checkIntegrityStudy(
  rootHashValuesPatient,
  rootHashValuesProvider
);
```

Check the integrity study

#### Parameters

1. [!badge variant="warning" text="rootHashValuesPatient"] - [!badge variant="warning" text="Array\<string>"]: Array of root hash values of all patients
2. [!badge variant="warning" text="rootHashValuesProvider"] - [!badge variant="warning" text="Array\<string>"]: Array of root hash values of all providers

!!! Warning Warn
`rootHashValuesPatient`, `rootHashValuesProvider` must be input by true order (which is added first, eg: `[\<PatientHash1>, \<PatientHash2>]`), or the result will be wrong
!!!

#### Returns

[!badge variant="danger" text="boolean"]: true if the data is valid, false if the data is invalid

#### Example

```ts
dataIntegrity.checkIntegrityStudy(
  ["0xc599d44fdb3d96d54427a825cdcadb3dc2e89902d33bdb64272005a1fe9fb030",  // This is just example, data can be alike
  "0xc599d44fdb3d96d54427a825cdcadb3dc2e89902d33bdb64272005a1fe9fb030",
  "0xc599d44fdb3d96d54427a825cdcadb3dc2e89902d33bdb64272005a1fe9fb030",
  "0xc599d44fdb3d96d54427a825cdcadb3dc2e89902d33bdb64272005a1fe9fb030",
  "0xc599d44fdb3d96d54427a825cdcadb3dc2e89902d33bdb64272005a1fe9fb030",
  "0xc599d44fdb3d96d54427a825cdcadb3dc2e89902d33bdb64272005a1fe9fb030",
  "0xc599d44fdb3d96d54427a825cdcadb3dc2e89902d33bdb64272005a1fe9fb030",
  "0xf1b58baf6d7650f6e7571ee0393e50619d4da8b02864d118cc44e3a6d894cbae",
  "0xf1b58baf6d7650f6e7571ee0393e50619d4da8b02864d118cc44e3a6d894cbae"],
  ["0051bd68c174759f9b23b1ab213c7901c4b97d4d519879d14a4f6133c12f80fd",
  "70a5f2406b818add7e4c6469b61194f228525080e46ddfb118388e630a9c4bda",])
  .then(console.log);

> true
```

---
