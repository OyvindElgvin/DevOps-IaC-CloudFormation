# Deploying a highly available web application using CloudFormation

For this project, the goal is to use Infrastructure as Code, or IaC, to deploy a highly available web application through AWS CloudFormation. The IaC process uses definition files to manage and provision data centers, rather than interactive configuration tools and can therefore deploy data centers reliably in an automatic fashion.

As seen in the diagram below the server stack consists of an autoscaling group in private subnets providing a minimum of two EC2 instances in two different Availability Zones to ensure high availability for the web application.

![diagram](Diagram.png)

The server stack spin up EC2 instances ready-made with Ubuntu installed and uses the commands below to install awscli and apache2. After the installation of the dependencies, a zip file containing the HTML for the web application is copied from a Udacity managed s3 bucket and into the EC2 instances.

```bash
#!/bin/bash
apt-get update -y
apt-get install unzip awscli -y
apt-get install apache2 -y
systemctl start apache2.service
cd /var/www/html
aws s3 cp s3://udacity-demo-1/udacity.zip .
unzip -o udacity.zip
```

## Launch stack

### Give execute permission to files (only needed the first time)

```bash
chmod +x create.sh  
chmod +x update.sh
chmod +x delete.sh
```

### Create and Update Network

```bash
./create.sh NetworkIaC network.yml network-parameters.json
```

```bash
./update.sh NetworkIaC network.yml network-parameters.json
```

### Create and Update Servers

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

### Web application test example

[http://serve-webap-1s7p4pezt4zbh-258404552.us-west-2.elb.amazonaws.com](http://serve-webap-1s7p4pezt4zbh-258404552.us-west-2.elb.amazonaws.com)
