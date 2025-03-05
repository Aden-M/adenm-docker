**Public Repository for Docker Compose Containers**
This repository contains my publicly available Docker Compose stack, designed to provide scalable TCP routing and TLS connections for various backend services. The stack leverages Traefik’s dynamic container labels and static TCP routing, with Authentik (replacing Authelia) as the SSO middleware.

**Included Containers and Their Functions:**

**Traefik** – A highly flexible and scalable reverse proxy container, offering extensive SSL termination for Docker containers and TCP services. It also supports middleware integration for authentication.

**Authentik** – An enterprise-grade Single Sign-On (SSO) service, enabling scalable user enrollment, multiple authentication providers (e.g., OAuth, proxies), and direct backend integration for secure applications.

**Authelia** – A lightweight SSO provider that is easy to deploy and scale. It operates as a standalone container and can be integrated as either a static middleware or a dynamic label. (Currently being phased out in favor of Authentik.)

**Prometheus** – A monitoring and data collection container that gathers system metrics through cAdvisor and Node Exporter. In this setup, it primarily monitors Traefik.

**Grafana** – A data visualization tool that connects to Prometheus to provide insights into Traefik’s performance and container activity.

**Additional Containers (Work in Progress):**
- Chronograf, InfluxDB, and n8n have not yet been fully configured for functionality.
- Authelia is currently being replaced with Authentik.
- Some services may require additional research or troubleshooting to ensure full functionality.
- Guides and documentation are available for all of these services.
