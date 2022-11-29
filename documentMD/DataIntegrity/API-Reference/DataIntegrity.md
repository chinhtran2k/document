---
icon: dot
---

# DataIntegrity

Data Integrity SDK

## Main function

---

### checkIntegritySingleDDR

```ts
dataintegrity.checkIntegritySingleDDR(patientDID, ddrId, hashedData);
```

check the integrity of single ddr

#### Parameters

1. [!badge variant="warning" text="patientDID"] - [!badge variant="warning" text="string"]: DID Address of Patient
2. [!badge variant="warning" text="ddrId"] - [!badge variant="warning" text="string"]: Id of DDR
3. [!badge variant="warning" text="hashedData"] - [!badge variant="warning" text="string"]: The data was hashed by keccak256

#### Returns

1. [!badge variant="danger" text="boolean"]: true if the data is valid, false if the data is invalid

#### Example

```ts
pocStudy.checkIntegritySingleDDR(
    "0x35Db94bf8f1773B71AA121ffDb9f527a0fe64bba",
    "0001",
    "0xf00814e2e916628483aef34d34f1f63cee0d8b67a2c7fbea160d2b5d188534c9")
    .then(console.log);

> true
```

---

### checkIntegritySinglePatient

```ts
pocStudy.checkIntegritySinglePatient(patientDID, ddrsRawId, ddrsHashedData);
```

Check the integrity of single patient

#### Parameters

1. [!badge variant="warning" text="patientDID"] - [!badge variant="warning" text="string"]: DID of patient
2. [!badge variant="warning" text="ddrsRawId"] - [!badge variant="warning" text="Array\<string>"]: Array of raw id of DDRs
3. [!badge variant="warning" text="ddrsHashedData"] - [!badge variant="warning" text="Array\<string>"]: Array of hashed data of DDRs

#### Returns

[!badge variant="danger" text="boolean"]: true if the data is valid, false if the data is invalid

#### Example

```ts
pocStudy.checkIntegritySinglePatient(
    "0x3b3FFD45DCD98E843938967B352e22673007fb19",
    Array.from(["1", "2", "3"]),
    Array.from([
      "0xf00814e2e916628483aef34d34f1f63cee0d8b67a2c7fbea160d2b5d188534c9",
      "0x46f910e6fdee1489ecdcb31fd30eb4b8a2b0c6ddac7e252d1ef3c59d02f09c5e",
      "0xd81a12bbbd8e1ada2e7ea6a82ec3b9b54464675977ed8af94b15320c698cac6d",
    ])
).then(console.log);

> true
```
