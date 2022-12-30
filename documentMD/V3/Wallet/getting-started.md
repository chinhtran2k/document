---
order: 100
icon: rocket
---

# Getting started

---

!!! Note:
This SDK is wroted by typescript
!!!

---

## Adding Wallet SDK

```ts
import { WalletBaseExtend } from "@hpa3-blockchain/wallet/dist";
import { Connection } from "@hpa3-blockchain/wallet/dist";

const connection = new Connection("http://localhost:8545");
const wallet = new WalletBaseExtend(connection);
```
