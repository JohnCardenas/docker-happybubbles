## Introduction
Easily run your HappyBubbles Presence Server in Docker, specifying an MQTT server to connect to from environment variables.

## Supported Tags
* `1.6.2`, `latest`

At this time, only an amd64 image is built automatically. However, if you would like to build an image suitable for an ARM device, please see **Building the Image**, below.

## Usage
### Simple Command Line
The following command will start the server using the default MQTT parameters:
>`docker run -it --name happybubbles-presence -p 5555:5555 johncardenas/happybubbles:latest`

### Docker-Compose
Create a `docker-compose.yml` file and add the following:
```
happybubbles-presence:
   image: "johncardenas/happybubbles-presence:latest-amd64"
   restart: always
   environment:
      MQTT_HOST: "localhost:1883"
      MQTT_USERNAME: "none"
      MQTT_PASSWORD: "none"
   ports:
      - 5555
```

## Environment Variables
* `MQTT_HOST`: Specifies the MQTT server to connect to, including the port. Defaults to `localhost:1883`.
* `MQTT_USERNAME`: Specifies the user name to connect to the MQTT server with. Defaults to `none`.
* `MQTT_PASSWORD`: Specifies the password to connect to the MQTT server with. Defaults to `none`.
* `MQTT_CLIENT_ID`: Specifies the client ID to connect as. Defaults to `happy-bubbles-presence-detector`.

## Parameters
* `-p 5555` - port of the web interface

## Building the Image
If you would like to make changes to the base Dockerfile, check out the GitHub repository and run this command to build it:

>`docker build -t happybubbles-presence ./1.6.2/amd64`

You can also build an arm32v7 image suitable for use on a Raspberry Pi 2+ with the following command:

>`docker build -t happybubbles-presence ./1.6.2/arm32v7`