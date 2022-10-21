---
icon: dot
order: 100
---

# WalletBaseExtend

Extend Wallet like metamask base on WalletBase in web3-core

---

## Main functions

### createWallet

```ts
wallet.createWallet();
```

Generates the wallet with one account. If wallets already exist they will not be overridden.

#### Parameters

none

#### Returns

[!badge variant="danger" text="Object"]: The generated wallet.

#### Example

```ts
wallet.createWalletFromMnemonic("use share wealth depth leader mind check circle heavy cake dragon trap");
> WalletBase {
  ...
  mnemonic: 'use share wealth depth leader mind check circle heavy cake dragon trap',
  wallet: <ref *1> Wallet {
    '0': {...},
    ...
    '0x32eB821d88F2E650d4732C4CE974A30Bb4296949': {...},
    '0x32eb821d88f2e650d4732c4ce974a30bb4296949': {...}
  },
  walletImported: [],
  defaultAccount: 0
}
wallet.addAccountFromPrivateKey("0x4c0883a69102937d6231471b5dbb6204fe5129617082792ae468d01a3f362318");
> WalletBase {
  ...
  mnemonic: 'use share wealth depth leader mind check circle heavy cake dragon trap',
  wallet: <ref *1> Wallet {
    '0': {...},
    '1': {...},
    ...
    length: 2,
    ...
    '0x32eB821d88F2E650d4732C4CE974A30Bb4296949': {...},
    '0x32eb821d88f2e650d4732c4ce974a30bb4296949': {...},
    '0x2c7536E3605D9C16a7a3D7b1898e529396a65c23': {...},
    '0x2c7536e3605d9c16a7a3d7b1898e529396a65c23': {...}
  },
  walletImported: [ 1 ],
  defaultAccount: 0
}
wallet.removeAccount(1);
> WalletBase {
  ...
  mnemonic: 'use share wealth depth leader mind check circle heavy cake dragon trap',
  wallet: <ref *1> Wallet {
    '0': {...},
    ...
    length: 1,
    ...
    '0x32eB821d88F2E650d4732C4CE974A30Bb4296949': {...},
    '0x32eb821d88f2e650d4732c4ce974a30bb4296949': {...}
  },
  walletImported: [],
  defaultAccount: 0
}
```

---

### createWalletFromMnemonic

```ts
wallet.createWalletFromMnemonic(mnemonic);
```

Generates the wallet with one account from mnemonic. If wallets already exist they will not be overridden.

#### Parameters

[!badge variant="warning" text="mnemonic"] - [!badge variant="warning" text="String"]: A string with 12 valid words as mnemonic to generate wallet.

#### Returns

[!badge variant="danger" text="Object"]: The generated wallet.

#### Example

```ts
wallet.createWalletFromMnemonic("use share wealth depth leader mind check circle heavy cake dragon trap");
> WalletBase {
  ...
  mnemonic: 'use share wealth depth leader mind check circle heavy cake dragon trap',
  wallet: <ref *1> Wallet {
    '0': {...},
    ...
    '0x32eB821d88F2E650d4732C4CE974A30Bb4296949': {...},
    '0x32eb821d88f2e650d4732c4ce974a30bb4296949': {...}
  },
  walletImported: [],
  defaultAccount: 0
}
```

---

### addAccountFromPrivateKey

```ts
wallet.addAccountFromPrivateKey(privateKey);
```

Add account from private key to wallet

#### Parameters

[!badge variant="warning" text="privateKey"] - [!badge variant="warning" text="String"]: A private key

#### Returns

[!badge variant="danger" text="Object"]: The wallet.

#### Example

```ts
wallet.createWalletFromMnemonic("use share wealth depth leader mind check circle heavy cake dragon trap");
> WalletBase {
  ...
  mnemonic: 'use share wealth depth leader mind check circle heavy cake dragon trap',
  wallet: <ref *1> Wallet {
    '0': {
      address: '0x32eB821d88F2E650d4732C4CE974A30Bb4296949',
      ...
    },
    ...
    '0x32eB821d88F2E650d4732C4CE974A30Bb4296949': {...},
    '0x32eb821d88f2e650d4732c4ce974a30bb4296949': {...}
  },
  walletImported: [],
  defaultAccount: 0
}
wallet.addAccountFromPrivateKey("0x4c0883a69102937d6231471b5dbb6204fe5129617082792ae468d01a3f362318");
> WalletBase {
  ...
  mnemonic: 'use share wealth depth leader mind check circle heavy cake dragon trap',
  wallet: <ref *1> Wallet {
    '0': {...},
    '1': {...},
    ...
    length: 2,
    ...
    '0x32eB821d88F2E650d4732C4CE974A30Bb4296949': {...},
    '0x32eb821d88f2e650d4732c4ce974a30bb4296949': {...},
    '0x2c7536E3605D9C16a7a3D7b1898e529396a65c23': {...},
    '0x2c7536e3605d9c16a7a3d7b1898e529396a65c23': {...}
  },
  walletImported: [ 1 ],
  defaultAccount: 0
}

```

