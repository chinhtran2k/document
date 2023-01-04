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
import { DDR , Claim, DDRBranch, DisclosureBranch, Patient, POCStudy, DataIntegrity} from "./src/action";

const connection = new Connection("http://localhost:8545");

const ddr =new DDR(connection);
const claim =new Claim(connection);
const ddrBranch =new DDRBranch(connection);
const disclosureBranch =new DisclosureBranch(connection);
const patient =new Patient(connection);
const erc20Proxy = new ERC20Proxy(connection);
const pocStudy =new POCStudy(connection);
const dataIntegrity = new DataIntegrity(connection);
```
