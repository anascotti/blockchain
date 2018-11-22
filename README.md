# blockchain

At startup, the chain contains only the genesis block 

curl http://localhost:5000/chain

```
{
	"chain": [{
		"index": 1,
		"previous_hash": 1,
		"proof": 100,
		"timestamp": 1542895618.610925,
		"transactions": []
	}],
	"length": 1
}
```

curl http://localhost:5000/mine

A new block is forged ad the miner receives a reward (1 coin) for finding the proof

```
{
	"index": 2,
	"message": "New Block Forged",
	"previous_hash": "051242a9fd8ed454a65799c1cdaf33b1343adb9b395aea59ba554cccca965322",
	"proof": 41047,
	"transactions": [{
		"amount": 1,
		"recipient": "324a886d3a3b4e15a9ca08dfe26c6b00",
		"sender": "0"
	}]
}
```

curl http://localhost:5000/chain 

```
{
	"chain": [{
		"index": 1,
		"previous_hash": 1,
		"proof": 100,
		"timestamp": 1542895618.610925,
		"transactions": []
	}, {
		"index": 2,
		"previous_hash": "051242a9fd8ed454a65799c1cdaf33b1343adb9b395aea59ba554cccca965322",
		"proof": 41047,
		"timestamp": 1542895676.9379041,
		"transactions": [{
			"amount": 1,
			"recipient": "324a886d3a3b4e15a9ca08dfe26c6b00",
			"sender": "0"
		}]
	}],
	"length": 2
}
```

curl -X POST -H "Content-Type: application/json" -d '{"sender": "d4ee26eee15148ee92c6cd394edd974e","recipient": "some-address", "amount": 10}'  http://localhost:5000/transactions
```
{"message":"Transaction will be added to Block 3"}
```
The block is not added to the chain until it is mined.

curl http://localhost:5000/chain
```
{
	"chain": [{
		"index": 1,
		"previous_hash": 1,
		"proof": 100,
		"timestamp": 1542895618.610925,
		"transactions": []
	}, {
		"index": 2,
		"previous_hash": "051242a9fd8ed454a65799c1cdaf33b1343adb9b395aea59ba554cccca965322",
		"proof": 41047,
		"timestamp": 1542895676.9379041,
		"transactions": [{
			"amount": 1,
			"recipient": "324a886d3a3b4e15a9ca08dfe26c6b00",
			"sender": "0"
		}]
	}],
	"length": 2
}
```
curl http://localhost:5000/mine

curl http://localhost:5000/chain

```
{
	"chain": [{
		"index": 1,
		"previous_hash": 1,
		"proof": 100,
		"timestamp": 1542895618.610925,
		"transactions": []
	}, {
		"index": 2,
		"previous_hash": "051242a9fd8ed454a65799c1cdaf33b1343adb9b395aea59ba554cccca965322",
		"proof": 41047,
		"timestamp": 1542895676.9379041,
		"transactions": [{
			"amount": 1,
			"recipient": "324a886d3a3b4e15a9ca08dfe26c6b00",
			"sender": "0"
		}]
	}, {
		"index": 3,
		"previous_hash": "e3105cf6103eeb312e1cdc779a55d29ea20547e4cee3992322cae1e02a3bf79e",
		"proof": 26466,
		"timestamp": 1542895840.5416977,
		"transactions": [{
			"amount": 10,
			"recipient": "some-address",
			"sender": "d4ee26eee15148ee92c6cd394edd974e"
		}, {
			"amount": 1,
			"recipient": "324a886d3a3b4e15a9ca08dfe26c6b00",
			"sender": "0"
		}]
	}],
	"length": 3
}
```

```
```