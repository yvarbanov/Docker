FROM python:2.7.13-alpine

LABEL maintainer "yvarbanov"

COPY requirements.txt .

RUN pip install -r requirements.txt

COPY app1.py /usr/src/app1/
COPY app2.py /usr/src/app2/

COPY supervisord.conf /etc/supervisor/supervisord.conf

CMD ["supervisord","-c","/etc/supervisor/supervisord.conf"]
