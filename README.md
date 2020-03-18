# Docker comandos
* docker image build -t bulletinboard:1.0 .

* docker container run --publish 8000:8080 --detach --name bb bulletinboard:1.0
  
* docker container rm --force bb
  
* docker image tag bulletinboard:1.0 silviostanzani/bulletinboard:1.0
  
* docker login
  
* docker image push silviostanzani/bulletinboard:1.0
  
* docker image push silviostanzani/bulletinboard:1.0
