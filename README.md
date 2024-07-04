# NetflixOps

![NetflixOps System Design](assets/NetflixOps.png)


## Overview


## Tools/Plugins used
- Jenkins: for creating pipelines
- Prometheus and Grafana for monitoring
- SonarQube
- Owasp
- Trivy scan

## Details steps

### Overview
- To get started create a ec2 instance.
- Preferably you need two instances a t2.large and a t2.micro one for monitoring and the other one for the whole pipeline.
- So in total we have 3 servers:
    - The server on which app is deployed
    - Monitoring server
    - Pipelines server
- For the app i'll be using a Netflix clone [Netflix Clone](https://github.com/gsbarure/netflix-clone-react-typescript) 
>**> [!IMPORTANT]
> Make sure you use vpn while using the api or the app as for some reason TMDB doesnt work in India.


### Run the docker-compose.yml using

```sh 
docker-compose up
```

The docker-compose file has 5 containers

 ✔ Container node-exporter         
 ✔ Container localstack  
 ✔ Container grafana     
 ✔ Container jenkins      
 ✔ Container trivy    

>**Note**: Learn more about docker-compose here: [docker-compose](https://docs.docker.com/compose/)

- Now you'll see 5 services running on your system.

## Lets configure the prometheus.yml file

- This will contain the config for prometheus monitoring basically all the plugins and the dependencies for prometheus.

