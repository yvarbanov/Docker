FROM python:alpine

LABEL maintainer "yvarbanov"

WORKDIR /usr/src/app

COPY app.py app.py
COPY requirements.txt requirements.txt

RUN pip install -r requirements.txt

CMD ["python", "./app.py"]
