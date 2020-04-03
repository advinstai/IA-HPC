# Docker

## Testando instalação do docker

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

## Listando conteineres presentes no computador

```
docker image ls
```

## Mostrando conteineres que foram iniciadas nesse computador

```
sudo docker ps --all
```

## Montando um conteiner docker 

Um container é montado com base em um arquivo chamado dockerfile. A seguir replicamos uma fragmento do tutorial docker (https://docs.docker.com/get-started/part2/) passo a passo.

* Um conteiner é definido com base em uma imagem vazia, ou a partir de uma imagem existente
* A forma mais eficiente de manter um dockerfile é versionando no github
* O primeiro passo para criar um novo conteiner docker é obtendo a descrição e os arquivos necessários para criar o conteiner

```
git clone https://github.com/dockersamples/node-bulletin-board
cd node-bulletin-board/bulletin-board-app
```

* Conteúdo do dockerfile descritor da imagem

```
FROM node:current-slim

WORKDIR /usr/src/app
COPY package.json .
RUN npm install

EXPOSE 8080
CMD [ "npm", "start" ]

COPY . .
```

* Montando um conteiner a partir da descrição
```
docker build --tag bulletinboard:1.0 .
```

* Iniciando o conteiner
```
docker run --publish 8000:8080 --detach --name bb bulletinboard:1.0
```


## 
# Docker comandos
* docker image build -t bulletinboard:1.0 .

* docker container run --publish 8000:8080 --detach --name bb bulletinboard:1.0
  
* docker container rm --force bb
  
* docker image tag bulletinboard:1.0 silviostanzani/bulletinboard:1.0
  
* docker login
  
* docker image push silviostanzani/bulletinboard:1.0
  
* docker image push silviostanzani/bulletinboard:1.0

Fonte: https://docs.docker.com/get-started/part2/