---

### addIncrementalAccount

```ts
wallet.addIncrementalAccount();
```

Add next account from mnemonic

#### Parameters

none

#### Returns

[!badge variant="danger" text="Object"]: The wallet.

#### Example

```ts
wallet.createWalletFromMnemonic("use share wealth depth leader mind check circle heavy cake dragon trap");
> WalletBase {
  ...
  mnemonic: 'use share wealth depth leader mind check circle heavy cake dragon trap',
  wallet: <ref *1> Wallet {
    '0': {...},
    ...
    '0x32eB821d88F2E650d4732C4CE974A30Bb4296949': {...},
    '0x32eb821d88f2e650d4732c4ce974a30bb4296949': {...}
  },
  walletImported: [],
  defaultAccount: 0
}
wallet.addAccountFromPrivateKey("0x4c0883a69102937d6231471b5dbb6204fe5129617082792ae468d01a3f362318");
> WalletBase {
  ...
  mnemonic: 'use share wealth depth leader mind check circle heavy cake dragon trap',
  wallet: <ref *1> Wallet {
    '0': {...},
    '1': {...},
    ...
    length: 2,
    ...
    '0x32eB821d88F2E650d4732C4CE974A30Bb4296949': {...},
    '0x32eb821d88f2e650d4732c4ce974a30bb4296949': {...},
    '0xd627E4CFAEd1026077aBe9Fd43Aa750be925a077': {...},
    '0xd627e4cfaed1026077abe9fd43aa750be925a077': {...}
  },
  walletImported: [],
  defaultAccount: 0
}
```

---

### removeAccount

```ts
wallet.removeAccount(accountImportedIndex);
```

Remove an imported account from wallet

#### Parameters

[!badge variant="warning" text="accountImportedIndex"] - [!badge variant="warning" text="number"]: An index of imported account in `walletImported`

#### Returns

[!badge variant="danger" text="Object"]: The wallet.

#### Example

```ts
wallet.createWalletFromMnemonic("use share wealth depth leader mind check circle heavy cake dragon trap");
> WalletBase {
  ...
  mnemonic: 'use share wealth depth leader mind check circle heavy cake dragon trap',
  wallet: <ref *1> Wallet {
    '0': {...},
    ...
    '0x32eB821d88F2E650d4732C4CE974A30Bb4296949': {...},
    '0x32eb821d88f2e650d4732c4ce974a30bb4296949': {...}
  },
  walletImported: [],
  defaultAccount: 0
}
wallet.addAccountFromPrivateKey("0x4c0883a69102937d6231471b5dbb6204fe5129617082792ae468d01a3f362318");
> WalletBase {
  ...
  mnemonic: 'use share wealth depth leader mind check circle heavy cake dragon trap',
  wallet: <ref *1> Wallet {
    '0': {...},
    '1': {...},
    ...
    length: 2,
    ...
    '0x32eB821d88F2E650d4732C4CE974A30Bb4296949': {...},
    '0x32eb821d88f2e650d4732c4ce974a30bb4296949': {...},
    '0x2c7536E3605D9C16a7a3D7b1898e529396a65c23': {...},
    '0x2c7536e3605d9c16a7a3d7b1898e529396a65c23': {...}
  },
  walletImported: [ 1 ],
  defaultAccount: 0
}
wallet.removeAccount(1);
> WalletBase {
  ...
  mnemonic: 'use share wealth depth leader mind check circle heavy cake dragon trap',
  wallet: <ref *1> Wallet {
    '0': {...},
    ...
    length: 1,
    ...
    '0x32eB821d88F2E650d4732C4CE974A30Bb4296949': {...},
    '0x32eb821d88f2e650d4732c4ce974a30bb4296949': {...}
  },
  walletImported: [],
  defaultAccount: 0
}
```

---

### encryptWallet

