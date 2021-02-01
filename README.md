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


## Security

The Settings net you an A+ Rating if you use a host prefix and not deploy it on root Domain (Root Domain nets you an A rating)



## Further Settings:


### trusted Proxy: 
```
docker inspect proxy
```

get the subnet where traefik and nextcloud is from there ```(IPAddress and IPPrefixLen=```

go to ```nextcloud/app/config/config.php ```

and enter 

```'trusted_proxies' => 'Subnet/Prefix'```, e.g. '172.17.0.2/16'

also change ```overwrite.cli.url``` to your URL:

```'overwrite.cli.url' => 'https://<yourdomain>',```
and finally add these 2 entries with your domain:
```
  'overwriteprotocol' => 'https',
  'overwritehost' => '<yourdomain>',
```  
  
