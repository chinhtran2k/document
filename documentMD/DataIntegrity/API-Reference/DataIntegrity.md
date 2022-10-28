---
icon: dot
---

# Data Integrity

Data Integrity SDK for manage ERC721

## Main function

---

### mint

```ts
dataIntegrity.mint(privateKey, didAddress, imageHash, [tokenURI]);
```

Mint (Save) prescription hash to DataIntegrity contract

#### Parameters

1. [!badge variant="warning" text="privateKey"] - [!badge variant="warning" text="string"]: Private key of account that has permission to interact with DID
2. [!badge variant="warning" text="didAddress"] - [!badge variant="warning" text="string"]: DID contract address which will call mint function
3. [!badge variant="warning" text="imageHash"] - [!badge variant="warning" text="string"]: The keccak256 hash of prescription image
4. [!badge variant="warning" text="tokenURI"] - [!badge variant="warning" text="string"] (optional): The uri of prescription

#### Returns

[!badge variant="danger" text="Object"]: The generated wallet.

#### Example

```ts

```

