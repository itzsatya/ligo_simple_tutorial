
# Simple Ligo Smart Contract 

A simple tezos smart contract build using Ligo (jsligo). Which can add or subtract the values given to it.

## Links

[Better-to-dev link for the deployed smart contract](https://better-call.dev/ithacanet/KT19KYFRCJNJtJyuPEhamHv4QX6GRtULF5J1/operations)


## Installation

Cloning and Installing components for the contract

```bash
  git clone https://github.com/itzsatya/ligo_simple_tutorial.git
  cd ligo_simple_tutorial
  sudo dpkg -i ligo.deb
  ligo --version
  sudo add-apt-repository ppa:serokell/tezos && sudo apt-get update
  sudo add-apt-repository ppa:serokell/tezo-rc && sudo apt-get update
  sudo apt-get install -y tezos-client tezos-node tezos-baker-012-psithaca tezos-accuser-012-psithaca
```

Now, commands to execute to put contract on testnet and test it before doing so.

```bash
  ligo compile contract simple.jsligo -o simple.tz
  ligo run interpret "add(10,32)" --init-file simple.jsligo
  ligo run dry-run simple.jsligo "Increment(32)" "40"
  ligo run test simple.jsligo
  tezos-node config init --network ithacanet
  tezos-client --endpoint https://rpc.ithacanet.teztnets.xyz/ config update 
  tezos-client activate account alice with ithacanet.json
  tezos-client originate contract simple transferring 0 from alice running simple.tz --init 10 --burn-cap 0.1
```