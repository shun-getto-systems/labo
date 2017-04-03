# labo

laboratory docker image for developper


## run container

```
docker run -d --name getto-labo -h getto-labo -p $PORT:22 -v shared:/home/shun/.shared getto/labo.shun
```

### init container

```
docker exec -u shun:shun getto-labo /home/shun/bin/labo-setup
```

### setup shared

```
docker volume create --name shared
docker run -it -v shared:/home/shun/.shared getto/labo.shun bash
$ sudo chown shun:shun .shared
```

### setup shared/.config

```
git clone https://github.com/shun-fix9/configfiles.git .shared/.config
```


## build image

```
docker build -t getto/labo.shun .
```


## user-data.yml

* docker-tcp.socket : see https://coreos.com/os/docs/latest/customizing-docker.html
* start docker.service

### for google cloud

metadata : key=user-data, value=`paste user-data.yml`
