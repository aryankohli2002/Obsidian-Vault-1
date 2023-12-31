The continuous integration setup consists of:

- running unit tests
    
- building the Docker image that we use to build our service
    
- running the build container and compiling our service
    
- building the Docker image that we run and deploy
    
- pushing the final image to a Docker registry


Continuous Integration (CI) is the part of the development process where you're looking to get your code changes merged with the main branch of the project. At this point, development teams run tests and builds to vet that the code changes don't cause any unwanted or unexpected behaviors.

![Git branches about to get merged](https://docs.docker.com/build/ci/images/continuous-integration.svg)

There are several uses for Docker at this stage of development, even if you don't end up packaging your application as a container image.

## [Docker as a build environment](https://docs.docker.com/build/ci/#docker-as-a-build-environment)

Containers are reproducible, isolated environments that yield predictable results. Building and testing your application in a Docker container makes it easier to prevent unexpected behaviors from occurring. Using a Dockerfile, you define the exact requirements for the build environment, including programming runtimes, operating system, binaries, and more.

Using Docker to manage your build environment also eases maintenance. For example, updating to a new version of a programming runtime can be as simple as changing a tag or digest in a Dockerfile. No need to SSH into a pet VM to manually reinstall a newer version and update the related configuration files.

Additionally, just as you expect third-party open source packages to be secure, the same should go for your build environment. You can scan and index a builder image, just like you would for any other containerized application.

The following links provide instructions for how you can get started using Docker for building your applications in CI:

- [GitHub Actionsopen_in_new](https://docs.github.com/en/actions/creating-actions/creating-a-docker-container-action)
- [GitLabopen_in_new](https://docs.gitlab.com/runner/executors/docker.html)
- [Circle CIopen_in_new](https://circleci.com/docs/using-docker/)
- [Renderopen_in_new](https://render.com/docs/docker)

### [Docker in Docker](https://docs.docker.com/build/ci/#docker-in-docker)

You can also use a Dockerized build environment to build container images using Docker. That is, your build environment runs inside a container which itself is equipped to run Docker builds. This method is referred to as "Docker in Docker".

Docker provides an official [Docker imageopen_in_new](https://hub.docker.com/_/docker) that you can use for this purpose.

## [What's next](https://docs.docker.com/build/ci/#whats-next)

Docker maintains a set of official GitHub Actions that you can use to build, annotate, and push container images on the GitHub Actions platform. See [Introduction to GitHub Actions](https://docs.docker.com/build/ci/github-actions/) to learn more and get started.