```ts
wallet.encryptWallet(password);
```

Encrypt wallet with password

#### Parameters

[!badge variant="warning" text="password"] - [!badge variant="warning" text="String"]: The password which will be used for encryption.

#### Returns

[!badge variant="danger" text="Object"]: The added wallet with core wallet encrypted.

#### Example

```ts
wallet.createWalletFromMnemonic("use share wealth depth leader mind check circle heavy cake dragon trap");
> WalletBase {
  ...
  mnemonic: 'use share wealth depth leader mind check circle heavy cake dragon trap',
  wallet: <ref *1> Wallet {
    '0': {...},
    ...
    '0x32eB821d88F2E650d4732C4CE974A30Bb4296949': {...},
    '0x32eb821d88f2e650d4732c4ce974a30bb4296949': {...}
  },
  ...
}
wallet.encryptWallet("secret");
> WalletBase {
  ...
  mnemonic: 'U2FsdGVkX181NBnOd5Mvv9NH2Meo+S2nnDpnwODoJ4FRm7aXebkRsQn88RccfZ/iZ+8OcPRKwRGFi9IT0OAgsVuThT9T1f5MbPnU/uiwcsP4kIWWHHYnNOGBMbPAdCGk',
  wallet: [
    {
      version: 3,
      id: 'f04d664d-fd3a-4b56-9851-14973be5c934',
      address: '32eb821d88f2e650d4732c4ce974a30bb4296949',
      crypto: [Object]
    }
  ],
  ...
}
```

---

### decryptWallet

```ts
wallet.decryptWallet(password);
```

Decrypt wallet with password

#### Parameters

[!badge variant="warning" text="password"] - [!badge variant="warning" text="String"]: The password which will be used for decryption.

#### Returns

[!badge variant="danger" text="Object"]: The added wallet with core wallet decrypted.

#### Example

```ts
wallet.createWalletFromMnemonic("use share wealth depth leader mind check circle heavy cake dragon trap");
> WalletBase {
  ...
  wallet: <ref *1> Wallet {
    '0': {...},
    ...
    '0x32eB821d88F2E650d4732C4CE974A30Bb4296949': {...},
    '0x32eb821d88f2e650d4732c4ce974a30bb4296949': {...}
  },
  ...
}
wallet.encryptWallet("secret");
> WalletBase {
  ...
  mnemonic: 'U2FsdGVkX181NBnOd5Mvv9NH2Meo+S2nnDpnwODoJ4FRm7aXebkRsQn88RccfZ/iZ+8OcPRKwRGFi9IT0OAgsVuThT9T1f5MbPnU/uiwcsP4kIWWHHYnNOGBMbPAdCGk',
  wallet: [
    {
      version: 3,
      id: 'f04d664d-fd3a-4b56-9851-14973be5c934',
      address: '32eb821d88f2e650d4732c4ce974a30bb4296949',
      crypto: [Object]
    }
  ],
  ...
}
wallet.decryptWallet("secret");
> WalletBase {
  ...
  mnemonic: 'use share wealth depth leader mind check circle heavy cake dragon trap',
  wallet: <ref *1> Wallet {
    '0': {...},
    ...
    '0x32eB821d88F2E650d4732C4CE974A30Bb4296949': {
      address: '0x32eB821d88F2E650d4732C4CE974A30Bb4296949',
      privateKey: '0x5e5b09bc7fba7bb4029847ecb15ffc62ab7364ef9233297d27735971817eef2b',
      ...
    },
    '0x32eb821d88f2e650d4732c4ce974a30bb4296949': {
      address: '0x32eB821d88F2E650d4732C4CE974A30Bb4296949',
      privateKey: '0x5e5b09bc7fba7bb4029847ecb15ffc62ab7364ef9233297d27735971817eef2b',
      ...
    }
  },
  ...
}
```

---

### transfer

```ts
wallet.transfer(accountId, to, value);
```

Transfer from an account in wallet to an address

#### Parameters

1. [!badge variant="warning" text="accountId"] - [!badge variant="warning" text="number"]: The account id in wallet.
2. [!badge variant="warning" text="to"] - [!badge variant="warning" text="String"]: The address to transfer to.
3. [!badge variant="warning" text="value"] - [!badge variant="warning" text="Number"]: The value to transfer.

#### Returns

