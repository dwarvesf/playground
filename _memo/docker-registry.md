---
tags: 
  - docker
  - developer
  - software
title: Docker Registry
date: 2016-07-21
description: This repository’s main product is the Docker Registry 2.0 implementation for storing and distributing Docker images. It supersedes the docker/docker-registry project with a new API design, focused around security and performance.
authors: null
menu: memo
type: null
hide_frontmatter: false
---

![](assets/docker-registry_460b62865d3bc638b0bb0c4f7e23260e_md5.webp)

## Summary
The Docker toolset to pack, ship, store, and deliver content.

This repository’s main product is the Docker Registry 2.0 implementation for storing and distributing Docker images. It supersedes the docker/docker-registry project with a new API design, focused around security and performance.

## To be simple
### Server
Simply, just run below command:

```javascript
$ docker run -d -p 5000:5000 --restart=always --name registry registry:2
```

### Client
Get any image from the hub and tag it to point to the registry

```javascript
$ docker pull ubuntu && docker tag ubuntu your-domain:5000/ubuntu
$ docker push your-domain:5000/ubuntu
$ docker pull your-domain:5000/ubuntu
```

### Running a domain registry
While running on `localhost` has its uses, most people want their registry to be more widely available. To do so, the Docker engine requires you to secure it using TLS, which is conceptually very similar to configuring your web server with SSL.

### Server
Let's create some directories

```javascript
$ mkdir registry && cd registry && mkdir certs && mkdir data && mkdir auth
```

First of all, create `htpasswd` file so that client can login to this hub

```javascript
$ docker run --entrypoint htpasswd registry:2 -Bbn testuser testpassword > auth/htpasswd
```

And now, copy or create your own seft sign certificates and save these file `{ca.pem,cert.pem,key.pem}` into `certs/`

```javascript
$ docker run --rm \
  -v ~/docker_registry_tls/certs:/certs \
  -e SSL_IP=<your-docker-hub-ip> \
  -e SSL_DNS=<your-docker-hub-domain> \
  paulczar/omgwtfssl
```

Then, create docker-compose.ymp

```javascript
registry:
  restart: always
  image: registry:2
  ports:
    - 443:5000
  environment:
    REGISTRY_HTTP_TLS_KEY: /certs/key.pem
    REGISTRY_HTTP_TLS_CERTIFICATE: /certs/cert.pem
    REGISTRY_HTTP_TLS_CLIENTCAS_0: /certs/ca.pem
    REGISTRY_HTTP_SECRET: someRandomSecret
    REGISTRY_AUTH: htpasswd
    REGISTRY_AUTH_HTPASSWD_PATH: /auth/htpasswd
    REGISTRY_AUTH_HTPASSWD_REALM: Registry Realm
  volumes:
    - ~/docker_registry_tls/data:/var/lib/registry
    - ~/docker_registry_tls/certs:/certs
    - ~/docker_registry_tls/auth:/auth
```

And run `$ docker-compose up -d`

### Client
Create `ca.crt` for each client with content of `ca.crt` file that you’ve created above:

```javascript
$ sudo mkdir -p /etc/docker/certs.d/<your-hub-domain>/
$ sudo vim /etc/docker/certs.d/<your-hub-domain>/ca.crt
```

Try to login

```javascript
$ docker login <your-hub-domain>
```

That’s all, now you can login to your hub and pull, push whatever you want

## Issue
You may get some troubles like:

```javascript
FATA[0000] Error response from daemon: v1 ping attempt failed with error:
Get https://myregistrydomain.com:5000/v1/_ping: tls: oversized record received with length 20527.
If this private registry supports only HTTP or HTTPS with an unknown CA certificate,please add
`--insecure-registry myregistrydomain.com:5000` to the daemon's arguments.
In the case of HTTPS, if you have access to the registry's CA certificate, no need for the flag;
simply place the CA certificate at /etc/docker/certs.d/myregistrydomain.com:5000/ca.crt
```

## Solution

### Insecure registry
* Linux
* Redhat
* On some distributions, e.g. Oracle Linux 6, the Shared System Certificates feature needs to be manually enabled:
* or you can open /etc/default/docker and add the following at the end

### Note
If you use `boot2docker` (Mac), you may do some steps below:

```javascript
$ docker-machine ssh <your-machine>
```

```javascript
$ cd /var/lib/boot2docker && sudo vi profile
```

and you need to add `--insecure-registry=<your-domain>` (dont need to include port if your hub server use port 443) inside EXTRA_ARGS like:

```javascript
EXTRA_ARGS='
--label provider=virtualbox
--insecure-registry=<your-domain>
'
```

Exit and `docker-machine restart <your-machine>`.

Now you can login to your hub and pull-push your image.
