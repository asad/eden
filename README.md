# eden
dependencies: 
- [Docker](https://github.com/docker/docker) 
- up to date version of [Google Chrome](https://www.google.de/chrome/browser/desktop/) or [Mozilla Firefox](https://www.mozilla.org/de/firefox/new/)

# install linux & macOS
1. the docker image is hostet via docker.io, you can pull/run it using these commands:
2. `sudo docker run -p 80:3838 edensoftware/eden` (version with example files)
3. `sudo docker run -p 80:3838 edensoftware/eden:minimal` (minimal version)
4. open your webbrowser and point it to [localhost](localhost), you should see the welcome screen

# install eden on windows
1. see the tutorial https://docs.docker.com/docker-for-windows/ for installation and setting up docker on your windows machine
2. Press *WinKey + R*, Input `cmd` and press enter to start the *cmd.exe* to open the command promt
3. Type in the following command to download/start the docker image `sudo docker run -p 80:3838 edensoftware/eden` 
4. point your webbrowser to  [localhost](localhost), you should see the welcome screen

# install eden in the cloud
1. see https://aws.amazon.com/de/ec2/ and create an account
2. go to your dahsboard and click on *Launch Instance* and select *Ubuntu Server 14.4 LTS*
3. choose the size of of server you want to rent, *t2.micro* is maybe free for some users
4. click on *Review Instance Launch* and click on *Launch*
5. to access eden via the webbrowser, you have to allow inbound/outbound connections. For this please click on *Security Groups* and *Create Security Group*. Please add Inbound/Outbound connection: HTTP, TCP, Port 80 from everywhere, destination `0.0.0.0/0`. Go back to *EC2 Dashboard* and click on *Actions > Network > Change Security Groups* and select the securiy group you have created. 
5. create a new key pair, and download this file to your local machine
6. click *Launch and View Instance* and wait till the *Instance State* goes from *pending* to *running*
7. copy the Public DNS which looks like `ec2-54-234-172-226.compute-1.amazonaws.com
8. change the access of the local key you downloaded in step 5. `chmod 400 /path/key.pem`
9. open your terminal (e.g. bash on linux/macOS, cmd on windwos) and login to the server by typing in: `ssh -i "/path-to-key-from-step-4/key.pem" ubuntu@your-public-dns-copied-in-step-6` and type in *yes*
10. execute the command: `sudo apt-get install -y git && git clone https://github.com/naturesubmission/eden.git && cd eden && sudo chmod a+x aws-install.sh && ./aws-install.sh`
11. execute `sudo docker run -p 80:3838 edensoftware/eden`. eden is now running and can be accessed via the public IP or the public DNS e.g. at http://ec2-54-234-172-226.compute-1.amazonaws.com
12. to terminate the server go to the *EC2 dashboard* an click *Actions > Instance state > Terminate*

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