1. [!badge variant="danger" text="nonce"] - [!badge variant="danger" text="number"]: The nonce of the transaction.
2. [!badge variant="danger" text="receipt"] - [!badge variant="danger" text="object"]: A transaction receipt object, or null if no receipt was found.
   - `status` - `Boolean`: `TRUE` if the transaction was successful, `FALSE` if the EVM reverted the transaction.
   - `blockHash` 32 Bytes - `String`: Hash of the block where this transaction was in.
   - `blockNumber` - `Number` (or `hex String`): Block number where this transaction was in.
   - `transactionHash` 32 Bytes - `String`: Hash of the transaction.
   - `transactionIndex`- `Number` (or `hex String`): Integer of the transactions index position in the block.
   - `from` - `String`: Address of the sender.
   - `to` - `String`: Address of the receiver. null when it’s a contract creation transaction.
   - `contractAddress` - `String`: The contract address created, if the transaction was a contract creation, otherwise null.
   - `cumulativeGasUsed` - `Number` (or `hex String`): The total amount of gas used when this transaction was executed in the block.
   - `gasUsed` - `Number` (or `hex String`): The amount of gas used by this specific transaction alone.
   - `logs` - `Array`: Array of log objects, which this transaction generated.

#### Example

```ts
wallet.createWalletFromMnemonic("use share wealth depth leader mind check circle heavy cake dragon trap");
> WalletBase {
  ...
  wallet: <ref *1> Wallet {
    '0': {...},
    ...
    '0x32eB821d88F2E650d4732C4CE974A30Bb4296949': {...},
    '0x32eb821d88f2e650d4732c4ce974a30bb4296949': {...}
  },
  ...
}
wallet.transfer(0, "0xd627E4CFAEd1026077aBe9Fd43Aa750be925a077", 5);
> {
  nonce: 0,
  receipt: {
    transactionHash: '0xd06433e90341fa3e01fb443334d5ebb1e568887712074674b147c4bed8f00c66',
    transactionIndex: 0,
    blockHash: '0x3941967f9660339576accfe30775733199e19b69414ece1c7ec8e825622f0e95',
    blockNumber: 1,
    from: '0x32eb821d88f2e650d4732c4ce974a30bb4296949',
    to: '0xd627e4cfaed1026077abe9fd43aa750be925a077',
    gasUsed: 21000,
    cumulativeGasUsed: 21000,
    contractAddress: null,
    logs: [],
    status: true,
    logsBloom: '0x00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
  }
}
```

---

## Getters

---

### getListAccount

```ts
wallet.getListAccount([wallet]);
```

Get list of account address in wallet

#### Parameters

[!badge variant="warning" text="Object"]: The wallet object.

#### Returns

[!badge variant="danger" text="Array\<String>"]: List of account address in wallet.

#### Example

```ts
wallet.createWalletFromMnemonic("use share wealth depth leader mind check circle heavy cake dragon trap");
> WalletBase {
  ...
  mnemonic: 'use share wealth depth leader mind check circle heavy cake dragon trap',
  wallet: <ref *1> Wallet {
    '0': {
      address: '0x32eB821d88F2E650d4732C4CE974A30Bb4296949',
      ...
    },
    ...
    '0x32eB821d88F2E650d4732C4CE974A30Bb4296949': {...},
    '0x32eb821d88f2e650d4732c4ce974a30bb4296949': {...}
  },
  walletImported: [],
  defaultAccount: 0
}
wallet.addAccountFromPrivateKey("0x4c0883a69102937d6231471b5dbb6204fe5129617082792ae468d01a3f362318");
> WalletBase {
  ...
  mnemonic: 'use share wealth depth leader mind check circle heavy cake dragon trap',
  wallet: <ref *1> Wallet {
    '0': {...},
    '1': {...},
    ...
    length: 2,
    ...
    '0x32eB821d88F2E650d4732C4CE974A30Bb4296949': {...},
    '0x32eb821d88f2e650d4732c4ce974a30bb4296949': {...},
    '0x2c7536E3605D9C16a7a3D7b1898e529396a65c23': {...},
    '0x2c7536e3605d9c16a7a3d7b1898e529396a65c23': {...}
  },
  walletImported: [ 1 ],
  defaultAccount: 0
}
wallet.getListAccount();
> [
  '0x32eB821d88F2E650d4732C4CE974A30Bb4296949',
  '0x2c7536E3605D9C16a7a3D7b1898e529396a65c23'
]
```

---

### getMnemonic

```ts
wallet.getMnemonic();
```

Get mnemonic of added wallet

#### Parameters

none

