# sclerotinia-366-dependencies

A dockerfile to set up all the software dependencies necessary to run Kamvar et al. 2017.

Note that this container does not contain any of the code or data from Kamvar et al. 2017,
it is simply the computational environment for the code. The code and data can be found
at https://github.com/everhartlab/sclerotinia-366 or on the Open Science Framework at
https://osf.io/ejb5y/ (github is easier to browse, but the OSF project is more permanent).
All versions of the container are synced on Docker hub: 
https://hub.docker.com/r/everhartlab/sclerotinia-366-dependencies/


## Running the container

The image can be run via the command line. Docker will automatically install the image
for you. 

```
docker run --rm --name ssc-dep -dp 8787:8787 -e ROOT=TRUE everhartlab/sclerotinia-366-dependencies:latest
```

After that finishes, you can open your browser to `localhost:8787` and log in with

 - Username: rstudio
 - Password: rstudio

When you are finished, you can stop the container with:

```
docker stop ssc-dep
```

### Running the analyses

Kamvar et al. is rebuilt whenever something changes in the code. You can run the
container that contains all the code and data like so:

```
docker run --rm --name ssc -dp 8787:8787 -e ROOT=TRUE everhartlab/sclerotinia-366
```

After you open Rstudio server, you should open the Terminal tab and use 
`cp -R /analysis .` to copy the code and data to the current working directory.

-----

If you want to use it to rebuild Kamvar et al. 2017 from scratch , you can do the following:

```
git clone https://github.com/everhartlab/sclerotinia-366.git
cd sclerotinia-366
docker run --rm --name ssc-dep -dp 8787:8787 -v $(pwd):/home/rstudio/ -e ROOT=TRUE everhartlab/sclerotinia-366-dependencies
```

