# docker-php-hello-world

used to start any docker php project

setup project steps:

    $ git clone git@github.com:waqleh/docker-php-hello-world.git
    $ cd docker-php-hello-world/docker
    $ docker-compose build
    $ docker-compose up

url: http://localhost/

## Info:

3 containers:
- MySQL, with mounted volume for data persistent
- PHP-FPM, with mounted volume for application’s code
- NGINX, with mounted volumes for configurations, logs, and share mounted volume with PHP-FPM for application’s assets

environment variables file: docker/.env

## Docker Stuff

### Config
Check whether all is well in the docker composer config file (docker-compose.yml).
    docker-compose config

### Build
    docker-compose up
    
### Rebuild
`Dockerfile` changes will not reflect unless we re-build everything.

    docker-compose up --build

### Interacting with Docker containers
Run a command inside a container with `docker exec`. To logon to MySQL, use MySQL image name, for that run `docker ps -a`. The name of the container is `mysql-server-80`:

    docker exec -it mysql-server-80  bash -l

### Import DB
    docker exec -i mysql-server-80  mysql -u root -p.rootpasswd. horse_racing_simulator < ./sql/horse_racing_simulator.sql
    
### Turn Off
    docker-compose down

### Turn Off all Docker containers:
    docker stop $(docker ps -a -q)

### Delete all containers
    docker rm $(docker ps -a -q)
    
### Delete all images
    docker rmi $(docker images -q)
    
### The official command to remove all unused data (including volumes without containers) will be with docker 1.13 

    docker system prune  

### If you want to limit to volumes alone, [removing only unused volumes][1]:

    docker volume prune

You also have `docker image prune`, `docker container prune`

### To remove everything for this project:

    docker system prune -a
    WARNING! This will remove:
      - all stopped containers
      - all networks not used by at least one container
      - all images without at least one container associated to them
      - all build cache

    Are you sure you want to continue? [y/N] y