Domoticz
======

Domoticz - http://www.domoticz.com/

Docker containers with official Domoticz beta builds

[![](https://images.microbadger.com/badges/image/demydiuk/domoticz.svg)](https://microbadger.com/images/demydiuk/domoticz "Get your own image badge on microbadger.com")
[![](https://images.microbadger.com/badges/version/demydiuk/domoticz.svg)](https://microbadger.com/images/demydiuk/domoticz "Get your own version badge on microbadger.com")
[![](https://images.microbadger.com/badges/license/demydiuk/domoticz.svg)](https://microbadger.com/images/demydiuk/domoticz "Get your own license badge on microbadger.com")

## How to use

**Pull image**

```
docker pull demydiuk/domoticz:$VERSION

```

**Run container**

```
docker run -d \
    -p 8080:8080 \
    -v <path for config files>:/config \
    -v /etc/localtime:/etc/localtime:ro \
    --device=<device_id> \
    --name=<container name> \ 
    demydiuk/domoticz:$VERSION
```

Please replace all user variables in the above command defined by <> with the correct values (you can have several USB devices attached, just add other `--device=<device_id>`).

**Access Domoticz**

```
http://<host ip>:8080
```

8080 can be another port (you change `-p 8080:8080` to `-p 8081:8080` to have 8081 out of the container for example).

### Usage with docker-compose

```yaml
version: '3.3'

services:
  domoticz:
    image: demydiuk/domoticz:latest
    container_name: domoticz
    # Pass devices to container
    # devices:
    #   - "dev/serial/by-id/usb-0658_0200-if00:/dev/ttyACM0"

    volumes:
      - "/etc/localtime:/etc/localtime:ro"
    # Additional volumes that might be useful:
    #  - "./config:/config"
    #  - "./plugins:/opt/domoticz/plugins"

    # You can add or overwrite default Domoticz args (-www 8080)
    # command: -www 80

    # You can activate SSL support using -sslwww <PORT> param
    # command: -www 8080 -sslwww 8443

    # Host mode can be useful in case you have a hardware which requires host network access
    # network_mode: "host"

    restart: unless-stopped
```

