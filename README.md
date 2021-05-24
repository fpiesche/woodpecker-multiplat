# Multi-Arch Woodpecker Builds

This repo is set up to automate creating multi-arch Docker images (armv6, armv7, arm64, amd64) for
the [Woodpecker CI system](https://woodpecker.laszlo.cloud/), a free fork of [Drone](https://drone.io/).

The submodule for Woodpecker is primarily here for future monitoring for updates via Dependabot;
the actual meat of this project is just the three Dockerfiles and the GitHub Actions workflow.

`Dockerfile.build` is a Dockerfile that will run Woodpecker's unit tests and build the server and agent
executables inside a Docker container, so that multi-arch builds can be created using `docker buildx`;
the `Dockerfile.agent` and `Dockerfile.server` files will then copy the executables out of the relevant
containers and into new Alpine Linux containers to minimise final image size.

The finished images are available on Docker Hub at
[florianpiesche/woodpecker-server](https://hub.docker.com/r/florianpiesche/woodpecker-server) and
[florianpiesche/woodpecker-agent](https://hub.docker.com/r/florianpiesche/woodpecker-agent) respectively.