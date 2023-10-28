
```yml
# docker-compose.yaml
version: '3.8'
services:
  jenkins:
    image: jenkins/jenkins:lts
    privileged: true
    user: root
    ports:
      - "8080:8080"
      - "50000:50000"
  container_name: jenkins
  volumes:
    - /home/jenkins_compose/jenkins_compose/jenkins_configuration:/var/jenkins_home
    - /var/run/docker.sock:/var/run/docker.sock
```

```
docker-compose up -d
```
```
docker exec -it <container_name_or_id> cat /var/jenkins_home/secrets/initialAdminPassword

```
> docker ps to list all running containers
```
dkita@DESKTOP-BMN6Q80 MINGW64 ~/Documents/GitHub/jenkins/jenkins_compose (master)
$ docker ps
CONTAINER ID   IMAGE                 COMMAND                  CREATED              STATUS              PORTS                               NAMES
ba47242630e0   jenkins/jenkins:lts   "/usr/bin/tini -- /u…"   About a minute ago   Up About a minute   0.0.0.0:8080->8080/tcp, 50000/tcp   jenkins_compose-jenkins-1
9b429d43d2de   recipe-app-api-app    "sh -c 'python manag…"   5 days ago           Up 5 days           0.0.0.0:8000->8000/tcp              recipe-app-api-app-1
8c8fc3cc1a2a   postgres:13-alpine    "docker-entrypoint.s…"   5 days ago           Up 5 days           5432/tcp                            recipe-app-api-db-1
```
```
docker exec -it jenkins_compose-jenkins-1 cat /var/jenkins_home/secrets/initialAdminPassword

```

docker build image  -t jenkins-docker .