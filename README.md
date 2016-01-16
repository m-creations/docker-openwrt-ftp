docker-openwrt-ftp
===================

An image based on OpenWrt x86_64 which runs a ftp server.

How to use
----------

The simplest case is to specify user name and password when starting
the container:

```
docker run -p 11021:21 -it --rm -e FTP_USER=scott -e FTP_PASS=tiger -e HOST=publicname.example.com mcreations/openwrt-ftp
```

Note that ```HOST``` signifies the name or IP with which the docker
container can be reached from clients, usually the public IP or
name of the docker host where the container is started.

Now, you can ftp to this docker instance with

```
ftp publicname.example.com 11021
```

#### Passive ports

The default configuration uses passive ports from 65000 to 65100. If
you need to publish a specific port range on your host, you can narrow
down the range with the environment variables ```PASV_MIN_PORT``` and
```PASV_MAX_PORT```:

```
docker run -it --rm \
            -p 11021:21 \
            -e FTP_USER=scott -e FTP_PASS=tiger -e HOST=myserver.domain.com \
            -p 65000-65004:65000-65004 \
            -e PASV_MIN_PORT=65000 -e PASV_MAX_PORT=65004 \
            mcreations/ftp
```

Here, the ```PASV_MIN_PORT``` variable could be omitted as it defaults to 65000.

Contributors
------------

Many thanks to the following people who contributed to the project:

- Arnaud de Mouhy

Github Repo
-----------

https://github.com/m-creations/docker-openwrt-ftp
