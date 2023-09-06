# Traefik v2 HTTPS (SSL) on localhost

This repo is a minimal template to use Traefik v2 on localhost with HTTPS support.


Next, go to the traefik folder (`cd traefik`) and generate certificates using [mkcert](https://github.com/FiloSottile/mkcert) :

```bash
# If it's the firt install of mkcert, run
mkcert -install

# Generate certificate for domain "docker.localhost", "domain.local" and their sub-domains
mkcert -cert-file certs/local-cert.pem -key-file certs/local-key.pem "docker.localhost" "*.docker.localhost" "domain.local" "*.domain.local"
```


Create networks that will be used by Traefik:

```bash
docker network create proxy
``` 


Now, start containers with : 

```bash
# Start Traefik
docker-compose -f docker-compose.yml up -d
# Start Portainer
docker-compose -f docker-portainer.yml up -d
# Start pgAdmin 4
docker-compose -f docker-pgadmin4.yml up -d
# Start Redis Stack
docker-compose -f docker-redis.yml up -d
```



You can now go to your browser at [portainer.docker.localhost](https://portainer.docker.localhost), enjoy :rocket: !

*Note: you can access to Træfik dashboard at: [traefik.docker.localhost](https://traefik.docker.localhost)*

Don't forget that you can also map TCP and UDP through Træfik.