#### Returns

[!badge variant="danger" text="String"]: A string of 12 valid mnemonic word of wallet.

#### Example

```ts
wallet.createWalletFromMnemonic("use share wealth depth leader mind check circle heavy cake dragon trap");
> WalletBase {
  ...
  mnemonic: 'use share wealth depth leader mind check circle heavy cake dragon trap',
  wallet: <ref *1> Wallet {
    '0': {...},
    ...
    '0x32eB821d88F2E650d4732C4CE974A30Bb4296949': {...},
    '0x32eb821d88f2e650d4732c4ce974a30bb4296949': {...}
  },
  ...
}
wallet.getMnemonic();
> 'use share wealth depth leader mind check circle heavy cake dragon trap'
```

---

### getWalletBase

```ts
wallet.getWalletBase();
```

Get WalletBase of WalletBaseExtend

#### Parameters

none

#### Returns

[!badge variant="danger" text="Object"]: A `WalletBase` object in web3-core

#### Example

```ts
wallet.createWalletFromMnemonic("use share wealth depth leader mind check circle heavy cake dragon trap");
> WalletBase {
  ...
  mnemonic: 'use share wealth depth leader mind check circle heavy cake dragon trap',
  wallet: <ref *1> Wallet {
    '0': {...},
    ...
    '0x32eB821d88F2E650d4732C4CE974A30Bb4296949': {...},
    '0x32eb821d88f2e650d4732c4ce974a30bb4296949': {...}
  },
  ...
}
wallet.getWalletBase();
> <ref *1> Wallet {
  '0': {...},
  ...
  length: 1,
  defaultKeyName: 'web3js_wallet',
  '0x32eB821d88F2E650d4732C4CE974A30Bb4296949': {...},
  '0x32eb821d88f2e650d4732c4ce974a30bb4296949': {...}
}
```

---

### getWalletImported

```ts
wallet.getWalletImported();
```

Get list index of account imported by private key

#### Parameters

none

#### Returns

[!badge variant="danger" text="Array<number>"]: A list of index of account imported by private key

#### Example

```ts
wallet.createWalletFromMnemonic("use share wealth depth leader mind check circle heavy cake dragon trap");
> WalletBase {
  ...
  mnemonic: 'use share wealth depth leader mind check circle heavy cake dragon trap',
  wallet: <ref *1> Wallet {
    '0': {
      address: '0x32eB821d88F2E650d4732C4CE974A30Bb4296949',
      ...
    },
    ...
    '0x32eB821d88F2E650d4732C4CE974A30Bb4296949': {...},
    '0x32eb821d88f2e650d4732c4ce974a30bb4296949': {...}
  },
  walletImported: [],
  defaultAccount: 0
}
wallet.addAccountFromPrivateKey("0x4c0883a69102937d6231471b5dbb6204fe5129617082792ae468d01a3f362318");
> WalletBase {
  ...
  mnemonic: 'use share wealth depth leader mind check circle heavy cake dragon trap',
  wallet: <ref *1> Wallet {
    '0': {...},
    '1': {...},
    ...
    length: 2,
    ...
    '0x32eB821d88F2E650d4732C4CE974A30Bb4296949': {...},
    '0x32eb821d88f2e650d4732c4ce974a30bb4296949': {...},
    '0x2c7536E3605D9C16a7a3D7b1898e529396a65c23': {...},
    '0x2c7536e3605d9c16a7a3d7b1898e529396a65c23': {...}
  },
  walletImported: [ 1 ],
  defaultAccount: 0
}
wallet.getWalletImported();
> [ 1 ]
```

---

### getAccount

```ts
wallet.getAccount(accountIndex);
```

Get account from wallet by index

#### Parameters

[!badge variant="warning" text="accountIndex"] - [!badge variant="warning" text="number"]: Index of account in wallet

#### Returns

[!badge variant="danger" text="Object"]: The account object base from web3-core

#### Example

```ts
wallet.createWalletFromMnemonic("use share wealth depth leader mind check circle heavy cake dragon trap");
> WalletBase {
  ...
  mnemonic: 'use share wealth depth leader mind check circle heavy cake dragon trap',
  wallet: <ref *1> Wallet {
    '0': {...},
    ...
    '0x32eB821d88F2E650d4732C4CE974A30Bb4296949': {...},
    '0x32eb821d88f2e650d4732c4ce974a30bb4296949': {...}
  },
  ...
}
wallet.getAccount(0);
> {
  address: '0x32eB821d88F2E650d4732C4CE974A30Bb4296949',
  privateKey: '0x5e5b09bc7fba7bb4029847ecb15ffc62ab7364ef9233297d27735971817eef2b',
  signTransaction: [Function: signTransaction],
  sign: [Function: sign],
  encrypt: [Function: encrypt],
  index: 0
}
```

