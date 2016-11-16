# Supported tags and respective `Dockerfile` links

-	[`0.1.8-beta`, `latest` (*0.1/Dockerfile*)](https://github.com/nexocrew/docker_3nigm4_storageservice/0.1/Dockerfile)

# What is 3nigm4 Storage Service?
Official 3nigm4 Storage Service image implements API frontend to manage data uploads to an S3 instance. It's one of the microservices composing the 3nigm4 framework: secure storage of encrypted, metadata free, data chunks.

# How to use this image

## start a storageservice instance

The following example links to an auth-service container from [3nigm4 Auth Server](https://hub.docker.com/r/nexo/3n4auth) image to access authentication sevices and uses a mongodb container from the official [MongoDb image](https://hub.docker.com/_/mongo/).

```console
$ docker run -d --name store-service -p 80:80 --link mongodb:mongodb --link auth-service:auth-service nexo/3n4store 
```

To expose the service via https (really suggested) a volume containing SSL/TLS certificate and private kye must be provided (notice the Z flag is used only on SELinux eforcing systems):

```console
$ docker run -d --name store-service -p 80:80 --link mongodb:mongodb --link auth-service:auth-service -v /opt/3nigm4/ssl:/opt/3nigm4/ssl:Z nexo/3n4store 
```