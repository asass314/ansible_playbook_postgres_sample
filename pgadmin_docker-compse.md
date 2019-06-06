#
# *** pgadmin4 - Admin Tool for postgresql ***
#  https://www.pgadmin.org/download
#  CentOS7
#


mkdir -p /var/lib/pgadmin/docker

docker-compose.yml

```yaml
version: '3'  
services:
   pgadmin4:
     image: dpage/pgadmin4
     container_name: pgadmin4
     ports:
       - "443:443"
     volumes:
       - /var/lib/pgadmin/docker:/var/lib/pgadmin
       - /etc/pki/tls/certs/<your>.crt:/certs/server.cert
       - /etc/pki/tls/private/<your>.key:/certs/server.key
       - /tmp/servers.json:/servers.json
     environment:
       - PGADMIN_DEFAULT_EMAIL=admin@domain.com
       - PGADMIN_DEFAULT_PASSWORD=admin123
       - PGADMIN_ENABLE_TLS=True
     network_mode: host
```

docker-compose up -d
docker-compose down
https://pgadminhost:443
