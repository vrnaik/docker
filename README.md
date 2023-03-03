![](https://github.com/vrnaik/docker/blob/main/VRN-32x32.png)
## Docker Cheatsheet by Vikas Naik

all core Docker features including Dockerfiles and Docker Compose.

> writing down all the important commands and side notes for future reference.

## Tech

- [Docker] - Docker is a platform designed to help developers build, share, and run modern applications!
- [Salesforce] - Application as a Service/ Platform as a Service
- [AngularJS] - HTML enhanced for web apps!
- [Ace Editor] - awesome web-based text editor
- [Dillinger] - Markdown Editor
- [markdown-it] - Markdown parser done right. Fast and easy to extend.
- [Twitter Bootstrap] - great UI boilerplate for modern web apps
- [node.js] - evented I/O for the backend
- [Express] - fast node.js network app framework [@tjholowaychuk]
- [Gulp] - the streaming build system
- [Breakdance](https://breakdance.github.io/breakdance/) - HTML
to Markdown converter
- [jQuery] - duh.


## Docker
### 1. Basic docker containers and commands:
```sh
docker run hello-world  // this will download hello-world image from remote registry of dockerhub and runs the container.
```
> Note: if no process running in the container, the container will get terminated immediately.
---
```sh
docker pull alpine // this will only download the image
```
---
```sh
docker ps // shows all running containers
```
> `docker container ls` is an alternative command to `docker ps`

---
```sh
docker ps -a  // shows all past executed containers and their shell
```
---
```sh
docker stop D7 //  stops the running contailner, put only two chars of containerID
```
> Note: we can put container name also instead of container id. All running container info is shown by using `docker ps` command
---

```sh
docker run -it ubuntu // enters bash shell of ubuntu. Enter exit to exit the bash shell.
```
---

```sh
docker images // shows all downloaded images with its size.
```
---
### 2. Volume mapping and port mapping:

```sh
docker run nginx // runs nginx container with port 80 opened
```
---
```sh
docker run -p 8080:80 nginx
```
> here with `-p 8080:80` we have opened port 8080 of the system and mapped it with container's port 80. all request to port 8080 is forwarded to port 80 of the container.
> now localhost:8080 will work
---
```sh
docker run -p 8080:80 -v /Users/vikasnaikmacbkpro/CodeWorkspace/Nginx:/usr/share/nginx/html nginx
```
> here /Users/vikasnaikmacbkpro/CodeWorkspace/Nginx is local system directory path and /usr/share/nginx/html is container's directory path.
---
### 3. Container Management:

```sh

```
---

```sh

```
---

```sh

```
---

```sh

```
---

```sh

```
---



[//]: # (These are reference links used in the body of this note and get stripped out when the markdown processor does its job. There is no need to format nicely because it shouldn't be seen. Thanks SO - http://stackoverflow.com/questions/4823468/store-comments-in-markdown-syntax)

  
   
   [markdown-it]: <https://github.com/markdown-it/markdown-it>
   [Ace Editor]: <http://ace.ajax.org>
   [node.js]: <http://nodejs.org>
   [Twitter Bootstrap]: <http://twitter.github.com/bootstrap/>
   [jQuery]: <http://jquery.com>
   [@tjholowaychuk]: <http://twitter.com/tjholowaychuk>
   [express]: <http://expressjs.com>
   [AngularJS]: <http://angularjs.org>
   [Gulp]: <http://gulpjs.com>
   [Docker]: <https://www.docker.com>
   [Salesforce]: <https://www.salesforce.com>
   [Dillinger]: <https://dillinger.io/>

