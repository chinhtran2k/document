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

## Adding DIDManager

```ts
import { Connection } from "@hpa3-blockchain/wallet/dist";
import { DIDManager } from "@hpa3-blockchain/dids-manager";

const connection = new Connection("http://localhost:8545");
const dids = new DIDManager(connection);
```
