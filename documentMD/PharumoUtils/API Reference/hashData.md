---
icon: dot
---

# Hash data

This module for hashing data

## Main function

---

### hashData

```ts
hashData(data);
```

Hashes the given data using the Keccak-256 hash function.

#### Parameters

[!badge variant="warning" text="data"] - [!badge variant="warning" text="string"]: The data to be hashed.

!!! Note
Please combine all raw data to `one` string. If your data look like this:

```
const obj_A = {
  "name": "John",
  "phone": "+84123456789"
}
```

Then the `data` input must be `str(obj_A.name + obj_A.phone)` or `obj_A.toString()`
!!!

#### Returns

[!badge variant="danger" text="string"]: The Keccak-256 hash of the data as a hexadecimal string.

#### Example

```ts
const obj_A = {
    name: "John",
    phone: "+84123456789",
  };
hashData(obj_A.toString()).then(console.log);
> "0x7bc087f4ef9d0dc15fef823bff9c78cc5cca8be0a85234afcfd807f412f40877"
```
