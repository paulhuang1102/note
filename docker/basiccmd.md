# Docker basic cmd

## Install docker on mac

```
brew cask install docker
```

## Find docker image, pull, and remove run and list 

We can find docker on open registry or use 'docker search [software]'. Docker hub is the official open registry(https://hub.docker.com)

```
docker search node
```

use docker pull to download docker image and use : to specific version

```
docker pull node  //lastest version
docker pull node:8.11.3-stretch //specific version
docker images //list all docker image

REPOSITORY          TAG                 IMAGE ID            CREATED             SIZE
node                latest              0e2811757f93        5 days ago          673MB
node                8.11.3-stretch      65c2b8c0072d        3 weeks ago         891MB
```

remove docker image
```
docker rmi [image id]
```

use dockerfile to create new image
```
docker build -t [new image name] . //
```

## Docker life cycle

use docker run (-p is setting port[8080 is external port][80 is internal port]; -d is detach mode: run in backgroud)
```
docker run -p 8080:80 -d nginx
```

use docker ps to list docker  (-a is list all docker history)
```
docker ps

CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS              PORTS                      NAMES
c911fb88f224        mongo               "docker-entrypoint.s…"   22 minutes ago      Up 22 minutes       0.0.0.0:27017->27017/tcp   optimistic_shirley
807ed3ef5f77        nginx               "nginx -g 'daemon of…"   5 hours ago         Up 5 hours          0.0.0.0:8080->80/tcp       objective_lichterman
```

stop and remove
```
docker stop [container id]
docker rm [container id]
```

see the inspect
```
docker inspect [container id]
```

see the specific inspect (ex: see the container ip)
```
docker inspect --format '{{.NetworkSettings.IPAddress}}' [container id]
```

see the stats (like top)
```
docker stats

CONTAINER ID        NAME                   CPU %               MEM USAGE / LIMIT     MEM %               NET I/O             BLOCK I/O           PIDS
e72d1f6145a9        ccr_ccr_1              0.00%               51.52MiB / 1.952GiB   2.58%               452kB / 331kB       0B / 4.1kB          22
8e1e84df55d0        ccr_mongo_1            0.49%               42.73MiB / 1.952GiB   2.14%               229kB / 298kB       0B / 4.67MB         43
807ed3ef5f77        objective_lichterman   0.00%               1.934MiB / 1.952GiB   0.10%               7.01kB / 2.44kB     0B / 0B             2

docker stats [container id]
CONTAINER ID        NAME                CPU %               MEM USAGE / LIMIT     MEM %               NET I/O             BLOCK I/O           PIDS
e72d1f6145a9        ccr_ccr_1           0.11%               51.44MiB / 1.952GiB   2.57%               470kB / 344kB       0B / 4.1kB          22
```

see the logs
```
docker logs [container id]
docker logs -f [container id] //continue show
```