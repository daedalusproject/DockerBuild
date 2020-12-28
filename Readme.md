# Docker build


[![pipeline status](https://git.windmaker.net/a-castellano/DockerBuild/badges/master/pipeline.svg)](https://git.windmaker.net/a-castellano/DockerBuild/commits/master)[![coverage report](https://git.windmaker.net/a-castellano/DockerBuild/badges/master/coverage.svg)](https://git.windmaker.net/a-castellano/DockerBuild/commits/master)

An originary [Daedalus Project](https://github.com/daedalusproject) utility which allows users to create Docker images during CI/CD jobs.

This tool is curently used for creating all Docker images from [Limani](https://git.windmaker.net/a-castellano/limani) project. Images were only allowed to be uploaded to [Docker Hub](https://hub.docker.com/) but other registry URL's can be used.

## Installation

### From source

Just follow these instructions:
```bash
git clone https://git.windmaker.net/a-castellano/DockerBuild.git && cd DockerBuild
make build
sudo make install
```

### Using Repos

Add packages.windmaker.net repo:
```bash
apt-get install -y gnupg ca-certificates wget
wget -O - http://packages.windmaker.net/WINDMAKER-GPG-KEY.pub | sudo apt-key add - 
apt-get update
apt-get install docker-build
```

## Usage

This tool uses environment variables in order to obtain registry name, credential, image names, etc.

The following environment variables must be set in order to make this tool work:

* **DOCKER_REGISTRY_USER** - specifies registry user.
* **DOCKER_REGISTRY_PASSWORD** - specifies registry user password.
* **DOCKER_IMAGES_MAINTAINER** - specifies Image maintainer name. 
* **IMAGE_NAME** - specifies the name of the image that this toll is creating. 
* **IS_BASE_IMAGE** - specifies is the image we want to create is a base image (see below)

**docker-build** will look for a folder named as **IMAGE_NAME** value containing a valid Dockerfile.
```bash
export DOCKER_ORGANIZATION_NAME="acastellano"
export DOCKER_IMAGES_MAINTAINER="Álvaro Castellano Vela <alvaro.castellano.vela@gmail.com>"
export DOCKER_REGISTRY_USER="acastellano"
export DOCKER_REGISTRY_PASSWORD="my_dockerhub_password"
export IMAGE_NAME="test"
export IS_BASE_IMAGE=1

```

