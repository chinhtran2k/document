---
icon: dot
order: 2
---

# Connection

Connection function for web3 connection, almost class of this package use this connection to interact with Ethereum as a web3 head.

## Import

```ts
import { Connection } from "@hpa3-blockchain/wallet/dist";

const connection = new Connection();
```

---

### getBlock

```ts
connection.getBlock(blockHashOrBlockNumber);
```

Get all transactions of block

#### Parameters

[!badge variant="warning" text="blockHashOrBlockNumber"] - [!badge variant="warning" text="string"]: The block hash or block number

#### Returns

[!badge variant="danger" text="Object"]: The block object:

- `number` - `Number`: The block number. null if a pending block.
- `hash` `32 Bytes` - `String`: Hash of the block. null if a pending block.
- `parentHash` `32 Bytes` - String: Hash of the parent block.
- `baseFeePerGas` - `Number`: Minimum to be charged to send a transaction on the network
- `nonce` `8 Bytes` - `String`: Hash of the generated proof-of-work. null if a pending block.
- `sha3Uncles` `32 Bytes` - `String`: SHA3 of the uncles data in the block.
- `logsBloom` `256 Bytes` - `String`: The bloom filter for the logs of the block. null if a pending block.
- `transactionsRoot` `32 Bytes` - `String`: The root of the transaction trie of the block.
- `stateRoot` `32 Bytes` - `String`: The root of the final state trie of the block.
- `miner` - `String`: The address of the beneficiary to whom the mining rewards were given.
- `difficulty` - `String`: Integer of the difficulty for this block.
- `totalDifficulty` - `String`: Integer of the total difficulty of the chain until this block.
- `extraData` - `String`: The “extra data” field of this block.
- `size` - `Number`: Integer the size of this block in bytes.
- `gasLimit` - `Number`: The maximum gas allowed in this block.
- `gasUsed` - `Number`: The total used gas by all transactions in this block.
- `timestamp` - `Number`: The unix timestamp for when the block was collated.
- `transactions` - `Array`: Array of transaction objects, or 32 Bytes transaction hashes depending on the returnTransactionObjects parameter.
- `uncles` - `Array`: Array of uncle hashes.

#### Example

```ts
connection.getBlock(1407310).then(console.log);
> {
  parentHash: '0xf84358e0031a5b2c57bdcb53d4bebfa9a88a79c4a0f82b05f1d3504e268f7e69',
  sha3Uncles: '0x1dcc4de8dec75d7aab85b567b6ccd41ad312451b948a7413f0a142fd40d49347',
  miner: '0x0000000000000000000000000000000000000000',
  stateRoot: '0xdacb0695568f2d67129ca9e552b8edfd6fc240f23bb9703de4eda0597396ab4c',
  transactionsRoot: '0x1c312f1e92e1b44b14c6d2b4d8d28f7ddee1d61c13d3b19cf2001de5d60dca42',
  receiptsRoot: '0x119e4fd19c73f933f3b35d950739c60e60b6aec66f6aafd36f2a530387195480',
  logsBloom: '0x00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000',
  difficulty: '1407310',
  totalDifficulty: '1407310',
  size: 1627,
  number: 1407310,
  gasLimit: 700000000,
  gasUsed: 427810,
  timestamp: 1667364589,
d15bc72c1a1dcb8fcd53e86010735dbb92677c4ed0c1b9d91db273ab869a81bf4cb4e68f263a51028b4a24b3ae01f8c9b841663a5a73723bbc2ed1400cd15bc72c1a1dcb8fcd53e86010735dbb92677c4ed0c1b9d91db273ab869a81bf4cb4e68f263a51028b4a24b3ae01f8c9b841663a5a73723bbc2ed1400c752eeb24aad9ee15aaf2b4b26698f66090a18620f4532b2369c001cfab2445874938007067af48b3efdae3034178e90d9451985b9100b8417183a680f175bc64ddfde0934dee2e2eab2af25f177c0966c879b69d89488bdd33bd0daa21018de4042bff92cf01630c76792d7686132877719aadddf45cf1d400b841e92bca7a756143c7000a58f39a810a74a9eecd61171187b7fdb70d8a6ad982b614bee77f9377e5a9f315989a37fd43b41cfcc383b322dd11ec63eda972ae2a7e00',  mixHash: '0x63746963616c2062797a616e74696e65206661756c7420746f6c6572616e6365',
  nonce: '0x0000000000000000',
  hash: '0xa0d2199588e9111c427691bfeb7daaa0a5c02db48e0bba334f849e81dd8edd5e',
  transactions: [
    '0x3ea92dcd4cd782d305df22c313c7d3afc8d614f213560a8107d1ffab18799ce9'
  ],
  uncles: []
}
```

