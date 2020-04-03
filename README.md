# Docker

## Testando instalação docker
```
docker run hello-world
```

Retorno:

```
Hello from Docker!
This message shows that your installation appears to be working correctly.

To generate this message, Docker took the following steps:
 1. The Docker client contacted the Docker daemon.
 2. The Docker daemon pulled the "hello-world" image from the Docker Hub.
    (amd64)
 3. The Docker daemon created a new container from that image which runs the
    executable that produces the output you are currently reading.
 4. The Docker daemon streamed that output to the Docker client, which sent it
    to your terminal.

To try something more ambitious, you can run an Ubuntu container with:
 $ docker run -it ubuntu bash

Share images, automate workflows, and more with a free Docker ID:
 https://hub.docker.com/

For more examples and ideas, visit:
 https://docs.docker.com/get-started/
```


## Docker montando um conteiner a partir de uma imagem de base

* A criação de uma imagem docker é feita por meio de um arquivo chamado dockerfile

* A seguir mostramos um exemplo de como criar um conteiner a partir de uma imagem com tensorflow 

```
mkdir ˜/dockerimage
```

# Docker comandos
* docker image build -t bulletinboard:1.0 .

* docker container run --publish 8000:8080 --detach --name bb bulletinboard:1.0
  
* docker container rm --force bb
  
* docker image tag bulletinboard:1.0 silviostanzani/bulletinboard:1.0
  
* docker login
  
* docker image push silviostanzani/bulletinboard:1.0
  
* docker image push silviostanzani/bulletinboard:1.0


