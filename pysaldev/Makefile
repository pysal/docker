# Linux specific Docker file for pysaldev
#
VERSION = 2.3
REPO = sjsrey
container:
	docker build -t $(REPO)/pysaldev:$(VERSION) .

# run a shell for our env
cli:
	docker run -it -p 8888:8888 -v ${PWD}:/home/jovyan $(REPO)/pysaldev:$(VERSION) /bin/bash

test:
	docker run -it  -v ${PWD}:/home/jovyan $(REPO)/pysaldev:$(VERSION)  pytest
