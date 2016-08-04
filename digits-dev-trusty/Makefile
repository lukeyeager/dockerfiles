.PHONY : build run clean dockerclean bust-cache

DOCKER_ID := "digits-dev-trusty"

build:
	[ -e ".bust-cache" ] || touch .bust-cache
	docker build -t $(DOCKER_ID) .

run:
	nvidia-docker run -it --net=host \
		-p 5000:5000 \
		-p 34448:34448 \
		-v $(DOCKER_ID):/workdir \
		$(DOCKER_ID) bash

clean:
	-docker rm $(DOCKER_ID)
	-docker volume rm $(DOCKER_ID)
	docker images -q $(DOCKER_ID) | xargs -r docker rmi

dockerclean:
	docker ps -aq -f status=exited | xargs -r docker rm
	-docker images -q -f dangling=true | xargs -r docker rmi

bust-cache:
	echo `date '+%s'` >> .bust-cache
