# revive-rpc

Builds pallet-revive-eth-rpc from polkadot-sdk.


By default the eth-rpc binary will serve Ethereum JSON-RPC request at :8545 and
try to connect to the node's rpc using ws://127.0.0.1:9944, where it will proxy
the requests - it reuses the same code that is used to start the substrate rpc,
and as such exposes all the same cli arguments to configure the rpc, including
the one for starting the prometheus endpoint.

## Ports

- **8545**: Ethereum JSON-RPC HTTP/WebSocket server (standard Ethereum RPC port)
- **9616**: Prometheus metrics endpoint for monitoring

## Usage

### Download Binary

Get the latest release from the releases page.

### Run Binary Directly

```bash # connect to local substrate node ./eth-rpc-linux-x64 --node-rpc-url
ws://localhost:9944

# specify custom ports ./eth-rpc-linux-x64 \ --eth-rpc-listen-address
127.0.0.1:8545 \ --prometheus-listen-address 127.0.0.1:9616 ```

### Connect MetaMask

1. Add custom network in MetaMask
2. RPC URL: `http://localhost:8545`
3. Chain ID: Check with `eth_chainId` RPC call
4. Currency symbol: ETH (or your chain's native token)

### Monitor Metrics

Prometheus metrics available at `http://localhost:9616/metrics`

## Build from Source

```bash git clone https://github.com/paritytech/polkadot-sdk.git cd polkadot-sdk
cargo build --release -p pallet-revive-eth-rpc --bin eth-rpc ```
