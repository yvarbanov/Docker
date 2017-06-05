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

# fluentd + elasticsearch + kibana

Pull

	docker pull elasticsearch:latest

	docker pull kibana:latest

Conf

	sed -i '/RUN gem/aRUN gem install fluent-plugin-elasticsearch --no-ri --no-rdoc' Dockerfile

This conf file only stores docker logs:

	mv fluent.conf old.fluent.conf && mv fluent_kibana_elasticsearch.conf fluent.conf

Build

	docker build -t fluentd:logs

Run

	docker run -d --name elastic elasticsearch:latest

	docker run -d -p 24224:24224 -p 8080:8080 --link elastic:elasticsearch --name fluent fluentd:logs

	docker run -d -p 5601:5601 --link elastic:elasticsearch --name kibana kibana:latest

Test

	docker run --rm --log-driver=fluentd --log-opt tag="docker.{{.ID}}" centos:latest echo "foo"
	docker run --rm --log-driver=fluentd --log-opt tag="docker.{{.ID}}" centos:latest echo "bar"

Kibana

	Access at: http://localhost:5601
	Index patter: fluentd-*