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
import { WalletBaseExtend } from "wallet";
import { Connection } from "connection";

const connection = new Connection("http://localhost:8545");
const wallet = new WalletBaseExtend(connection);
```
