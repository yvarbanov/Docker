# docker-fluentd

Build

	docker build -t fluentd:logs .

Run

	docker run -d -p 24224:24224 -p 9880:9880 --name fluent fluentd:logs

Test Docker logging

	docker run --rm --log-driver=fluentd --log-opt tag="docker.{{.ID}}" centos:latest echo "hello world"

Test http logging

	curl -X POST -d 'json={"json":"hello world"}' http://localhost:9880/hello.world

Check logs

	docker logs fluent
