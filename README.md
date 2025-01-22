This is the current public repository for all of my docker compose containers.
This is an integrated and functional stack and currently aims to provide TCP routing and TLS connections
for any number of scalable backend services by leveraging Traefik dynamic container labels and static TCP 
routing, with Authelia as a SSO middleware.

The included containers, and a short summary of their function are as follows:

Traefik - This is one of the best reverse proxy docker containers, it is incredibly flexible and scalable, and provides convenient and extensive SSL termination for docker containers, services running over TCP, and also allows for middlewares to add integrated authentication in front of containers.

Authelia - This is a simple SSO provider that is convenient to set up and is easy to scale, it runs as its own container and can be added as a static middleware or dynamic label.

Prometheus - This is a data collection container and collects data regarding the host system or docker environment through cadvisor and nodeexporter. Currently, it is set up to monitor Traefik only.

Grafana - This is a data visualization service and runs as a docker container, it can integrate with a variety of data providers. In this repository it connects with Prometheus to provide data regarding the Traefik service and container.

Other containers:
I have not yet configured chronograf, influxDB, or n8n to a functional and useful state.



