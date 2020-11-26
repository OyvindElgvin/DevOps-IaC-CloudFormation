# This project deploys a highly available web app using CloudFormation




## Launch stack

### Give execute permission to files (only needed first time)

```
chmod +x create.sh  
chmod +x update.sh
chmod +x delete.sh
```

### Create Network

```
./create.sh NetworkIaC network.yml network-parameters.json
```

```
./update.sh NetworkIaC network.yml network-parameters.json
```

### Create Servers

```
./create.sh ServerStack servers.yml server-parameters.json
```

```
./update.sh ServerStack servers.yml server-parameters.json
```

### Delete Servers and Networks

```
./delete.sh ServerStack
./delete.sh NetworkIaC
```