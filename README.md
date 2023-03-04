![](https://github.com/vrnaik/docker/blob/main/VRN-32x32.png)
## Docker Cheatsheet by Vikas Naik

all core Docker features including Dockerfiles and Docker Compose.

> writing down all the important commands and side notes for future reference.

## Tech

- [Docker] - Docker is a platform designed to help developers build, share, and run modern applications!
- [Salesforce] - Application as a Service/ Platform as a Service
- [node.js] - evented I/O for the backend
- [Express] - fast node.js network app framework [@tjholowaychuk]
- [AngularJS] - HTML enhanced for web apps!
- [Ace Editor] - awesome web-based text editor
- [Dillinger] - Markdown Editor
- [markdown-it] - Markdown parser done right. Fast and easy to extend.
- [Twitter Bootstrap] - great UI boilerplate for modern web apps
- [Gulp] - the streaming build system
- [Breakdance](https://breakdance.github.io/breakdance/) - HTML
to Markdown converter
- [jQuery] - duh.


## Docker
### 1. Basic docker containers and commands:
```sh
docker run --name hellWorld hello-world  // this will download hello-world image from remote registry of dockerhub and runs the container.
```
> -Note: <br />
> -the `run` in above command creates new container and runs the container.<br />
> -if no process running in the container, the container will get terminated immediately.<br />
> the flag `--name hellWorld` is used to give a name to the container. If we don't provide a name to the container, a random name is assigned to the container.<br />
> it is not possible to create two container with same name.
---
```sh
docker pull alpine // this will only download the image
```
---
```sh
docker ps // shows all running containers
```
> -`docker container ls` is an alternative command to `docker ps`
> -`docker ps` commands shows containerid, container name, port and the command that's immediately executed inside the container.

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
> -here with `-p 8080:80` we have opened port 8080 of the system and mapped it with container's port 80. 
> 
> -all request to port 8080 is forwarded to port 80 of the container.
> 
> -now localhost:8080 will work
---
```sh
docker run -p 8080:80 -v /Users/vikasnaikmacbkpro/CodeWorkspace/Nginx:/usr/share/nginx/html nginx
```
> -here `/Users/vikasnaikmacbkpro/CodeWorkspace/Nginx` is local system directory path and `/usr/share/nginx/html` is container's directory path.
---
> List of all restricted ports on chrome:
> 1,      // tcpmux
7,      // echo
9,      // discard
11,     // systat
13,     // daytime
15,     // netstat
17,     // qotd
19,     // chargen
20,     // ftp data
21,     // ftp access
22,     // ssh
23,     // telnet
25,     // smtp
37,     // time
42,     // name
43,     // nicname
53,     // domain
69,     // tftp
77,     // priv-rjs
79,     // finger
87,     // ttylink
95,     // supdup
101,    // hostriame
102,    // iso-tsap
103,    // gppitnp
104,    // acr-nema
109,    // pop2
110,    // pop3
111,    // sunrpc
113,    // auth
115,    // sftp
117,    // uucp-path
119,    // nntp
123,    // NTP
135,    // loc-srv /epmap
137,    // netbios
139,    // netbios
143,    // imap2
161,    // snmp
179,    // BGP
389,    // ldap
427,    // SLP (Also used by Apple Filing Protocol)
465,    // smtp+ssl
512,    // print / exec
513,    // login
514,    // shell
515,    // printer
526,    // tempo
530,    // courier
531,    // chat
532,    // netnews
540,    // uucp
548,    // AFP (Apple Filing Protocol)
554,    // rtsp
556,    // remotefs
563,    // nntp+ssl
587,    // smtp (rfc6409)
601,    // syslog-conn (rfc3195)
636,    // ldap+ssl
993,    // ldap+ssl
995,    // pop3+ssl
1719,   // h323gatestat
1720,   // h323hostcall
1723,   // pptp
2049,   // nfs
3659,   // apple-sasl / PasswordServer
4045,   // lockd
5060,   // sip
5061,   // sips
6000,   // X11
6566,   // sane-port
6665,   // Alternate IRC [Apple addition]
6666,   // Alternate IRC [Apple addition]
6667,   // Standard IRC [Apple addition]
6668,   // Alternate IRC [Apple addition]
6669,   // Alternate IRC [Apple addition]
6697,   // IRC + TLS
10080,  // Amanda
---
### 3. Container Management:

```sh
docker run -p 8080:80 -d nginx // runs the container in the background
```
> -the `-d` flag in above command runs the container in the background and all the logs are stored to review it later.
> -above command will return the SHA Hashcode and run the container in background.
> -we can use command `docker log 922590` to view log of container running in the background.
---

```sh
docker log 922590 // shows log of the container having id 922590, put only first few chars of the containerid running in the background.
```

---
```sh
docker run --name ubuntu1 ubuntu // 
```
> Note: 
> -with above command we can create multiple container from same image.
> -all containers will have different environment with diff file structure but will share   same DOCKER HOST resources among them.
> -all containers will have different ip address but will be in same network as of network bridge of local system (DOCKERHOST).

---
```sh
docker start ubuntu1 // start the existing container which was stopped in the past
```
> -the `start` in above command is used to start the existing container which is currently not running.
> -`ubuntu1` in above command is the container name that we want to start.
> -with `docker start` command container will be started exactly with the same configuration as it was running with before exit.(ie port mapping, volume mapping, container name)
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

