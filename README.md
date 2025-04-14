![Docker Image CI](https://github.com/gringolito/docker-webnut/workflows/Docker%20Image%20CI/badge.svg)


Difference from [edgd1er's](https://github.com/edgd1er/docker-webnut) version:
- Using [jasonhensler's](https://github.com/jasonhensler/webNUT) fork of webNUT with added progress bars to the current Load and battery level columns

# docker-webNUT

webNUT (UPS network monitoring web ui) dockerized.

More infos on webNUT:  https://github.com/jasonhensler/webNUT

Set the following environment variables:

**UPS_HOST**    with NUT server host IP  *(default: 127.0.0.1)*

**UPS_PORT**	  with NUT server port  *(default: 3493)*

**UPS_USER**    with NUT server username   *(default: monuser)*

**UPS_PASSWORD**     with NUT server  password   *(default: secret)*

Run with:

> docker run -e UPS_HOST="10.11.12.13"  -e UPS_PORT="3493" -e UPS_USER="monuser" -e UPS_PASSWORD="secret" -p 6543:6543 --mount source=config,target=/config gringolito/webnut:latest

# Docker-compose

```
services:
  webnut:
    image: gringolito/webnut:latest
    restart: always
    environment:
      UPS_HOST: "10.11.12.13"
      UPS_PORT: "3493"
      UPS_USER: "monuser"
      UPS_PASSWORD: "secret"
    ports:
     - "6543:6543"
    volumes:
      - config:/config
volumes:
  config:
```