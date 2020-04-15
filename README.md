# HPC

### Comandos importantes para monitorar recursos computacionais:

* Verificando arquitetura computacional
```
lscpu
```

* monitor de atividade CPU

```
htop
```

* monitor de atividade GPU

```
nvidia-smi
```

### Carregando container tensorflow

* Container com tensorflow para CPU

    * -it : inicia um terminal para acessar o Container
    * --rm : remove o container após sair do Container

```    
docker run -it --rm tensorflow/tensorflow bash
```

* Container com tensorflow para GPU

    * --runtime=nvidia : utilizar o runtime nvidia para mapear o driver nvidia para o container
```
sudo docker run -it --rm --runtime=nvidia tensorflow/tensorflow:latest-gpu bash
```

* Código para verificar presença da GPU

```
print(tf.config.list_physical_devices('GPU'))

print(('Is your GPU available for use?\n{0}').format(
    'Yes, your GPU is available: True' if tf.test.is_gpu_available() == True else 'No, your GPU is NOT available: False'
))

print(('\nYour devices that are available:\n{0}').format(
    [device.name for device in tf.config.experimental.list_physical_devices()]
))
```

* Container com tensorflow e Jupyter

    * -v ~/notebooks:/tf/notebooks : mapeia o diretório local (~/notebooks) para o diretório do container (/tf/notebooks)  
    * -p 8889:8888 : mapeia porta do container (8889) para porta do host (8888)
      
* Redirecionando porta do Container para porta do host

* Mapeando usuário do host para Container

* Configurando conteiner para executar um comando e terminar a execução

* Montando Container para treinar Modelo

* Montando Container para realizar inferencias


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
docker ps --all
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

* FROM utilize uma imagem pré-existente (criada pelo grupo que mantém o node.js)

* WORKDIR especifica que todas as ações subseqüentes devem ser executadas no diretório /usr/src/ app no sistema de arquivos do conteiner (nunca no sistema de arquivos do host).

* COPY copia o arquivo package.json do host para o local atual (.) Na sua imagem (neste caso, para /usr/src/app/package.json)

* RUN Execute o comando npm install dentro do seu sistema de arquivos de imagem (utiliza o package.json instalar dependências)

* COPY o restante do código-fonte do host para o sistema de arquivos de imagem.

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

* O conteiner é iniciado de modo asíncrono liberado o terminal
* O intervalo de portas entre 8000 e 8080 são exportadas para serem acessíveis a partir do host do conteiner

* Terminando a execução do conteiner
```
docker rm --force bb
```

* Criando uma versão nova de imagem com tag

``` 
docker image tag bulletinboard:1.0 silviostanzani/bulletinboard:2.0
```
* armazenando imagem docker no espaço público do usuário

```  
docker image push silviostanzani/bulletinboard:2.0
```

# Exercício
* criar conta no docker hub
* instalar docker
* executar imagem bulletinboard
```
docker login
docker pull silviostanzani/bulletinboard:1.9
docker run --publish 8000:8080 silviostanzani/bulletinboard:1.9
acessar o link localhost:8000 no navegador
```
