---
order: 99
icon: hash
---

# Hashing value guide

This section will guide you through the process to generate `hashValue` in DDR.

---

## Requirements

Before we start, we need to know about DDR structure and `hashValue` ([ddr API](http://35.72.210.241/#hashpeak-api-b-blockchain-ddr-manager-b-get)):

```ts ddrs: object
// An example of DDR
"ddrs": [
    {
      ...
      "tokenID": "00234",
      "patientDID": "0xE84d1F21736fCe9A7c670265f8f0a86C49f0992e",
      "ddrID": "DDR-12345",
      "hashValue": "0x1d63660020a5b5062fb35d9f82afa81581442281c43343763ab1d340e9861bae",
      "didConsentedOf": []
    }
  ]
```

About `hashValue`: [!badge variant="Warning" text="bytes32"], [!badge variant="danger" text="UNIQUE"]

As you can see, we have a field call `hashValue`, it's a `bytes32` and it's actually `hashValue` of data of DDR. So, we need to generate hashValue of DDR before we create DDR, and we need it to keep unique.

!!! Danger REQUIRED
hashValue must be **UNIQUE**, or we will get so much trouble when manage data.
!!!

---

## Generate hashValue

We recommend you using `keccak256`. In this example, I will show you how to generate a hashValue with [`keccak256`](https://www.npmjs.com/package/keccak256) on Typescript.

!!! Note
You can use any hashing algorithm you want, but you need to make sure that the `hashValue` is unique, and it's a `bytes32`
!!!

```ts
import keccak256 from "keccak256";

const ddrData = "Fill this with your DDR data like Name + Address + DOB";

// Please remember to use patientDID, this is a unique identifier of patient
const patientDID = "0x4390CDBBdf5ACD2c45906fF8eB3a051Bb83e5DBB";

// You should combine all data into one string and hash it
const combinedData = ddrData + patientDID;

// Add "0x" to make sure it's a bytes32 string
console.log("0x" + keccak256(combinedData).toString("hex"));
> '0xa42cafe5e7198af9f202182ed81022e5ccc6c4386e7b65f9089941dd801eead0'
```

Our final `hashValue` is `0xa42cafe5e7198af9f202182ed81022e5ccc6c4386e7b65f9089941dd801eead0`.
