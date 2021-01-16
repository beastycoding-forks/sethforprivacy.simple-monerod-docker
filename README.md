# simple-monerod-docker
A simple and straightforward Dockerized monerod built from source and exposing standard ports.

# Docker Hub
This repo is used to build the images available at:

https://hub.docker.com/r/sethsimmons/simple-monerod

# Tags
I will always release the latest Monero version under the `latest` tag as well as the version number tag (i.e. `v0.17.1.9`).

`latest`: The latest tagged version of Monero from https://github.com/monero-project/monero/tags
`vx.xx.x.x`: The version corresponding with the tagged version from https://github.com/monero-project/monero/tags

# Recommended usage

I am using this container for my guide on running a Monero node:

https://sethsimmons.me/guides/run-a-monero-node/

The ways I would generally recommend running this container for a personal or public Monero node are below.

monerod Docker w/o public RPC:

```
sudo docker run -d --restart unless-stopped --name="monerod" -v bitmonero:/home/monero sethsimmons/simple-monerod:latest --rpc-restricted-bind-ip=0.0.0.0 --rpc-restricted-bind-port=18089 --no-igd --no-zmq --enable-dns-blocklist
```

monerod Docker w/ public RPC:
```
sudo docker run -d --restart unless-stopped --name="monerod" -v bitmonero:/home/monero sethsimmons/simple-monerod:latest  --rpc-restricted-bind-ip=0.0.0.0 --rpc-restricted-bind-port=18089 --public-node --no-igd --no-zmq --enable-dns-blocklist
```

monerod Docker w/o public RPC (pruned):
```
sudo docker run -d --restart unless-stopped --name="monerod" -v bitmonero:/home/monero sethsimmons/simple-monerod:latest  --rpc-restricted-bind-ip=0.0.0.0 --rpc-restricted-bind-port=18089 --no-igd --no-zmq --enable-dns-blocklist --prune-blockchain
```

monerod Docker w/ public RPC (pruned):
```
sudo docker run -d --restart unless-stopped --name="monerod" -v bitmonero:/home/monero sethsimmons/simple-monerod:latest  --rpc-restricted-bind-ip=0.0.0.0 --rpc-restricted-bind-port=18089 --public-node --no-igd --no-zmq --enable-dns-blocklist --prune-blockchain
```

# Shoutout
The base for the Dockerfile was pulled from:

https://github.com/leonardochaia/docker-monerod