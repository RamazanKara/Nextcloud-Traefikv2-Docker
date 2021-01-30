# Nextcloud-Traefikv2-Docker
Docker-Compose Scripts for running Nextcloud on Public with Traefikv2 and Docker (Compose)


## What does this deploy?

- Nextcloud with the correct labels to run on traefik on a separate network
- Cron to schedule Nextcloud Tasks
- MariaDB as the Database Backend
- NginX as the Webserver
- Redis for fast Cache

## Requirements

- Traefik with working TLS resolver needs to be deployed
- Change the external network to the one your traefik is in
- If your traefik has catch all rules for http, remove all the http labels.

