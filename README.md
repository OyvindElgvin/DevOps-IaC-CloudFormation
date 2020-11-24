# Launch stack

## Give execute permission to file

chmod +x create.sh
chmod +x update.sh

## Create NETWORK

```./create.sh NetworkIaC network.yml network-parameters.json```

```./update.sh NetworkIaC network.yml network-parameters.json```

## Create SERVER STACK

```./create.sh ServerStack servers.yml server-parameters.json```

```./update.sh ServerStack servers.yml server-parameters.json```
