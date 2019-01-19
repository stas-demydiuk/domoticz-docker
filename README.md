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