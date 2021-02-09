# Upgrade Procedure

**Note**: It is assumed you are currently operating a full-node running v0.8.2 version of Akash.

1. Verify you are currently running the correct version of Akash 
```
akashd version --long
name: akash
server_name: akashd
client_name: akashctl
version: 0.8.2
commit: 107f71bcd2804196b9f3194f3528b4b66a662e06
build_tags: netgo,ledger,mainnet
go: go version go1.15.5 linux/amd64
```

2. Export existing state from akashnet-1:
**Note**: It is recommended for validators and operators to take a full data snapshot at the export height before proceeding in case the upgrade does not go as planned or if not enough voting power comes online in a sufficient and agreed upon amount of time. In such a case, the chain will fallback to continue operating akashnet-1.

Before exporting state via the following command, the akashd binary must be stopped.

`$ akashd export --for-zero-height --height=<TBD> > akashnet_1_genesis_export.json`

3. Verify the SHA256 of the (sorted) exported genesis file:
```
$ jq -S -c -M '' akashnet_1_genesis_export.json | shasum -a 256
```

4. Build v0.9.3 of Akash
```
$ git clone https://github.com/ovrclk/akash.git && cd akash
$ git checkout v0.9.3 && make install
```

5. Verify you have the correct version:
```
akash version --long
name: akash
server_name: akash
version: 0.9.3
commit: 96a037eb9e717a090516bc0d391e2fcb54655bba
build_tags: netgo,ledger
go: go version go1.15.5 linux/amd64
build_deps:
- github.com/99designs/keyring@v1.1.6
- github.com/ChainSafe/go-schnorrkel@v0.0.0-20200405005733-88cbf1b4c40d
- github.com/Workiva/go-datastructures@v1.0.52
....
```

6.  Migrate exported state from the current v0.8.2 version to the new v0.9.3 version:
```
$ akash migrate v0.41 akashnet_1_genesis_export.json --chain-id=akashnet-2 > migrated_genesis.json
```

7. Adding IBC parameters to the genesis file:
```
cat migrated_genesis.json | jq '.app_state |= . + {"ibc":{"client_genesis":{"clients":[],"clients_consensus":[],"create_localhost":false},"connection_genesis":{"connections":[],"client_connection_paths":[]},"channel_genesis":{"channels":[],"acknowledgements":[],"commitments":[],"receipts":[],"send_sequences":[],"recv_sequences":[],"ack_sequences":[]}},"transfer":{"port_id":"transfer","denom_traces":[],"params":{"send_enabled":false,"receive_enabled":false}},"capability":{"index":"1","owners":[]}}' > genesis.json
```
8. Verify the SHA256 of the final genesis JSON:
```
$ jq -S -c -M '' genesis.json | shasum -a 256
```
9. Creating a new home directory for `akash`
```
$ akash init <moniker> --chain-id akashnet-2
```
10. Copying the node and priv_val_key and new genesis to the new home directory
```
$ cp .akashd/config/node_key.json .akash/config/node_key.json
$ cp .akashd/config/priv_validator_key.json .akash/config/priv_validator_key.json
$ cp ~/genesis.json .akash/config/genesis.json
```


