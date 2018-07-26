# Caddy for Local Development

This is a simple Caddy Docker image to get up and running with self signed SSL. 

By default it will accept all requests that come to it, verify SSL with a self signed cert then pass over to a host called `nginx`

## Usage

With `docker-compose.yml` add it as a service alongisde your `nginx` service

_**Example:** Trimmed docker-compose.yml file_
```
...
caddy:
    image: wearejh/caddy
    links:
        - nginx
    ports:
        - "80:80"
        - "443:443"
...
```

## Customising ...

If you'd like to customise the Caddyfile, maybe to change the service hostnames, add extra functionality etc then you can do this by mounting your custom Caddyfile via a single file volume. 

_**Example:** Trimmed docker-compose.yml file_
```
...
caddy:
    image: wearejh/caddy
    volumes:
        - path/to/local/Caddyfile:/etc/Caddyfile
    links:
        - nginx
    ports:
        - "80:80"
        - "443:443"
...
```
