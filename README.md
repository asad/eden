# eden

# install eden
dependencies: [Docker](https://github.com/docker/docker) 

the docker image is hostet via docker.io, you can pull/run it using these commands:

`sudo docker run -p 80:3838 edensoftware/eden` (version with example files)

`sudo docker run -p 80:3838 edensoftware/eden:minimal` (minimal version)

open your webbrowser and point it to [localhost](localhost)

# submit a new job
![submit a new job](start.gif "submit a new job")

# visualize results
![visualize results](samples.gif "visualize results")

# build your own docker image

you can create the docker image from scratch:

```
git clone https://github.com/naturesubmission/eden.git
cd eden
sudo docker build eden_local .
sudo docker run -p 80:3838 eden_local
# point browser to localhost
```

