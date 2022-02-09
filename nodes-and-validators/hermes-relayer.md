# Hermes Relayer Tutorial

In this tutorial will be provided information how easy and fast setup Hermes IBC relayer

## Hermes Official Documentation https://hermes.informal.systems/

Pre-requisites:

```
sudo apt update && sudo apt upgrade -y
sudo apt install librust-openssl-dev build-essential git -y
```
Install rust (https://www.rust-lang.org/tools/install)
```
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
```

## Hermes Installation

```
git clone https://github.com/informalsystems/ibc-rs.git hermes
cd hermes
git checkout v0.11.1   ### Can check latest version https://hermes.informal.systems/installation.html#install-by-downloading
cargo install ibc-relayer-cli --bin hermes
sudo cp target/release/hermes /usr/bin
```

Make hermes config & keys directory, copy config-template to config directory:

```
mkdir -p $HOME/.hermes
nano $HOME/.hermes/config.toml
```

Paste hermes config from example and fix ip address to your rpc nodes

```
cat <<EOF > /$HOME/.hermes/config.toml
[global]
log_level = 'debug'

[mode]

[mode.clients]
enabled = false
refresh = false
misbehaviour = false

[mode.connections]
enabled = false

[mode.channels]
enabled = false

[mode.packets]
enabled = true
clear_interval = 100
clear_on_start = true
#filter = enabled
tx_confirmation = false

[rest]
enabled = true
host = '127.0.0.1'
port = 3000

[telemetry]
enabled = false
host = '127.0.0.1'
port = 3001

[[chains]]
id = 'osmosis-1'
rpc_addr = 'http://localhost:26657'
websocket_addr = 'ws://localhost:26657/websocket'
grpc_addr = 'http://localhost:9090'
rpc_timeout = '30s'
account_prefix = 'osmo'
key_name = 'osmosis'
store_prefix = 'ibc'
max_gas = 15000000
max_msg_num = 10
gas_price = { price = 0.0001, denom = 'uosmo' }
gas_adjustment = 1
clock_drift = '15s'
trusting_period = '9days'
trust_threshold = { numerator = '1', denominator = '3' }
memo_prefix = 'SGTstake IBC service'
[chains.packet_filter]
policy = 'allow'
list = [
  ['transfer', 'channel-75']
]

[[chains]]
id = 'juno-1'
rpc_addr = 'http://localhost:26657'
grpc_addr = 'http://localhost:9090'
websocket_addr = 'ws://localhost:26657/websocket'
rpc_timeout = '30s'
account_prefix = 'juno'
key_name = 'juno'
store_prefix = 'ibc'
max_tx_size = 180000
max_gas = 2000000
gas_price = { price = 0.0025, denom = 'ujuno' }
gas_adjustment = 0.1
clock_drift = '15s'
trusting_period = '14days'
trust_threshold = { numerator = '1', denominator = '3' }
memo_prefix = 'SGTstake IBC service'
[chains.packet_filter]
policy = 'allow'
list = [
  ['transfer', 'channel-20']
  ]

[[chains]]
id = 'stargaze-1'
rpc_addr = 'http://localhost:26657'
grpc_addr = 'http://localhost:9090'
websocket_addr = 'ws://localhost:26657/websocket'
rpc_timeout = '10s'
account_prefix = 'stars'
key_name = 'relayer'
store_prefix = 'ibc'
max_gas = 2000000
gas_price = { price = 0.0025, denom = 'ustars' }
gas_adjustment = 0.1
clock_drift = '300s'
trusting_period = '10days'
trust_threshold = { numerator = '1', denominator = '3' }
memo_prefix = 'SGTstake IBC service'
[chains.packet_filter]
policy = 'allow'
list = [
  ['transfer', 'channel-0'],['transfer', 'channel-5']
  ]
EOF

```
You can validate your hermes configuration file:
```
hermes config validate
INFO ThreadId(01) using default configuration from '/home/relay/.hermes/config.toml'
Success: "validation passed successfully"
```

Add your relaying-wallets to hermes' keyring

Best practice is to use the same mnemonic over all networks, do not use your relaying-addresses for anything else because it might lead to mismatched account sequence errors.
```
hermes keys restore osmosis-1 -m "12 or 24 magic words"
hermes keys restore juno-1 -m "12 or 24 magic words"
hermes keys restore stargaze-1 -m "12 or 24 magic words"
```
