# This project deploys a highly available web app using CloudFormation

For this project, the goal is to use Infrastructure as Code, or IaC, to deploy a highly available web app through AWS CloudFormation. The IaC process uses definition files to manage and provision data centers, rather than interactive configuration tools and can therefore deploy data centers reliably in an automatic fashion.

The server stack consists of an autoscaling group providing minimum 4 EC2 instances 

Below is a diagram of the network used to set up the web app.
![diagram](Diagram.png)

## Launch stack

### Give execute permission to files (only needed the first time)

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