---

### getDefaultAccount

```ts
wallet.getDefaultAccount();
```

Get default account of wallet

#### Parameters

none

#### Returns

[!badge variant="danger" text="Object"]: The account object base from web3-core

#### Example

```ts
wallet.createWalletFromMnemonic("use share wealth depth leader mind check circle heavy cake dragon trap");
> WalletBase {
  ...
  mnemonic: 'use share wealth depth leader mind check circle heavy cake dragon trap',
  wallet: <ref *1> Wallet {
    '0': {...},
    ...
    '0x32eB821d88F2E650d4732C4CE974A30Bb4296949': {...},
    '0x32eb821d88f2e650d4732c4ce974a30bb4296949': {...}
  },
  ...
}
wallet.getAccount(0);
> {
  address: '0x32eB821d88F2E650d4732C4CE974A30Bb4296949',
  privateKey: '0x5e5b09bc7fba7bb4029847ecb15ffc62ab7364ef9233297d27735971817eef2b',
  signTransaction: [Function: signTransaction],
  sign: [Function: sign],
  encrypt: [Function: encrypt],
  index: 0
}
```

---

### getNonce

```ts
wallet.getNonce(address);
```

Get nonce of an address

#### Parameters

[!badge variant="warning" text="address"] - [!badge variant="warning" text="string"]: Address of account

#### Returns

[!badge variant="danger" text="number"]: The nonce of account

#### Example

```ts
wallet.getNonce("0x32eB821d88F2E650d4732C4CE974A30Bb4296949");
> 5
```

---

## Setters

---

### setDefaultAccount

```ts
wallet.setDefaultAccount(accountIndex);
```

Set default account of wallet to interact like Metamask

#### Parameters

[!badge variant="warning" text="accountIndex"] - [!badge variant="warning" text="number"]: index of account need to set

#### Returns

[!badge variant="danger" text="Object"]: The wallet.

#### Example

```ts
wallet.createWalletFromMnemonic("use share wealth depth leader mind check circle heavy cake dragon trap");
> WalletBase {
  ...
  mnemonic: 'use share wealth depth leader mind check circle heavy cake dragon trap',
  wallet: <ref *1> Wallet {
    '0': {
      address: '0x32eB821d88F2E650d4732C4CE974A30Bb4296949',
      ...
    },
    ...
    '0x32eB821d88F2E650d4732C4CE974A30Bb4296949': {...},
    '0x32eb821d88f2e650d4732c4ce974a30bb4296949': {...}
  },
  walletImported: [],
  defaultAccount: 0
}
wallet.addAccountFromPrivateKey("0x4c0883a69102937d6231471b5dbb6204fe5129617082792ae468d01a3f362318");
> WalletBase {
  ...
  mnemonic: 'use share wealth depth leader mind check circle heavy cake dragon trap',
  wallet: <ref *1> Wallet {
    '0': {...},
    '1': {...},
    ...
    length: 2,
    ...
    '0x32eB821d88F2E650d4732C4CE974A30Bb4296949': {...},
    '0x32eb821d88f2e650d4732c4ce974a30bb4296949': {...},
    '0x2c7536E3605D9C16a7a3D7b1898e529396a65c23': {...},
    '0x2c7536e3605d9c16a7a3d7b1898e529396a65c23': {...}
  },
  walletImported: [ 1 ],
  defaultAccount: 0
}
wallet.setDefaultAccount(1);
> WalletBase {
  ...
  mnemonic: 'use share wealth depth leader mind check circle heavy cake dragon trap',
  wallet: <ref *1> Wallet {
    '0': {...},
    '1': {...},
    ...
    length: 2,
    ...
    '0x32eB821d88F2E650d4732C4CE974A30Bb4296949': {...},
    '0x32eb821d88f2e650d4732c4ce974a30bb4296949': {...},
    '0x2c7536E3605D9C16a7a3D7b1898e529396a65c23': {...},
    '0x2c7536e3605d9c16a7a3d7b1898e529396a65c23': {...}
  },
  walletImported: [ 1 ],
  defaultAccount: 1
}
```
