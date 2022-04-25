# Docker Guide
```
docker images
```

```
docker version
```

```
docker --help
```

```
docker build .
```
> #### -it = interactive
```
docker run -it (name or id)        
```

```
docker pull (id)
```
> #### -a = all
```
docker ps -a                      
```

```
docker contаiner prune
```

```
docker rmi (id)
```

```
sudo chmod 666 /var/run/docker.sock
```

```
docker stop (id)
```

```
docker start (id)
```
> #### -p = port
```
docker run -p 8000:8000 (id)      
```
> #### to delete all images  -f = force
```
docker rmi -f $(docker images -q)         
```

```
docker kill $(docker ps -q)
```

