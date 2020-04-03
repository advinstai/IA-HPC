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

## Introdução a NN
https://raphaelmcobe.github.io/dataSanJose2019_nn_presentation/#/

## TensorFlow
https://www.datacamp.com/community/tutorials/tensorflow-tutorial
https://mlfromscratch.com/tensorflow-2/#/
