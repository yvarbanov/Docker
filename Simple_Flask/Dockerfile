FROM python:slim

MAINTAINER yvarbanov

RUN pip install -U Flask

WORKDIR /usr/src/app

COPY app.py .

CMD ["python", "./app.py"]