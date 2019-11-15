# Build Container for my RaspberryPi 4

Contains a Dockerfile for building an docker image and its container for the _RaspberryPi 4_ using buildroot.

Implicitely will run ```git clone --branch lothar/raspberry4-devel https://github.com/Rubusch/buildroot.git``` inside the docker container.


## Build


```
$ cd ./docker__buildroot/
$ time docker build --build-arg USER=$USER -t rubuschl/raspberrypi4-buildroot:$(date +%Y%m%d%H%M%S) .
```

Use ```--no-cache``` when re-implementing the docker image.


## Usage

```
$ docker images
    REPOSITORY                      TAG                 IMAGE ID            CREATED             SIZE
    rubuschl/raspberrypi4-buildroot 20191104161353      cbf4cb380168        24 minutes ago      10.5GB
    ubuntu                          xenial              5f2bf26e3524        4 days ago          123MB

$ time docker run --rm -ti --user=$USER:$USER --workdir=/home/$USER -v $PWD/output:/home/$USER/output rubuschl/raspberrypi4-buildroot:20191104161353
```

## Debug

```
$ docker images
    REPOSITORY                      TAG                 IMAGE ID            CREATED             SIZE
    rubuschl/raspberrypi4-buildroot 20191104161353      cbf4cb380168        24 minutes ago      10.5GB
    ubuntu                          xenial              5f2bf26e3524        4 days ago          123MB

$ docker run --rm -ti --user=$USER:$USER --workdir=/home/$USER -v $PWD/output:/home/$USER/output rubuschl/raspberrypi4-buildroot:20191104161353 /bin/bash
```
