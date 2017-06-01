FROM alpine:3.6

LABEL maintainer "yvarbanov"

RUN apk add --no-cache py-pip

WORKDIR /usr/src/app

COPY test.py .
COPY requirements.txt .

RUN pip install -r requirements.txt

COPY supervisord.conf /etc/supervisor/

CMD ["/usr/bin/supervisord"]
