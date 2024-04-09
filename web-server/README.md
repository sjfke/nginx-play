# Nginix Notes

## Stop, Start and Configuration test

```shell
# stop, start etc
$ nginx -s stop   # fast shutdown
$ nginx -s quit   # graceful shutdown
$ nginx -s reload # reloading the configuration file
$ nginx -s reopen # reopening the log files

$ nginx -v        # version
nginx version: nginx/1.25.3

$ nginx -t        # configuration test
nginx: the configuration file /etc/nginx/nginx.conf syntax is ok
nginx: configuration file /etc/nginx/nginx.conf test is successful
```

## References

* [Deploying NGINX and NGINX Plus on Docker](https://docs.nginx.com/nginx/admin-guide/installing-nginx/installing-nginx-docker/)
* [Setting Up Nginx with Self-Signed HTTPS in Docker Compose](https://ecostack.dev/posts/nginx-self-signed-https-docker-compose/)
* [The Powerhouse Guide to the Nginx Include Directive](https://thelinuxcode.com/nginx-include/)
* [docker compose](https://docs.docker.com/reference/cli/docker/compose/)
* [docker compose build](https://docs.docker.com/reference/cli/docker/compose/build/) - Build or rebuild services
* [How to Use Docker Cp to Copy Files Between Host and Containers](https://www.howtogeek.com/devops/how-to-use-docker-cp-to-copy-files-between-host-and-containers/)

```shell
# define variables
PS C:\Users\sjfke> $name = "crazy-frog"
PS C:\Users\sjfke> $image = "localhost/nginx-test"

# build image
PS C:\Users\sjfke> docker build --tag $image --no-cache -f .\Dockerfile $PWD
PS C:\Users\sjfke> docker image ls $image

# run, test, delete container
PS C:\Users\sjfke> docker run --name $name -p 8080:80 -d $image
PS C:\Users\sjfke> docker exec -it $name bash
PS C:\Users\sjfke> docker rm --force $name

# using compose
PS C:\Users\sjfke> $project = "enginx"
PS C:\Users\sjfke> docker compose -p $project -f .\compose.yaml build
PS C:\Users\sjfke> docker compose -p $project -f .\compose.yaml up -d

PS C:\Users\sjfke> $container = docker ps --format json | jq '.Names' # enginx-nginx-test-1
PS C:\Users\sjfke> $container = docker ps --format json | jq 'select(.Image|test(\"^enginx.\")) | .Names' # enginx-nginx-test-1
PS C:\Users\sjfke> docker exec -it $container bash
# PS C:\Users\sjfke> docker exec -it enginx-nginx-test-1 bash
PS C:\Users\sjfke> docker compose -p $project -f .\compose.yaml down
```

## ``jq`` Installation and Usage

```shell
# Install 'jq'
PS C:\Users\sjfke> winget install jqlang.jq # Windows
$ sudo dnf install jq                       # Fedora
$ brew install jq                           # MacOS
```

Usage see [jq Manual (development version)](https://jqlang.github.io/jq/manual/)
