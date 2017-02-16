## Build oet-core docker image

In your project directory, create a file named Dockerfile and paste the following:

```
FROM nginx
COPY dist /usr/share/nginx/html/
COPY node_modules /usr/share/nginx/html/node_modules
```

This tells Docker to:

- Build an image starting with the nginx image
- Copy dist directory into the path /usr/share/nginx/html in the image
- Copy node_modules directory into the path /usr/share/nginx/node_modules in the image

Then build an image

``` docker build -t NAME .```

Run it

```docker run -ti NAME bash```

Login to https://hub.docker.com/

```docker login```

Push image to Docker Hub 

``` docker push NAME[:TAG]```


## Run teamcity agent 

```docker-compose -f teamcity-agent/compose.yaml up```

## Run teamcity server and agent

```docker-compose -f teamcity/compose.yaml up```

This Compose file defines two services: tcserver and tcagent
https://blog.jetbrains.com/teamcity/2016/06/teamcity-on-docker-hub-its-official-now/

Add new agents easily 

```docker-compose scale tcagent=3```

## Run jenkins

Run command 

```docker-compose -f jenkins/compose.yaml up```

Jenkins service:

- Uses an image that’s built from the Dockerfile in the jenkins_docker_dir directory (Maven installation on top of jenkins image).
- Forwards the exposed ports 8080 and 50000 on the container to ports 8080 and 50000 on the host machine(local or AC2).
- Mounts directory jenkins_data on the host to /var/jenkins_homee inside the container, allowing to store settings and build results on host machine.

