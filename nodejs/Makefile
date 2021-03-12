# include ../../javascript/nodejs/docker/Makefile
couchdbPath=../docker/
nodejsPath=../../javascript/nodejs/docker/
network=couchdb-nodejs-net
path=$(shell pwd)

.PHONY: couchdb
couchdb:
ifndef arg
	cd $(couchdbPath); $(MAKE) run network=$(network)
else
	cd $(couchdbPath); $(MAKE) $(arg) network=$(network)
endif

.PHONY: nodejs
nodejs:
ifndef arg
	cd $(nodejsPath); $(MAKE) shell path=$(path) network=$(network)
else
	cd $(nodejsPath); $(MAKE) $(arg) path=$(path) network=$(network)
endif