Conteúdo Dockerfile:

```
FROM tensorflow/tensorflow:latest-gpu

COPY train.py .

RUN apt install -y python3-pip
RUN pip3 install pandas
RUN pip3 install scikit-learn

ENTRYPOINT ["python3","train.py"]
```

Criar imagem:

```
sudo docker build --tag silviostanzani/tensorflow:train .
```

rodar imagem:
```
sudo docker run -v /home/silvio/git:/tf -it --rm --runtime=nvidia silviostanzani/tensorflow:train
```
