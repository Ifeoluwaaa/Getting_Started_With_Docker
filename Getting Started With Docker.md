## GETTING STARTED WITH DOCKER

> Commands will be ran on a  web Docker CLI

![Docker_cli](./Getting%20started%20with%20Docker.jpg/DockerCLI.png)

![New_Instance](./Getting%20started%20with%20Docker.jpg/New_Instance.png)

> To check for docker information

    docker
    docker version
    docker --version
    docker info
    docker help
       
![Docker_info](./Getting%20started%20with%20Docker.jpg/Docker_info.png)
![Docker_info](./Getting%20started%20with%20Docker.jpg/Docker_info.2.png)

> To display the docker management commmand container and help of the run command 

    docker container help
    docker container run --help
![docker_help](./Getting%20started%20with%20Docker.jpg/Docker_help.png)
![docker_help](./Getting%20started%20with%20Docker.jpg/Docker_help.2.png)

> Using docker cli search on the Docker Hub for an image called mariadb

    docker image pull mariadb
![dockerimage](./Getting%20started%20with%20Docker.jpg/dockerimage.png)

> Using docker client pull image called alpine with the edge tag

Tags on docker are versions of the image
> List all images downloaded locally

    docker image pull alpine:edge
    docker image ls
![imagepull](./Getting%20started%20with%20Docker.jpg/Imagepull.png)

> Launch a container from the alpine:edge image, get shell access to the container

    docker container run -it alpine:edge sh
> create a new file called a.txt in the root directory of the container 

    cd /root
    touch a.txt
> exit the container without stopping it

    ctrl p+q
> check that the container is still running

    docker container ls -a
![dockercontainer](./Getting%20started%20with%20Docker.jpg/dockerrunit.png)

> Get shell access to the container and check the file a.txt still exists then exit the container 

    docker container exec -it 27ee sh
    cd /root
    ls -l
    exit
![exist](./Getting%20started%20with%20Docker.jpg/exists.png)    

> Run the Nginx web server in Docker container, in the background, and publish port 80

    docker container run -d -p 8080:80 --name mysite nginx
    docker container run -d -p 8080:80 --name mysite.corect nginx
![nginx](./Getting%20started%20with%20Docker.jpg/nginx.png)
![nginx.2](./Getting%20started%20with%20Docker.jpg/nginxls.2.png)
> connect to the server from another machine using a browser

    ip address
    paste ip address on browser
![ip](./Getting%20started%20with%20Docker.jpg/ipaddress.png)
![browser](./Getting%20started%20with%20Docker.jpg/NGINX%20site.png)

> this is a public docker cli so using nginx on browser is a little different

![docker](./Getting%20started%20with%20Docker.jpg/sshport.png)

> click on the ports on the top right of the page

![.80nginx](./Getting%20started%20with%20Docker.jpg/80browser.png)
![8080nginx](./Getting%20started%20with%20Docker.jpg/8080browser.png)

> check the web server logs 

    docker container logs a4e
![logs](./Getting%20started%20with%20Docker.jpg/logs.png)

> Attach to the container in which nginx is running

    docker container exec -it 14e5ad bash
![bash](./Getting%20started%20with%20Docker.jpg/bash.png)

> Run two nginx and two apache containers that publish random ports

    docker container run -d -P --name apache1 httpd
    docker container run -d -P --name apache1 httpd
    docker container run -d -P --name nginx1 nginx
    docker container run -d -P --name nginx2 nginx
![webservers](./Getting%20started%20with%20Docker.jpg/webservers.png)
![confirmservers](./Getting%20started%20with%20Docker.jpg/confirmwebservers.png)

> Connect to web servers using a browser

![browser](./Getting%20started%20with%20Docker.jpg/apachebrowser.png)
![browser](./Getting%20started%20with%20Docker.jpg/nginxbrowser.png)

> Stop and remove all containers 

    docker container stop (containers id)
    docker container rm $(docker container ls -a -f status=exited -q)
![stop](./Getting%20started%20with%20Docker.jpg/stopcontainer.png)
![containers](./Getting%20started%20with%20Docker.jpg/lsexit.png)
![removecontainers](./Getting%20started%20with%20Docker.jpg/remove.png)
![remove](./Getting%20started%20with%20Docker.jpg/confirmrm.png)

> Run ubuntu:latest in a container and get shell access

    docker container run -it ubuntu:latest sh

