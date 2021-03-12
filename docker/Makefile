SHELL=/bin/bash

name = couchdb
ports = 5984:5984
volume = couchdbVolume
user = admin
password = RuahMan773!

ifndef network
	network=$(name)-net
endif

.PHONY: build
build:
	@if [[ "$(shell docker images -q $(name) 2> /dev/null)" == "" ]]; then \
		docker build -t $(name) .; \
	else \
		echo "image: $(name) is already setup"; \
	fi

.PHONY: network
network:
	@if [[ "$(shell docker network inspect $(network) 2> /dev/null)" == "[]" ]]; then \
		docker network create $(network); \
	else \
		echo "network: $(network) is already setup"; \
	fi

.PHONY: run
run: build network 
	docker container run --name $(name) --network=$(network) -v $(volume):/opt/couchdb/data -p $(ports) -e COUCHDB_USER=$(user) -e COUCHDB_PASSWORD=$(password) -d $(name)

.PHONY: shell
shell:  
	@echo shell

.PHONY: stop
stop:
	docker container stop $(name)

.PHONY: start
start:
	docker container start $(name)

.PHONY: rm
rm:
	docker container rm $(name)

.PHONY: rmi
rmi:
	docker rmi $(name)

.PHONY: rmv
rmv:
	docker volume rm $(volume)

