FROM python:2.7.13-alpine

MAINTAINER yvarbanov

COPY requirements.txt .

RUN pip install -r requirements.txt

COPY app1.py /usr/src/app1/
COPY app2.py /usr/src/app2/

ADD supervisord.conf /etc/supervisor/supervisord.conf

CMD ["supervisord"]
