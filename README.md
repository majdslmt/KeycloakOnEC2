# KeycloakOnEC2

sudo docker run -d \
  --name keycloak-prod \
  -v /home/ubuntu/cert:/certificates \
  -v /home/ubuntu/jar/custom-event-listener.jar:/opt/keycloak/providers/custom-event-listener.jar \
  -p 443:8443 \
  -e KEYCLOAK_ADMIN=admin \
  -e KEYCLOAK_ADMIN_PASSWORD=password \
  quay.io/keycloak/keycloak:latest \
  start \
  --features=token-exchange \
  --https-certificate-file=/certificates/cert.crt \
  --https-certificate-key-file=/certificates/key.pem \
  --hostname=host \
  --proxy=edge \
  --db=postgres \
  --db-url-host=rds url\
  --db-url-port=5432 \
  --db-url-database=Keycloak \
  --db-username=dbadmin \
  --db-password=password
