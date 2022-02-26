
# Run keycloak on synology nas

## requirements

* synology nas that runs docker
* a local dns server to assign an additional hostname to the nas (I'm running [pi-hole](https://pi-hole.net/))

## preparation

* create an DNS entry for keycloak (e.g. `keycloak-nas.home`)
* edit `variables.env` and `secrets.env`, add missing information (see comments in files)
* `cp variables.env .env`

## start container

* `docker-compose up -d`

## configuration of synology

* see [synologsy forum](https://www.synoforum.com/resources/synology-reverse-proxy.12/) for how to configure the reverse proxy
   * Source:
      * protocol: https
      * hostname: the keycloak hostname (e.g. `keycloak-nas.home`)
      * port: 443
   * Destination:
      * protocol: https
      * hostname: localhost
      * port: 9443

## Links

* [google integration](http://www.mastertheboss.com/keycloak/google-social-login-with-keycloak/)