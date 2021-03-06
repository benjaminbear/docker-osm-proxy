# Open Street Map Proxy 

Minimalist Open Street Map Proxy docker container in nodejs

## Usage

Pull repository

```bash
docker pull bbaerthlein/docker-osm-proxy
```


Run container:

```bash
docker run -p 8080:8080 bbaerthlein/docker-osm-proxy
```

Access for test open:

```
http://127.0.0.1:8080/0/0/0.png
```

Force type in url:

```
http://127.0.0.1:8080/0/0/0.png?r=tile
http://127.0.0.1:8080/0/0/0.png?r=other
```

## Environment variables

```
ENV OSM_PROXY_PORT=8080
ENV OSM_PROXY_CACHE_PATH=/var/cache/openstreetmap-proxy
ENV OSM_PROXY_LAYER_URL=http://{s}.{type}.openstreetmap.org/{z}/{x}/{y}.png
ENV OSM_PROXY_CACHE_LIFETIME=2592000 # in milliseconds
ENV OSM_PROXY_CACHE_VALID_ORIGINS=mydomain.org,anotherdomain.com # empty to disable origin validation
```

## Mount cache directory 

If you want persist cache directory

```bash
mkdir "$(pwd)/cache" # Create dir with user uid 1000
docker  run -v "$(pwd)/cache":/var/cache/openstreetmap-proxy -p 8080:8080 bbaerthlein/docker-osm-proxy
```

## Docker hub

https://hub.docker.com/r/bbaerthlein/docker-osm-proxy