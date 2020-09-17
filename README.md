# Traefik v2 HTTPS (SSL) on localhost

This repo is a minimal template to use Traefik v2 on localhost with HTTPS support.



To get started, just clone this repo:

```
git clone https://github.com/Heziode/traefik-v2-https-ssl-localhost.git
```



Next, go to the root of the repo (`cd traefik-v2-https-ssl-localhost`) and generate certificates using [mkcert](https://github.com/FiloSottile/mkcert) :

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
# Start "whoami" example
docker-compose -f whoami.yml up
```



You can now go to your browser at [whoami.docker.localhost](https://whoami.docker.localhost), enjoy :rocket: !

*Note: you can access to Træfik dashboard at: [traefik.docker.localhost](https://traefik.docker.localhost)*

Don't forget that you can also map TCP and UDP through Træfik.

## Code of Conduct

This project adheres to the [Contributor Covenant](https://www.contributor-covenant.org/). By participating in this project you agree to abide by its terms.



# License

MIT
