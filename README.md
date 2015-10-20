docker-h2
=========

Dockerized H2 database service.

A mix of [zhilvis/docker-h2](https://github.com/zhilvis/docker-h2) and [zilvinasu/h2-dockerfile](https://github.com/zilvinasu/h2-dockerfile).

Get an [automated build](https://hub.docker.com/r/oscarfonts/h2/) from [docker registry](https://registry.hub.docker.com/).


## Running

Get the image:

```
docker pull oscarfonts/h2
```

Run as a service, exposing ports 1521 (TCP database server) and 81 (web interface) and mapping DATA_DIR to host:

```
docker run -d -p 1521:1521 -p 81:81 -v /path/to/local/data_dir:/opt/h2-data oscarfonts/h2 --name=MyH2Instance
```

See the tomcat logs while running:

```
docker logs -f MyH2Instance
```
