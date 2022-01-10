# docker

## Maintenance

Clear any old docker images that aren't in use
  `docker container prune`
  `docker system prune -a`
  `docker volumes prune`

View volumes. Check docker volumes count not increasing more than expected.
  `ls -la /var/lib/docker/volumes | wc -l`

## Containers

All running containers in docker engine
  `docker ps`
Include stopped containers
  `docker ps -a`  
Minimal output
  `docker ps --format "table {{.Names}}\t{{.Status}}"`
Only Ids (useful for piping etc.)
```docker ps -aq```
Remove containers except
  `docker rm $(docker ps -a | grep -v "post" | awk 'NR>1 {print $1}')`
Remove all containers
  `docker rm $(docker ps -aq)`
Stop and remove all
  `docker stop $(docker ps -aq) && docker rm $(docker ps -aq)`
Stop all running containers
  `docker stop $(docker ps -aq)`
Inspect just mounts:
  `docker inspect -f '{{ .Mounts }}' CONTAINERID`

### Logs

Redirect stderr to stdout in order to grep.
  `docker logs mkweb 2>&1 | grep webhook`

Clear logs without deleting files
`echo "" > $(docker inspect --format='{{.LogPath}}' <container_name_or_id>)`

### Build
  `docker-compose build`

### Run
  `docker-compose run --entrypoint bash NAME`

### Images
Remove all images (force)
  `docker rmi -f $(docker images -q)`

### Exec
  `docker exec -ti CONTAINER bash`

### Commit
  `docker commit CONTAINERID IMAGE`

## Hacks
### Keep any container running
For example, your container won't start up because there is an exception. You want to dive into a bash shell to inspect, but can't because the failed container gets closed down.

Solve this by adding a simple entrypoint that keeps running such as:
  `entrypoint: tail -F anything`