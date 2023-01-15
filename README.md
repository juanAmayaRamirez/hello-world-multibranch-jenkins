# Jenkins cicd aws pipeline

## initial setup
### requirements:
Install docker desktop  
* windows: https://docs.docker.com/desktop/install/windows-install/   
* linux: https://docs.docker.com/desktop/install/linux-install/  
* mac: https://docs.docker.com/desktop/install/mac-install/
### step by step
1. with docker installed go to https://hub.docker.com/ and search for jenkins/jenkins image
2. there is a command to download the image you desire, for the latest just run  
`$ docker pull jenkins/jenkins`
3. now we will run the dokcer container with the downloaded image, expose ports 8080, 50000 and mount a persistant volume jenkins_home with the following command  
`$ docker run -d --name jenkins -p 8080:8080 -p 50000:50000 -v jenkins_home:/var/jenkins_home jenkins/jenkins`
4. verify the container just created  
`$ docker ps -l`
5. go to local host 8080 and see the path where jenkins stored the password
6. with docker exec read the password for example with a cat  
`$ docker exec jenkins cat /var/jenkins_home/secrets/initialAdminPassword`
7. after entering the password, if this is the first time using jenkins, just install the recommended plugins but if you know what you are doing, select the plugins you need, create the admin user and thats it.
8. now that we have the container up and running, we can remove ir with `$ docker rm -f` to terminate it whenever we want and the configuration will not be los since we assigned a volume. 
### Docker compose
Docker Compose is a tool that helps you to run multiple containers as a single service. It allows you to define all the containers and the connections between them in a single file, and then start, stop, and manage all of them with a single command. It makes it easy to set up and manage complex applications. Think of it as a way to organize and run multiple docker containers together seamlessly.

Instalation  
linux: https://www.digitalocean.com/community/tutorials/how-to-install-and-use-docker-compose-on-ubuntu-20-04  