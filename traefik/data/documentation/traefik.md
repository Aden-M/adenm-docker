**Traefik Installation Guide**

Minimum Requirements:
1. Docker with the Docker Compose plugin.
2. A user with membership in the Docker group .
3. Outbound internet access (The machine needs to be able to access the internet to pull certificates, install docker image.)
4. Port 443 avaliable (only on the machine which runs Traefik, no port forwarding needed for local service.)
5. A DNS Server or Manual Access to /etc/hosts.
6. A cloudflare account with atleast one registered Domain Name.

Installation: Initial Setup:
1. Create a cloudflare API token with Zone:Zone Settings:Read, Zone:Zone:Edit, Zone:DNS:Edit.
2. Copy out the traefik folder from the github repository into /srv/docker/ or wherever else you you want to be your docker compose directory.
3. Create secrets.env under the data folder, create the entry CF_DNS_API_TOKEN={$COPIED API TOKEN}.
4. Create acme.json and apply chmod 600 to acme.json.
5. Edit the docker-compose.yml to match your registered Domain Name which is also on the Cloudflare Zone for the API token.
6. Change the email in traefik.yml
7. Run the container.
