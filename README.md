# Docker Compose Persistant Volume example

## Tutorial

Basic:

`git checkout 1-basic`

Persist redis data:

`git checkout 2-persist-redis-example`

Shows the definition, and creation of a persitant volume 
between container starts, stops and removal. Any data written to the volume 
persists.

The later example mounts to the /data path to persist the redis data.  
We know that it neds to be the /data path by reading the dockerhub docks for the 
redis image. Also, the `--appendonly yes` flag is needed on the redis server
commend to tell it to persist data.

```
docker-compose up
```

Video: 

Connect with redis, from outside the container:

```
nc -v 127.0.0.1 6379
```

Validate we can persist data:

```
SET colour red
+OK
GET colour
$3
red
```
Now stop the containers (Ctl+C) or `docker-compose stop`.

Restart the project: 
```
docker-compose up
```
Verify data is still there: Again from outside container

```
nc -v 127.0.0.1 6379
Connection to 127.0.0.1 6379 port [tcp/*] succeeded!
GET colour
$3
red
```
