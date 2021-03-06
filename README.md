# profitability-service

### Prerequisites

profitability-service requires nodejs, npm and optionally pm2 to run.


### Installation

```sh
git clone https://github.com/felixbrucker/profitability-service
cd profitability-service
npm install
npm install pm2 -g
```

### Run

```sh
pm2 start process.json
```

or

```sh
npm start
```

to startup on boot:

```sh
pm2 save
pm2 startup
```

note: windows users need the following instead:

```sh
npm install pm2-windows-startup -g
pm2-startup install
pm2 save
```

### Update software

run ``` git pull ```


### JSON template to query

```sh
{
	"algos": {
		"x11": {"hashrate":150000000},
		"x13": {"hashrate":150000000},
		"x14": {"hashrate":150000000},
		"x15": {"hashrate":150000000},
		"quark": {"hashrate":150000000},
		"qubit": {"hashrate":150000000}
	},
	"region": "eu",
	"name": "Baikal Mini Miner"
}
```

Hashrate is in Hash/sec, region can be one of these: ["eu","usa","hk","jp"]

name is optional for stats

### JSON template for responses from the server

```sh
{
	"result": {
		"url": "stratum+tcp://x11.eu.nicehash.com:3336",
		"profitability": 1.0317e-11,
		"pool": "nicehash",
		"algo": "x11",
		"profitabilityArr": [
			{"algo":"x11", "profitability": 0.00154755},
			{"algo":"quark", "profitability": 0.0012342},
			{"algo":"x13", "profitability": 0.0011424},
			{"algo":"qubit", "profitability": 0.0010815},
			{"algo":"x15", "profitability": 0.000015},
			{"algo":"x14", "profitability": 0}	
		]
	}
}
```

in case something is wrong/missing in the query:

```sh
{
	"result": false
}
```

### complete list of supported algos

* argon2
* blake2s
* blake256r8
* c11
* decred
* lbry
* lyra2rev2
* m7m
* myr-gr
* neoscrypt
* nist5
* qubit
* quark
* scrypt
* sha256
* sib
* skein
* veltor
* x11
* x11evo
* x13
* x14
* x15
* x17
* yescrypt
* scryptnf
* keccak
* lyra2re
* whirlpoolx
* axiom
* scryptjanenf16
* blake256r14
* blake256r8vnl
* hodl
* daggerhashimoto
* cryptonight
* equihash
* pascal


### Todos

 - Error handling
 - Properly use async Methods
 - Properly send responses to indicate the result to frontend
 - Add Code Comments
 - Write Tests


License
----

GNU GPLv3 (see LICENSE)
