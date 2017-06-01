FROM python:alpine

LABEL maintainer "yvarbanov"

WORKDIR /usr/src/app

COPY . .

RUN pip install -r requirements.txt

CMD ["python", "./app.py"]
