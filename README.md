**Public Repository for Docker Compose Containers**
This feature branch of the adenm-docker repository contains a drag-and-drop docker-compose.yml setup for gitlab CE.
Traefik is a hard requirement for functionality. This setup ensures secure SSL connection to the Gitlab CE frontend
using Let's Encrypt certificates from Traefik. 

Presuming that a working Traefik configuration is already deployed (on the same host and on the proxy network), 
the only requirement for functionality is a DNS rule pointing the correct subdomain to the IP of the traefik host.

**Included Containers and Their Functions:**

**Gitlab CE (ARM64)** – A selfhosted alternative to Github and Gitlab offering reduced cost by utilizing on 
premises and fixed cost equipment.
This image and docker compose are specifically designed for use on ARM64 hosts. This docker-compose has been tested
on a Rasberry Pi5 8gb and runs exceptionally well.

