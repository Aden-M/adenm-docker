**Traefik Installation Guide**

**Minimum Requirements:**
1. Docker with the Docker Compose plugin.
2. A user with membership in the Docker group .
3. Outbound internet access (The machine needs to be able to access the internet to pull certificates, install docker image.)
4. Port 443 avaliable (only on the machine which runs Traefik, no port forwarding needed for local service.)
5. A DNS Server or Manual Access to /etc/hosts.
6. A cloudflare account with atleast one registered Domain Name.

**Installation: Setup Overview:**
1. Create a cloudflare API token with Zone:Zone Settings:Read, Zone:Zone:Edit, Zone:DNS:Edit.
2. Copy out the traefik folder from the github repository into /srv/docker/ or wherever else you you want to be your docker compose directory.
3. Create secrets.env under the data folder, create the entry CF_DNS_API_TOKEN={$COPIED API TOKEN}.
4. Create acme.json and apply chmod 600 to acme.json.
5. Edit the docker-compose.yml to match your registered Domain Name which is also on the Cloudflare Zone for the API token.
6. Change the email in traefik.yml
7. Run the container.

**Installation: Detailed Setup:**
1. Clone the repository and checkout the traefik-overhaul branch, move the traefik folder, create acme.json, create secrets.env:
```bash
git clone https://github.com/adenm/adenm-docker
cd adenm-docker
git checkout traefik-overhaul
cp -r traefik-overhaul /srv/docker/
cd /srv/docker/traefik/data
touch acme.json && chmod 600 acme.json
touch secrets.env
```
2. Modify traefik.yml with your own email:

```bash
nano /srv/docker/traefik/data/traefik.yml
```

```yaml
certificatesResolvers:
  cloudflare:
    acme:
      email: {$youremail.email.site}
      storage: acme.json
      dnsChallenge:
        provider: cloudflare
        #disablePropagationCheck: true # uncomment this if you have issues pulling certificates through cloudflare, By setting this flag to true disables the need to wait for the propagation of the TXT record to all authoritative name servers.
        resolvers:
          - "1.1.1.1:53"
          - "1.0.0.1:53"
```

3. Enter your API key into secrets.env:

```bash
nano /srv/docker/traefik/data/secrets.env
```

```env
CF_DNS_API_TOKEN = {$Cloudflare DNS API Token}
```

4. Set your domain name for certificates and desired subdomain for Traefik:

```bash
nano /srv/docker/traefik/docker-compose.yml
```

