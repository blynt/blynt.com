---
layout: '../../layouts/Page.astro'
title: "Docker Cheatsheet"
---

## Images

#### List images

```bash
docker ps
```

Fetch remote image

```bash
docker pull ubuntu
```

### Remove images

```bash
docker rmi <image_id:version>
```

Force remove images

```bash
docker rmi -f <image_id:version>
```

## Containers

#### Start container

In interactive mode (with terminal)

```bash
docker run --name my-ubuntu -it ubuntu -p 80:80
```

In detached mode (background)

```bash
docker run --name my-ubuntu -d ubuntu -p 80:80
```

This uses port mapping, so the container's port 80 is mapped to the host's port
80 (so you can open `http://localhost:80` in your browser).

Example using default Postgres container:

```bash
docker run --name my-postgres -e POSTGRES_PASSWORD=mysecretpassword -d postgres
```

#### Execute command on a running container

```bash
docker exec -it <container_id> psql -U postgres
```

#### Attach to a running container

```bash
docker attach <container_id>
```

#### List running containers

```bash
docker ps
```

#### Stop a running container

```bash
docker stop <container_id>
```

#### Remove a container

```bash
docker rm <container_id>
```
