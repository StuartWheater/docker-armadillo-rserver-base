no_cache=true
name=datashield/docker-armadillo-rerver-base
tag=test

all:
	sudo docker build --no-cache=$(no_cache) -t="${name}:$(tag)" .
	sudo docker image push ${name}:$(tag)
