docker-openwrt-ftp
===================

An image based on OpenWrt x86_64 which runs a ftp server.

How to use
----------

The simplest case is to specify user name and password when starting
the container:

```
docker run -it --rm \
            -p 11021:21 \
            -p 65100:65100 -p 65101:65101 -p 65102:65102 -p 65103:65103 -p 65104:65104 \
            -e FTP_USER=scott -e FTP_PASS=tiger -e HOST=localhost \
            -e PASV_MIN_PORT=65000 -e PASV_MAX_PORT=65004 \
            mcreations/ftp
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
