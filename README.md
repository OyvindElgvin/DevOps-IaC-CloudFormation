# This project deploys a highly available web app using CloudFormation

Here is a diagram of the network created to set up the webpage.

![diagram](Diagram.png)

## Launch stack

### Give execute permission to files (only needed first time)

```bash
chmod +x create.sh  
chmod +x update.sh
chmod +x delete.sh
```

### Create Network

```bash
./create.sh NetworkIaC network.yml network-parameters.json
```

```bash
./update.sh NetworkIaC network.yml network-parameters.json
```

### Create Servers

```bash
./create.sh ServerStack servers.yml server-parameters.json
```

```bash
./update.sh ServerStack servers.yml server-parameters.json
```

### Delete Servers and Networks

```bash
./delete.sh ServerStack
./delete.sh NetworkIaC
```

### WebPage example

[http://serve-webap-1s7p4pezt4zbh-258404552.us-west-2.elb.amazonaws.com](http://serve-webap-1s7p4pezt4zbh-258404552.us-west-2.elb.amazonaws.com)
