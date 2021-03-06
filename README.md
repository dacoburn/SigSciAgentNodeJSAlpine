## Signal Sciences Docker Configuration - Alpine NodeJS

This is a dockerized agent with the SigSci NodeJS Module and a simple NodeJS app. T You can use a pre-built container or build your own. When building and deploying I tend to use the agent version followed by the SigSci module version for the tag.

## Information about the files


**start.sh**
The start.sh is a simple script for doing some customizations. I use it to start the apache service and then set a custom hostname that the Signal Sciences agent will report up. I like to include a hard coded value, I.E. MYKUBECLUSTERNAME, followed by the dynamically found hostname. On Docker, or Kuberneted, the hostname is the docker id. Between those two things it makes it very easy to figure out where the container is running in relation to the agent found in the Signal Sciences dashboard.

**contrib**
I'll usually create a .dockerignore file that will ignore adding the contrib to the final docker container and put files that I would like to copy into the container in this folder.

**Dockerfile**
The included dockerfile is my example for creating a container that has Apache2, with the SignalSciences Module enabled, and our Signal Sciences Agent.

**Makefile**
I tend to prefer nice easy command for doing my tasks in building, deploying, and testing locally. The makefile simplifies this process but is not neccessary.

## Running the container

make run DOCKERUSER=YOURDOCUERUSER DOCKERNAME=sigsci-alpine-nodejs DOCKERTAG=1.18.2-1.4.4 SIGSCI_ACCESSKEYIS=*ACCESSKEY* SIGSCI_SECRETKEYID=*SECRETKEY*

## Building Docker image

You can use the Makefile to build the Docker Container
Make Example:

make build DOCKERUSER=YOURDOCUERUSER DOCKERNAME=sigsci-alpine-nodejs DOCKERTAG=1.18.2-1.4.4


###Deploying to Docker

You can also use the Makefile to deploy the created container to Docker Hub

make deploy DOCKERUSER=*USERNAME* DOCKERNAME=sigsci-alpine-nodejs  DOCKERTAG=1.18.2-1.4.4
