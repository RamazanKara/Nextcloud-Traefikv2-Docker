# Nextcloud-Traefikv2-Docker-Compose
Docker-Compose Scripts for securely running Nextcloud on Public with Traefikv2 and Docker (Compose)


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

get the Docker subnet where traefik and nextcloud is deployed to ```(IPAddress and IPPrefixLen)```

go to ```nextcloud/app/config/config.php ```

and enter 

```'trusted_proxies' => 'Subnet/Prefix'```, e.g. ```'172.17.0.2/16'```

also change ```overwrite.cli.url``` to your URL:

```'overwrite.cli.url' => 'https://<yourdomain>',```
and finally add these 2 entries with your domain:
```
  'overwriteprotocol' => 'https',
  'overwritehost' => '<yourdomain>',
```  

## Do I need to thing about something else to keep my Next Cloud Safe?

- If you have a static IP you will get lots of scans and passwort tries. Implement TOTP Authenticator or Yubi Key (Apps are on Nextcloud Repo)
- Use fail2ban (I will make a separate Repo for that) and ban these fools for messing with your stuff
- Deploy this Stuff on a separate Linux User 
- Dont disable SELinux you noob.


  
