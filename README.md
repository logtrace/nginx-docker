# NGINX docker
This repository contains a Dockerfile extended from the original docker image to setup the nginx for a ghost optimization script. The idea is to make it easier and quick to setup ghost blog with nginx for personal bloggers.

The original optimization script is taken from [here](https://gist.github.com/vvo/7414035#file-ghost-performance-nginx-config-conf)
## Setup Requirements
To use this in your environment you should have docker installed and your ghost blog should be running as a docker container.

## Usage
Create a directory structure called `nginx/conf` in `/var/lib`. Final directory structure would look like `/var/lib/nginx/conf`. Copy `default.conf` in to `/var/lib/nginx/conf`. Replace all the places containing `<ghost_host>:<ghost_port>` with your ghost docker container host and(or) port.

Then execute the following command
```
docker run --name nginx --link <ghost_blog_container_name> -p 80:80 -p 443:443 -v /var/lib/nginx/conf:/etc/nginx/conf.d -d logtrace/nginx
```
Your nginx should be up and running in no time.