---

### getTransactionData

```ts
connection.getTransactionData(transactionHash);
```

Returns a transaction matching the given transaction hash.

#### Parameters

[!badge variant="warning" text="transactionHash"] - [!badge variant="warning" text="string"]: The transaction hash

#### Returns

[!badge variant="danger" text="Object"]: A transaction object its hash `transactionHash`:

- `hash` `32 Bytes` - `String`: Hash of the transaction.
- `nonce` - `Number`: The number of transactions made by the sender prior to this one.
- `blockHash` `32 Bytes` - `String`: Hash of the block where this transaction was in. null if pending.
- `blockNumber` - `Number`: Block number where this transaction was in. null if pending.
- `transactionIndex` - `Number`: Integer of the transactions index position in the block. null if pending.
- `from` - `String`: Address of the sender.
- `to` - `String`: Address of the receiver. null if it’s a contract creation transaction.
- `value` - `String`: Value transferred in wei.
- `gasPrice` - `String`: Gas price provided by the sender in wei.
- `gas` - `Number`: Gas provided by the sender.
- `input` - `String`: The data sent along with the transaction.

#### Example

```ts
connection.getTransactionData('0x9fc76417374aa880d4449a1f7f31ec597f00b1f6f3dd2d66f4c9c6c445836d8b§234')
.then(console.log);
> {
    "hash": "0x9fc76417374aa880d4449a1f7f31ec597f00b1f6f3dd2d66f4c9c6c445836d8b",
    "nonce": 2,
    "blockHash": "0xef95f2f1ed3ca60b048b4bf67cde2195961e0bba6f70bcbea9a2c4e133e34b46",
    "blockNumber": 3,
    "transactionIndex": 0,
    "from": "0xa94f5374fce5edbc8e2a8697c15331677e6ebf0b",
    "to": "0x6295ee1b4f6dd65047762f924ecd367c17eabf8f",
    "value": '123450000000000000',
    "gas": 314159,
    "gasPrice": '2000000000000',
    "input": "0x57cb2fc4"
}
```

---

### getTransactionReceipt

```ts
connection.getTransactionReceipt(transactionHash);
```

Returns a transaction matching the given transaction hash.

#### Parameters

[!badge variant="warning" text="transactionHash"] - [!badge variant="warning" text="string"]: The transaction hash

#### Returns

[!badge variant="danger" text="Object"]: A transaction object its hash `transactionHash`:

- `hash` `32 Bytes` - `String`: Hash of the transaction.
- `nonce` - `Number`: The number of transactions made by the sender prior to this one.
- `blockHash` `32 Bytes` - `String`: Hash of the block where this transaction was in. null if pending.
- `blockNumber` - `Number`: Block number where this transaction was in. null if pending.
- `transactionIndex` - `Number`: Integer of the transactions index position in the block. null if pending.
- `from` - `String`: Address of the sender.
- `to` - `String`: Address of the receiver. null if it’s a contract creation transaction.
- `value` - `String`: Value transferred in wei.
- `gasPrice` - `String`: Gas price provided by the sender in wei.
- `gas` - `Number`: Gas provided by the sender.
- `input` - `String`: The data sent along with the transaction.

#### Example

```ts
connection.getTransactionReceipt('0x9fc76417374aa880d4449a1f7f31ec597f00b1f6f3dd2d66f4c9c6c445836d8b§234')
.then(console.log);

> {
    "hash": "0x9fc76417374aa880d4449a1f7f31ec597f00b1f6f3dd2d66f4c9c6c445836d8b",
    "nonce": 2,
    "blockHash": "0xef95f2f1ed3ca60b048b4bf67cde2195961e0bba6f70bcbea9a2c4e133e34b46",
    "blockNumber": 3,
    "transactionIndex": 0,
    "from": "0xa94f5374fce5edbc8e2a8697c15331677e6ebf0b",
    "to": "0x6295ee1b4f6dd65047762f924ecd367c17eabf8f",
    "value": '123450000000000000',
    "gas": 314159,
    "gasPrice": '2000000000000',
    "input": "0x57cb2fc4"
}

```
