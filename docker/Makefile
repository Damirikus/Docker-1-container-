build: 
	docker build -t deb .

all: 
	docker run -it -p 443:443 deb

clean: 
	docker container prune
	docker image prune
	docker image rm deb
