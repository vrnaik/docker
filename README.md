<a name="docker-cheatsheet-by-vikas-naik"></a>
<h1><img src="https://raw.githubusercontent.com/vrnaik/docker/main/Images/VRN-32x32.png"  style="height: 28px; margin-right:5px ;"> Docker Cheatsheet by Vikas Naik</h1>

all core Docker features including Dockerfiles and Docker Compose.

> writing down all the important commands and side notes for future reference.

<!-- TOC start -->
- [Tech](#tech)
- [Docker](#docker)
  * [1. Basic docker containers and commands](#1-basic-docker-containers-and-commands-back)
  * [2. Volume mapping and port mapping](#2-volume-mapping-and-port-mapping-back)
  * [List of all restricted ports on chrome](#list-of-all-restricted-ports-on-chrome-back)
  * [3. Container Management](#3-container-management-back)
  * [4. Image Management](#4-image-management-back)
  * [5.A. Node.js in Docker](#4a-nodejs-in-docker-back)
  * [5.B. Express.js in Docker](#4b-expressjs-in-docker-back)
  * [Docker Alternative Commands](#docker-alternative-commands)
  * [Docker Client Server Architecture](#docker-client-server-architecture-back)
  * [Quick Reference](#quick-reference-back)
  * [Glossary ](#glossary-back)
<!-- TOC end -->

<!-- TOC --><a name="tech"></a>
## Tech

- [Docker] - Docker is a platform designed to help developers build, share, and run modern applications!
- [Salesforce] - Application as a Service/ Platform as a Service
- [node.js] - evented I/O for the backend
- [Express] - fast node.js network app framework [@tjholowaychuk]
- [AngularJS] - HTML enhanced for web apps!
- [Netlify] - Drop a folder with your site’s HTML, CSS, and JS files.
- [Ace Editor] - awesome web-based text editor
- [Meditor] - Open source online Markdown editor
- [Dillinger] - Markdown Editor
- [Derlin] - Markdown TOC generator
- [markdown-it] - Markdown parser done right. Fast and easy to extend.
- [Twitter Bootstrap] - great UI boilerplate for modern web apps
- [Gulp] - the streaming build system
- [Breakdance](https://breakdance.github.io/breakdance/) - HTML
to Markdown converter
- [jQuery] - duh.


<!-- TOC --><a name="docker"></a>
## Docker
<!-- TOC --><a name="1-basic-docker-containers-and-commands-back"></a>
### 1. Basic docker containers and commands: [Back](#docker-cheatsheet-by-vikas-naik)
```sh
docker run --name hellWorld hello-world  // this will download hello-world image from remote registry of dockerhub and runs the container.
```
> Note: <br />
> - the `run` in above command creates new container and runs the container.<br />
> - if no process running in the container, the container will get terminated immediately.<br />
> - the flag `--name hellWorld` is used to give a name to the container. If we don't provide a name to the container, a random name is assigned to the container.<br />
> - it is not possible to create two container with same name.<br />
---
```sh
docker pull alpine // this will only download the image
```
---
```sh
docker ps // shows all running containers
```
> - `docker container ls` is an alternative command to `docker ps` <br />
> - `docker ps` commands shows containerid, container name, port and the command that's immediately executed inside the container. <br />

---
```sh
docker ps -a  // shows all past executed containers and their shell
```
---
```sh
docker stop D7 //  stops the running contailner, put only two chars of containerID
```
> Note: we can put container name also instead of container id. All running container info is shown by using `docker ps` command. <br />
---
```sh
docker kill D7 //  stops the running container, use this if `docker stop` is not responding.
```
---

```sh
docker run -it ubuntu // enters bash shell of ubuntu. Enter exit to exit the bash shell.
```
---

```sh
docker exec ubuntu1 echo "hello world" // this will execute echo command inside ubuntu1 container
```
---
```sh
docker exec -it ubuntu1 bash // with this command we can enter ubuntu1 containers bash shell in interactive mode
```
---
<!-- TOC --><a name="2-volume-mapping-and-port-mapping-back"></a>
### 2. Volume mapping and port mapping: [Back](#docker-cheatsheet-by-vikas-naik)

```sh
docker run nginx // runs nginx container with port 80 opened
```
---
```sh
docker run -p 8080:80 nginx
```
> - here with `-p 8080:80` we have opened port 8080 of the system and mapped it with container's port 80. <br />
> - all request to port 8080 is forwarded to port 80 of the container.<br />
> - now localhost:8080 will work. <br />
---
```sh
docker run -p 8080:80 -v /Users/vikasnaikmacbkpro/CodeWorkspace/Nginx:/usr/share/nginx/html nginx
```
> - here `/Users/vikasnaikmacbkpro/CodeWorkspace/Nginx` is local system directory path and `/usr/share/nginx/html` is container's directory path.
---
<!-- TOC --><a name="list-of-all-restricted-ports-on-chrome-back"></a>
### List of all restricted ports on chrome: [Back](#docker-cheatsheet-by-vikas-naik)

| Port      | process |
| :--------- | :-----:|
|1|      // tcpmux                                   |
|7|      // echo                                     |
|9|      // discard                                  |
|11|     // systat                                   |
|13|     // daytime                                  |
|15|     // netstat                                  |
|17|     // qotd                                     |
|19|     // chargen                                  |
|20|     // ftp data                                 |
|21|     // ftp access                               |
|22|     // ssh                                      |
|23|     // telnet                                   |
|25|     // smtp                                     |
|37|     // time                                     |
|42|     // name                                     |
|43|     // nicname                                  |
|53|     // domain                                   |
|69|     // tftp                                     |
|77|     // priv-rjs                                 |
|79|     // finger                                   |
|87|     // ttylink                                  |
|95|     // supdup                                   |
|101|    // hostriame                                |
|102|    // iso-tsap                                 |
|103|    // gppitnp                                  |
|104|    // acr-nema                                 |
|109|    // pop2                                     |
|110|    // pop3                                     |
|111|    // sunrpc                                   |
|113|    // auth                                     |
|115|    // sftp                                     |
|117|    // uucp-path                                |
|119|    // nntp                                     |
|123|    // NTP                                      |
|135|    // loc-srv /epmap                           |
|137|    // netbios                                  |
|139|    // netbios                                  |
|143|    // imap2                                    |
|161|    // snmp                                     |
|179|    // BGP                                      |
|389|    // ldap                                     |
|427|    // SLP (Also used by Apple Filing Protocol) |
|465|    // smtp+ssl								 |
|512|    // print / exec                             |
|513|    // login                                    |
|514|    // shell                                    |
|515|    // printer                                  |
|526|    // tempo                                    |
|530|    // courier                                  |
|531|    // chat                                     |
|532|    // netnews                                  |
|540|    // uucp                                     |
|548|    // AFP (Apple Filing Protocol)              |
|554|    // rtsp                                     |
|556|    // remotefs                                 |
|563|    // nntp+ssl                                 |
|587|    // smtp (rfc6409)                           |
|601|    // syslog-conn (rfc3195)                    |
|636|    // ldap+ssl                                 |
|993|    // ldap+ssl                                 |
|995|    // pop3+ssl                                 |
|1719|   // h323gatestat                             |
|1720|   // h323hostcall                             |
|1723|   // pptp                                     |
|2049|   // nfs                                      |
|3659|   // apple-sasl / PasswordServer              |
|4045|   // lockd                                    |
|5060|   // sip                                      |
|5061|   // sips                                     |
|6000|   // X11                                      |
|6566|   // sane-port                                |
|6665|   // Alternate IRC [Apple addition]           |
|6666|   // Alternate IRC [Apple addition]           |
|6667|   // Standard IRC [Apple addition]            |
|6668|   // Alternate IRC [Apple addition]           |
|6669|   // Alternate IRC [Apple addition]           |
|6697|   // IRC + TLS                                |
|10080|  // Amanda							         |
---
<!-- TOC --><a name="3-container-management-back"></a>
### 3. Container Management: [Back](#docker-cheatsheet-by-vikas-naik)
>Note: <br />
> - when a new container is created with `docker run imageName` docker creates new writable fs layer and stores in the harddrive. this writable fs layer remains in the harddisk even if the container is stopped. 
> - when we start the stopped container this writable fs layer is again used by the docker.
> - when we remove the stopped container its fs layer also gets deleted.


```sh
docker run -p 8080:80 -d nginx // runs the container in the background
```
> - the `-d` flag in above command runs the container in the background and all the logs are stored to review it later. <br />
> - above command will return the SHA Hashcode and run the container in background. <br />
> - we can use command `docker log 922590` to view log of container running in the background. <br />
---

```sh
docker log 922590 // shows log of the container having id 922590, put only first few chars of the containerid running in the background.
```

---
```sh
docker run --name ubuntu1 ubuntu // 
```
> Note: 
> - with above command we can create multiple container from same image. <br />
> - all containers will have different environment with diff file structure but will share   same DOCKER HOST resources among them. <br />
> - all containers will have different ip address but will be in same network as of network bridge of local system (DOCKERHOST). <br />
---
```sh
docker inspect ubuntu1 // to inspect the container, what is executed inside the container
```
---
```sh
docker start ubuntu1 // start the existing container which was stopped in the past
```
> - the `start` in above command is used to start the existing container which is currently not running. <br />
> - `ubuntu1` in above command is the container name that we want to start. <br />
> - with `docker start` command container will be started exactly with the same configuration as it was running with before exit.(ie port mapping, volume mapping, container name) <br />
---

```sh
docker rm ubuntu1 // delete the existing container with name ubuntu1
```

---
```sh
docker container prune  // deletes all stopped containers
```

---
```sh
docker container rm 05 d7 // deletes two stopped containers having containerids starting with 05 and d7
```

---
<!-- TOC --><a name="4-image-management-back"></a>
### 4. Image Management: [Back](#docker-cheatsheet-by-vikas-naik)
>Note: Docker Image Key Points <br />
> - it is Read Only, we cannot modify the image but we can create new image from it <br />
> - Consists of multiple fs layers <br />
> - images could be stored in the private or public repositories <br />
> - could be copied, deleted or moved <br />
> - there are official and community images <br />
> - every image has base image. we can add multiple new file system layer on top of the base image to create new custom image.
> - we can use different fs layers in different images.
> - Dockerfile is used to create new custom image.

---
```sh
docker pull busybox // this will only download the image
```
---

```sh
docker images // shows all downloaded images with its size.
```
---
```sh
docker image rm fd484f19954f // fd484f19954f is image id.
```

---
```sh
docker image prune // used to remove/delete only unused(dangling ones) images.
```

---
```sh
docker image prune -a // used to remove/delete all images. it doesn't matter if it is in use by any container.
```

---
<!-- TOC --><a name="4a-nodejs-in-docker-back"></a>
### 5.A. Node.js in Docker: [Back](#docker-cheatsheet-by-vikas-naik)

```sh
docker pull node // downloads nodejs image
```
---
```sh
docker run -it node  // create new container from node image in interactive mode
```

---
```sh
docker run -v $PWD:/app -w /app node node hello.js
```
>Note: <br />
>   - in above command we have mapped our local system current directory with node containers `/app` directory. <br />
>   - the `-w /app` indicates that we want to set `/app` directory of container as a working directory. <br />
>   - the first `node` in the command is the name of the image. <br />
>   - after the first node, every thing ie `node hello.js` is the command to be executed inside the container.  <br />
---

<!-- TOC --><a name="4b-expressjs-in-docker-back"></a>
### 5.B. Express.js in Docker: [Back](#docker-cheatsheet-by-vikas-naik)

```sh
docker run -v $PWD:/app -w /app -it node npm init 
```
>Note: <br />
> - above command will create package.jon file in /app directory of container but bcoz it mapped to our local directory, we can see this file in our local system directory. <br />
   

---
```sh
docker run -v $PWD:/app -w /app -it node npm install express
```
>Note: <br />
> - above command will install expressjs module.

---

```sh
docker run -v $PWD:/app -w /app -it -p 8081:3000 node node index.js
```
>Note: <br />
> - above command will map local system port 8081 with containers expressjs port 3000. <br />
> - the node.js is an expressjs application.
---
> to handle control C (^c) to terminate the expressjs server application, write below lines of code in the expressjs application server. 

```javascript
const process = require('process')
process.on('SIGINT',() => {
   console.log('Application is being interrupted...')
   process.exit(0)
})
```

> to terminate the express server when we stop the container write below line of code

```javascript
const process = require('process')
process.on('SIGTERM',() => {
   console.log('Application is being terminated...')
   process.exit(0)
})
```
---
<!-- TOC --><a name="docker-alternative-commands"></a>
### Docker Alternative Commands: [Back](#docker-cheatsheet-by-vikas-naik)
| Management Command (New) | Alternative Command (Old) |
| :--------- | :-----|
|docker container ls | docker ps |
|docker builder build | docker build |
|docker container inspect | docker inspect |
|docker container commit | docker commit |
|docker container run | docker run |
|docker image pull | docker pull |

---
<!-- TOC --><a name="docker-client-server-architecture-back"></a>
### Docker Client Server Architecture: [Back](#docker-cheatsheet-by-vikas-naik)
![](https://raw.githubusercontent.com/vrnaik/docker/9aed5022b213a082226bc3018022118e5b9db641/Images/Docker-architecture.svg)

<!-- TOC --><a name="quick-reference-back"></a>
### Quick Reference: [Back](#docker-cheatsheet-by-vikas-naik)
- https://docs.docker.com/get-started/overview/ (Official Documentation)
- https://hub.docker.com/ (Docker Registry)


<!-- TOC --><a name="glossary-back"></a>
### Glossary: [Back](#docker-cheatsheet-by-vikas-naik)
- Docker Client : it detects/identifies the docker commands in the terminal and sends to Docker Server. 
- Docker Server : it executes the docker commands.
- Docker Host : In linux OS, the Complete OS is the Docker Host. In Mac/Windows the docker desktop is the Docker Host. Docker Host is the Linux environment in which all containers are executed. 
- Docker Image : it is read only image from which the containers are created.
- Docker Container : containers are created from images. We can interact with Containers and edit files in the containers.
- Docker Repository : Docker Repositories are used to store different versions of the image. 
- Docker Registry : it is Docker Repository hosting service. Docker Hub website is the Docker Registry.


[//]: # (These are reference links used in the body of this note and get stripped out when the markdown processor does its job. There is no need to format nicely because it shouldn't be seen. Thanks SO - http://stackoverflow.com/questions/4823468/store-comments-in-markdown-syntax)

   <!-- http://twitter.github.com/bootstrap/ -->
   
   [markdown-it]: <https://github.com/markdown-it/markdown-it>
   [Ace Editor]: <http://ace.ajax.org>
   [node.js]: <http://nodejs.org>
   [Twitter Bootstrap]:  <https://twitter.github.io/> 
   [jQuery]: <http://jquery.com>
   [@tjholowaychuk]: <http://twitter.com/tjholowaychuk>
   [express]: <http://expressjs.com>
   [AngularJS]: <http://angularjs.org>
   [Gulp]: <http://gulpjs.com>
   [Docker]: <https://www.docker.com>
   [Salesforce]: <https://www.salesforce.com>
   [Dillinger]: <https://dillinger.io/>
   [Derlin]: <https://derlin.github.io/bitdowntoc/>
   [Netlify]: <https://app.netlify.com/drop/>
   [Meditor]: <https://pandao.github.io/editor.md/index.html>

