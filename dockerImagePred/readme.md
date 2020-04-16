Conteúdo Dockerfile

```
FROM tensorflow/tensorflow:latest-gpu

COPY classifier.pkl .
COPY pred.py .

RUN apt install -y python3-pip
RUN pip3 install pandas
RUN pip3 install scikit-learn

ENTRYPOINT ["python3","pred.py"]
```

montando imagem

```
sudo docker build --tag silviostanzani/tensorflow:pred .
```

rodando imagem
```
sudo docker run -it --rm --runtime=nvidia silviostanzani/tensorflow:pred bash
```
