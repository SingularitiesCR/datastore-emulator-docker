# Google Cloud Datastore Emulator

A [Google Cloud Datastore Emulator](https://cloud.google.com/datastore/docs/tools/datastore-emulator/) container image. The image is meant to be used for creating an standalone emulator for testing.

- [`171.0` (Dockerfile)](https://github.com/SingularitiesCR/datastore-emulator-docker/blob/171.0/Dockerfile)

## Custom commands

This image contains a script named `start-datastore` (included in the PATH). This script is used to initialize the Datastore emulator.

### Starting an emulator

By default, the following command is called:

```sh
start-datastore
```

## Creating a Datastore emulator with Docker Compose

The easiest way to create an emulator with this image is by using [Docker Compose](https://docs.docker.com/compose). The following snippet can be used as a `docker-compose.yml` for a datastore emulator:

```YAML
version: "2"

services:
  datastore:
    image: singularities/datastore
    environment:
      - DATASTORE_PROJECT_ID=project-test
      - DATASTORE_LISTEN_ADDRESS=0.0.0.0:8081
    ports:
      - "8081:8081"
```

### Persistence

The image has a volume mounted at `/opt/data`. To maintain states between restarts, mount a volume at this location.
