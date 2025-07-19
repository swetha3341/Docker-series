
##Objective:

To create a simple Docker container that runs a python scripts ("Hello world")
Which demonstrates how docker works  with command-line applications.

## Configrations 

1. Created a repo on github Docker-series

2. Cloned the repo 

```
https://github.com/swetha3341/Docker-series.git
```

3. Installing docker

```
sudo apt update
sudo apt install docker.io -y
```

4.Verify if docker has installed.

```
docker run hello-world
```

This outputs an error saying permission denied for 2 reasons.

1. docker deamon not running
   
3. user doesnt have access to run the docker commands.

Hence perform he below steps to resolve the issue.

5. Check the status of  the Daemon process ,If not running then start it.
   
```
sudo systemctl status docker
``` 
6. Add the user ubutu to group docker
   
Docker daemon (dockerd) runs as root.

We add users to the docker group to let them use Docker without sudo.
⚠️ This gives root-like access — it's a security risk.

```
sudo usermod -aG docker ubuntu
```

🧠 Adding a user to the Docker group lets them access the Docker socket (/var/run/docker.sock), which has root privileges.

7. Write the DockerFile
   
This builds a container that runs the python-app

🧠 What does "Separating install and runtime steps in a Dockerfile" mean?

It means you clearly separate the steps where you install things (like Python or libraries) from the steps where you run your app. This improves:

✅ Readability – Easier to understand what's being installed and what's being run.
⚡ Build caching – Docker reuses cached layers, so your image builds faster.
🔒 Security & stability – Installations are done only once; runtime is clean and stable.

8. app.py
   
A simple python script that prints "Hello World"

10. Build Docker Image

```
docker build -t swetha/first-docker-image:latest .
```

10. To check the Docker Image created.

```
docker images
```

11. Run your First Docker Container

```
docker run -it swetha/first-docker-image
```
Output:

```
Hello world
```
12. Push the Docker Image to docker Hub (registry)

```
docker push swetha/first-docker-image  
``` 


## SUMMARY

"I containerized a simple command-line Python app using Docker. I used an Ubuntu base image, copied the app script, installed Python and pip using RUN, and started the script using CMD. The app simply prints 'Hello World' to show that the container setup works correctly."


