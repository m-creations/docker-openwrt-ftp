docker-openwrt-ftp
===================

An image based on OpenWrt x86_64 which runs a ftp server.

How to use
----------

The simplest case is to specify user name and password when starting
the container:

```
docker run -p 11021:21 -it --rm -e FTP_USER=scott -e FTP_PASS=tiger -e HOST=localhost mcreations/openwrt-ftp
```

Note that ```HOST``` signifies the name or IP with which the docker
container can be reached from clients, usually the docker host where
the container is started.

Now, you can ftp to this docker instance with

```
ftp localhost 11021
```

Github Repo
-----------

https://github.com/m-creations/docker-openwrt-ftp
