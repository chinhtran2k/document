---
icon: dot
---

# DataIntegrity

This module use for check integrity of data

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

Check the integrity of single ddr

#### Parameters

1. [!badge variant="warning" text="patientDID"] - [!badge variant="warning" text="string"]: DID Address of Patient was created which has owner owns the DDR
2. [!badge variant="warning" text="ddrId"] - [!badge variant="warning" text="string"]: DDR ID off-chain was sent from Pharumo
3. [!badge variant="warning" text="hashedData"] - [!badge variant="warning" text="string"]: The data of DDR that was hashed by keccak256
4. [!badge variant="warning" text="ddrConsentedTo"] - [!badge variant="warning" text="Array\<string>"]: List of Provider which DDR consented to

#### Returns

[!badge variant="danger" text="boolean"]: true if the data is valid, false if the data is invalid

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

### checkIntegritySinglePatient

```ts
dataIntegrity.checkIntegritySinglePatient(
  patientDID,
  hashClaim,
  ddrsRawId,
  ddrsHashedData,
  ddrsConsentedTo
);
```

Check the integrity of single patient

#### Parameters

1. [!badge variant="warning" text="patientDID"] - [!badge variant="warning" text="string"]: DID Address of Patient which owner owns all the DDRs
2. [!badge variant="warning" text="hashClaim"] - [!badge variant="warning" text="string"]: The data claim was hashed by the keccak256
3. [!badge variant="warning" text="ddrsRawId"] - [!badge variant="warning" text="Array\<string>"]: Array of raw DDR ID of DDRs belong to the patient
4. [!badge variant="warning" text="ddrsHashedData"] - [!badge variant="warning" text="Array\<string>"]: Array of hashed data of DDRs belong to the patient
5. [!badge variant="warning" text="ddrsConsentedTo"] - [!badge variant="warning" text="Array\<Array\<string>>"]: List of Provider which DDR consented to of each DDR

#### Returns

[!badge variant="danger" text="boolean"]: true if the data is valid, false if the data is invalid

#### Example

```ts
dataIntegrity.checkIntegritySinglePatient(
    "0x3b3FFD45DCD98E843938967B352e22673007fb19",
    Array.from(["1", "2", "3"]),
    Array.from([
      "0xf00814e2e916628483aef34d34f1f63cee0d8b67a2c7fbea160d2b5d188534c9",
      "0x46f910e6fdee1489ecdcb31fd30eb4b8a2b0c6ddac7e252d1ef3c59d02f09c5e",
      "0xd81a12bbbd8e1ada2e7ea6a82ec3b9b54464675977ed8af94b15320c698cac6d",
    ]),
    Array.from([
      Array.from(["0xcA03F19695aee47057246615c059F94b0c2734e9"]),
      Array.from(["0xcA03F19695aee47057246615c059F94b0c2734e9"]),
      Array.from(["0xcA03F19695aee47057246615c059F94b0c2734e9"])
    ])
).then(console.log);

> true
```

---

### checkIntegritySingleProvider

```ts
dataIntegrity.checkIntegritySingleProvider(providerDID, accountID, hashClaim);
```

Check the integrity of single patient

#### Parameters

1. [!badge variant="warning" text="providerDID"] - [!badge variant="warning" text="string"]: Address of Provider
2. [!badge variant="warning" text="accountID"] - [!badge variant="warning" text="string"]: Id of Provider off-chain from Pharumo
2. [!badge variant="warning" text="hashClaim"] - [!badge variant="warning" text="string"]: Data claim was hashed by the keccak256


#### Returns

[!badge variant="danger" text="boolean"]: true if the data is valid, false if the data is invalid

#### Example

```ts
dataIntegrity.checkIntegritySingleProvider(
   "0xA0244F2A9420f7DD214682D06A9396A3809B8aC3",
   "PR01",
   "0x00f15667904c8879269dd4afba3a04f641cc2f17c9462a9864f31d0932e9b5f1")
).then(console.log);

> true
```

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
