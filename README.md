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

#### (Optional) Passive ports

If you need to publish ports to your host, as the default configuration
will use passive ports from 65000 to 65100, you may find it complicated
to specify 101 ```-p``` options on the command line. You can narrow the used
ports with the environment variables ```PASV_MIN_PORT``` and ```PASV_MAX_PORT```.

```
docker run -it --rm \
            -p 11021:21 \
            -p 65000:65000 -p 65001:65001 -p 65002:65002 -p 65003:65003 -p 65004:65004 \
            -e FTP_USER=scott -e FTP_PASS=tiger -e HOST=myserver.domain.com \
            -e PASV_MIN_PORT=65000 -e PASV_MAX_PORT=65004 \
            mcreations/ftp
```

Here, the ```PASV_MIN_PORT``` variable could be omitted as it defaults to 65000.

Github Repo
-----------

https://github.com/m-creations/docker-openwrt-ftp
