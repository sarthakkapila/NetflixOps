# NetflixOps

![NetflixOps System Design](assets/NetflixOps.drawio.png)


## Overview
This repo contains the code & steps followed to deploy a Netflix clone app using Jenkins CI-CD, Docker container with Kubernetes Cluster along with the monitoring of metric using Grafana, Prometheus & Node Exporter.

## Details steps

### Launching a T2 instance
- Choose any t2 instance 
For the project I am going to use https://www.localstack.cloud/ which is used to test AWS apps locally.

- Follow the follwing steps for localstack
```
brew install localstack/tap/localstack-cli
```

Verifiy installation
```
localstack --version
```
-- 3.5.0

#### Using Docker to start LocalStack ec2 instance using docker-compose.yml in /docker  
```
docker-compose up
```
- LocalStack Endpoint 
```
aws --endpoint-url=http://localhost:4566 ec2 run-instances \
    --profile localstack \
    --image-id <ami-id-of-t2> \   #ami-df5de72bdb3b for ubuntu 22.04
    --instance-type t2.micro \
    --tag-specifications 'ResourceType=instance,Tags=[{Key=Name,Value=MyInstance}]'
```
- Access Logs
```
localstack logs
```
#### MISC
- Describe instance
```
aws --endpoint-url=http://localhost:4566 ec2 describe-instances --profile localstack
```
- Stop Instance
```
aws --endpoint-url=http://localhost:4566 ec2 stop-instances --instance-ids <Instance-id> --profile localstack
```
- Start Instance 
```

aws --endpoint-url=http://localhost:4566 ec2 start-instances --instance-ids <Instance-id> --profile localstack
```
