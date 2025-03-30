<p align="center">
  <img src="docs/images/diun_logo.png" alt="Diun Logo" height="200"/>
</p>

# <img src="docs/images/t9Logo.png" height="25"> Tyzen9's Diun Container
This container uses Diun to create notifications when a Docker image is updated on a Docker registry.
Visit the [Diun webpage](https://crazymax.dev/diun/) to learn more about this application.

## Prerequisites
Install [Docker Engine](https://docs.docker.com/get-docker/) or [Docker Desktop](https://docs.docker.com/desktop/) if you require the Docker user interface.  In production it's generally best to use [Docker Engine](https://docs.docker.com/get-docker/) on a Linux host operating system, and a lightweight service delivery platform designed for managing containerized applications such as [Portainer](https://www.portainer.io/)

This documentation assumes you have a working knowledge of [Docker](https://www.docker.com/), and [Pushover](https://pushover.net/api).

## Configuration
This `docker-compose` implementation is configured using the `environment` section of the `docker-compose.yaml` file.  
The config options are documented on the [Diun Configuration](https://crazymax.dev/diun/config/) page.

### Pushover
Be sure to set the `DIUN_NOTIF_PUSHOVER_TOKEN` and `DIUN_NOTIF_PUSHOVER_RECIPIENT` keys appropriately when deploying this container.

## Start the Container (Development/Testing)
1. Clone this repository: `git clone https://github.com/tyzen9/docker-diun.git`
1. Set the configuration options as desired in the `docker-compose.yaml` file.
1. Navigate to the project's root directory and run the following command:

```
docker compose up
```

## Testing Notifications
Test the configured notification using this command on the docker host machine:

```
docker exec [container-name] diun notif test
```

## Production Deployment using Portainer
I use [Portainer](https://www.portainer.io/) to manage and orchestrate my Docker resources in my Production environments. To deploy this into your Portainer environment:

1. In Portainer, choose the Environment to deploy to
1. In the left menu choose Stacks, then click `+ Add stack`
1. Choose `Repository` and fill in the required fields (don't forget name at the top)
1. At the bottom, there is an option to `Load variables from .env file`. Click this button and provide the prepared `.env` file for this environment.
1. Click `Deploy the stack`

Once successfully deployed, it would be a good idea to test the notification (See above) as there is no Diun dashboard.