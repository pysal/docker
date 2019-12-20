# Base docker image for PySAL development

This serves as the base image for common build, testing, and documentation of packages in the [PySAL ecosystem](http://pysal.org).



## Using the image for PySAL development

```
git clone git@github.com:pysal/pysal.git  # (Or, clone your fork)
cd pysal
docker run -it --rm   -v ${PWD}:/home/jovyan sjsrey/pysaldev:2.3 sh -c "python setup.py develop && /bin/bash"
```

This will mount the host current working directory at the home directory of the container. You can use host tooling (editor) to work on the source code. Any changes made during a container run will be preserved on the host.

If your development requires using jupyter notebooks/lab then your workflow would be:

```
git clone git@github.com:pysal/pysal.git # (Or, clone your fork)
cd pysal
docker run -it --rm  -p 8888:8888 -v ${PWD}:/home/jovyan sjsrey/pysaldev:2.3 sh -c "python setup.py && /bin/bash"
```

At the shell in the container enter: `jupyter notebook` From the shell copy the url with the token and paste into a browser on the host. The url should look something like ` http://127.0.0.1:8888/?token=f1e8a4cf0487a8bc728b12f530c30a7d52449632d662c4ee`


## Building the image

`docker build -t sjsrey/pysaldev .`

### Push the built image to docker hub to share with others

```
docker tag sjsrey/pysaldev sjsrey/pysaldev:X.X.X (where X.X.X is the version)
docker login
docker push sjsrey/pysaldev
```

### Stop/delete all local docker containers/images

```
docker stop $(docker -ps -aq)
docker rm $(docker -ps -aq)
docker rmi $(docker images -q) --force

```
