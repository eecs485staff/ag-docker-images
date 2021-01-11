# ag-docker-images

![upload-ag-images](https://github.com/eecs485staff/ag-docker-images/workflows/upload-ag-images/badge.svg)

This repository houses the Docker images that are used by the EECS 485 Autograder sandbox environments. More information about the custom sandbox images and how to configure them on the Autograder can be found [here](https://eecs-autograder.github.io/autograder.io/topics/custom_sandbox_images.html).

The EECS 485 AG images are publicly hosted on [Docker Hub](https://hub.docker.com/) and inherit from the official [eecs-autograder Ubuntu base image](https://github.com/eecs-autograder/base-docker-images). These images are publicly available to allow IAs and GSIs to easily and quickly [debug student submissions in a local Docker environment](https://github.com/eecs485staff/p1-insta485-static/blob/master/README_docker.md).

## Automated Image Builds and Uploads

Images are built and uploaded to Docker Hub automatically using a [GitHub actions workflow](https://github.com/eecs485staff/ag-docker-images/actions?query=workflow%3Aupload-ag-images) that will run whenever code is pushed or merged into the master branch. Any change, whether a dependency upgrade or Dockerfile modification, will prompt some or all of the images to be rebuilt and uploaded. Docker Hub uploads are managed by the [eecs485dockerbot](https://hub.docker.com/u/eecs485dockerbot) service user. Sensitive information, like eecs485dockerbot's personal access token, are stored in this [repository's secrets](https://github.com/eecs485staff/ag-docker-images/settings/secrets) for use in the GitHub actions workflow.

## Manually Building Images

When updating the Docker images, it is helpful to build them locally for testing purpose. You can build the images locally with the following commands:

```bash
$ pwd
/Users/jadchaar/Development/eecs485/ag-docker-images
$ docker build base -t eecs485/ag_base:latest # Build and tag the base image
$ docker build p1 -t eecs485/p1:latest # Build and tag the P1 image
$ docker build p2 -t eecs485/p2:latest # Build and tag the P2 image
$ docker build p3 -t eecs485/p3:latest # Build and tag the P3 image
$ docker build p4 -t eecs485/p4:latest # Build and tag the P4 image
$ docker build p5 -t eecs485/p5:latest # Build and tag the P5 image
```

## Docker Hub Images

- [Base Images](https://hub.docker.com/repository/docker/eecs485/ag_base)
- [P1 Images](https://hub.docker.com/repository/docker/eecs485/p1)
- [P2 Images](https://hub.docker.com/repository/docker/eecs485/p2)
- [P3 Images](https://hub.docker.com/repository/docker/eecs485/p3)
- [P4 Images](https://hub.docker.com/repository/docker/eecs485/p4)
- [P5 Images](https://hub.docker.com/repository/docker/eecs485/p5)
