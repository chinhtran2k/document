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
import { DIDManager } from "didManager";
import { Connection } from "connection";

const connection = new Connection("http://localhost:8545");
const dids = new DIDManager(connection);
```
