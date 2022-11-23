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

## Adding DataIntegrity

```ts
import { CONFIG } from "./src/config";
import { Connection } from "./src/utils";
import { DDR , Patient, POCStudy } from "./src/action";

const connection = new Connection("http://localhost:8545");

const ddr =new DDR(connection);
const patient =new Patient(connection);
const erc20Proxy = new ERC20Proxy(connection);
const pocStudy =new POCStudy(connection);
```