> Install the OpenSSH server in the container


    apt update && apt install ssh
![update](./Getting%20started%20with%20Docker.jpg/aptupdate.png)


> Confirm the ssh is running

    service ssh start
    service ssh status
![ssh](./Getting%20started%20with%20Docker.jpg/sshconfirm.png)

> Add a user and set its password

    useradd ifeoluwa
    passwd ifeoluwa
![user](./Getting%20started%20with%20Docker.jpg/newuser.png)

> Exit the container without stopping it

![ubuntu](./Getting%20started%20with%20Docker.jpg/newcontainer.png)

> Check the IP address of the container and connect to it using SSH and the user

![ipaddress](./Getting%20started%20with%20Docker.jpg/newipaddress.png)

    ssh -l ifeoluwa 172.17.0.2

![sshlogin](./Getting%20started%20with%20Docker.jpg/sshlogin.png)

> Consider the previous challenge when you've installed the openssh server in a ubuntu docker container

    service status ssh
![ssh](./Getting%20started%20with%20Docker.jpg/sshstatus.png)

![exit](./Getting%20started%20with%20Docker.jpg/exit.png)

> Commit the changes to a new image named myubuntu with the tag custom

    docker commit -m "OpenSSH installed" -a "ifeoluwa" 77c7 ifeoluwa2/myubuntu:custom

    docker image ls
![commmit](./Getting%20started%20with%20Docker.jpg/newubuntu.png)

> start a container from this new image and check that the ssh daemon is installed and is running 

    docker container run -it ifeoluwa2/myubuntu:custom
    service ssh status
    service ssh start
![newcontainer](./Getting%20started%20with%20Docker.jpg/newcontainer.png)

> Push the image to Docker Hub

    docker login
![login](./Getting%20started%20with%20Docker.jpg/dockerlogin.png)

    docker image push ifeoluwa2/myubuntu:custom
![docker](./Getting%20started%20with%20Docker.jpg/hubcommit.png)
![dockerhub](./Getting%20started%20with%20Docker.jpg/dockerhub.png)

> On Docker Hub search for Apache

![dockerhub](./Getting%20started%20with%20Docker.jpg/DockerHub2.png)
![apachehub](./Getting%20started%20with%20Docker.jpg/Apachehub.png)

> Go to the Dockerfile of the image with the latest tag

![apachefile](./Getting%20started%20with%20Docker.jpg/dockerfileshot.png)

![latest:tag](./Getting%20started%20with%20Docker.jpg/Latesttag.png)

> Copy the Dockerfile locally and build custom image from that file

![copying](./Getting%20started%20with%20Docker.jpg/copyfile.png)

    vim Dockerfile
![vim](./Getting%20started%20with%20Docker.jpg/pasteonvim.png)

![view](./Getting%20started%20with%20Docker.jpg/cat.png)

> Download httpd-foreground

![wget](./Getting%20started%20with%20Docker.jpg/wget.png)

> Set the execution permission before building the image

    chmod +x httpd-foreground

> Build custom image from that file

    docker image build -t myapache:1.0 .
![custom_image](./Getting%20started%20with%20Docker.jpg/buildimage.png)

> Start a container from the image and test that it works

    docker container run -d -P myapache:1.0
![new_container](./Getting%20started%20with%20Docker.jpg/confirmation.png)

> Create a volume named webappl

    docker volume create webappl
![volume](./Getting%20started%20with%20Docker.jpg/createvolume.png)

> Inspect the volume 

    docker volume inspect webapp1
![volume](./Getting%20started%20with%20Docker.jpg/volumedets.png)

> Start the Apache web server in a docker container with the volume mounted in its DirectoryRoot 

    docker container run -d -p 80:80 -v webapp1:/usr/local/apache2/htdocs

![volumecont](./Getting%20started%20with%20Docker.jpg/Dockercontainerend.png)

    docker container ls
![check](./Getting%20started%20with%20Docker.jpg/lscommand.png)

> copy a few files in the volumes directory

    echo "I am having fun learning linux, this docker cli is really cool" >>Learning

    ls

    cat learning

    cp /root/Learning /var/lib/docker/volumes/webapp1/_data/index.html

![cp_files](./Getting%20started%20with%20Docker.jpg/learning.png)
![end](./Getting%20started%20with%20Docker.jpg/end.png)

> Access the files in the volume with a browser

![apache](./Getting%20started%20with%20Docker.jpg/apache_browser.png)


