
The **Docker architecture** defines all the components, such as the docker daemon, the docker client or the docker registries, and their inter-connections upon which Docker is built.

Scrolling down you will learn how it actually looks and works inside Docker and the different components that make use of it.

## How does it work?

The idea behind a Docker container is that it is a self-contained unit of software that can move to and run on any server that is configured to run containers. It could be a laptop, an EC2 instance, or a bare-metal server in a private data center.

At the heart of Docker’s architecture is the Docker daemon, which provides a layer that abstracts the OS specifics from the user while giving that user the ability to handle all aspects of the container’s lifecycle (from build to install to run to clean up) in an easy-to-use and repeatable way. Containers have become very popular because of the benefits provided by this abstraction.

Regardless of whether Docker is being used on Linux or Windows, you can use the exact same commands to begin working with your application. The following image illustrates Docker’s architecture:

[![](https://sysdig.com/wp-content/uploads/image2-49.png "image_tooltip")](https://sysdig.com/wp-content/uploads/image2-49.png)

Virtualization also became popular due to its ability to isolate workloads, move them around, and only provide as many resources as they need. However, containers do this much more efficiently.

A virtual machine instance needs an entire operating system to be in place and running, which adds a lot of overhead and increases the number of variables that need to be managed between what a developer builds and what is running in production.

In contrast, a container only needs a single instance of an operating system in place so it can run more instances on the same servers. The following diagram shows the difference between running Docker containers and virtual machines:

![](https://sysdig.com/wp-content/uploads/image3-38-1170x479.png "image_tooltip")

## Docker Engine

Docker Engine is the core of the Docker platform, and it facilitates all aspects of a container lifecycle. It has three primary components: a command-line interface, a REST API, and the daemon (which takes care of getting the work done).

From the client side, the Docker CLI is probably still the most widely-used client option in the Docker ecosystem. It is used extensively in the test and development stages of the application lifecycle. An increasing number of tools now provide a graphical user interface that leverages the REST API to create a better user experience – especially for novice users.

These include first-party tools like Docker Desktop and integrations with third-party tools like the Docker plugin for Visual Studio Code.

The types of commands that can be called via the CLI or API vary from configuring the host network to building a container to simply running a container.The other side of Docker Engine is the daemon that runs on the host and takes care of all the OS-specific commands like managing the network and storage that containers are using.

For the actual runtime layer, the daemon leverages a container runtime that knows how to interact with the host operating system to unpack, apply security and quota policies, start, stop, and clean up the actual container instances.

The default container runtime used by Docker Engine is _containerd_, although there are other available options that some users prefer based on their exact scenario.

## Docker Registry

One of the big selling points of containers is that they are transportable across servers. Docker Registry is the self-managed, open-source solution that is provided by Docker to facilitate this exact requirement. A container registry stores the individual container images after they are built as well as any related metadata (like versions, tags, creation dates, authors, and even security scan results).

For a managed offering that runs in the cloud, Docker offers Docker Hub (which has thousands of pre-built images from vendors and the community already available for use).

The general workflow for using Docker Registry or Docker Hub is to use Docker Engine to:

- Build the container image.
- Push it to the registry of your choice from the build machine.
- Tell Docker to pull the exact image you want to use on the consuming machines.
- And then finally run the image.

## Docker Objects

### **Docker Images**

The build process for Docker results in the creation of a Docker image. This is the binary that is moved to and from registries, used as a base (to build other container images on top), and used by the container runtime engine to build an actual running container instance.

Docker images are built in layers. Each layer extends what is in the layer before it to work towards fulfilling all the dependencies any given application will have when its layer is eventually added to the container.

Having this layered approach allows people to focus on what they do best, streamline the transportation of Docker images, and save developers time by having an inventory of images available to use as a base for their applications.

For example, an organization could standardize a container base image that includes the core libraries required plus certificates that are commonly used across their application portfolio in one layer. The next step would be to use that base image as the first layer and create a second layer for Java, Go, or Node, having developers consume that language-specific instance.

This allows the base image or the language layer to be updated for critical CVEs and other defects, while developers can update at their convenience by simply changing the reference they have to the version they will include in their build.

An additional benefit of the layers is that they are only uploaded to registries or downloaded to host machines if they do not already exist.

So if an organization has 10 containerized applications running Node on a host, there will only be one copy of both the base image layer and the Node layer. This can save a lot of downloading time plus reduce the amount of disk space required.

### **Docker Container Instances**

Once a Docker image is downloaded to a host and started, the running copy is referred to as a container instance. This can be done with a single command line that looks like this:

`# this will download the latest version of the nginx # container image from the default registry and start it $ docker run nginx:latest`Code language: Shell Session (shell)

### **Docker Volumes**

Volumes are managed by Docker to allow data to be written outside the container instance, which allows it to persist outside of the actual container instance’s lifecycle.

This option is what makes containers capable of handling persistent data, which allows databases and other data-driven applications to run inside Docker without worrying about data loss. Storage drivers can take advantage of cloud, network-attached, and other high-performance storage subsystems while providing the best performance characteristics to support an application’s needs.

### **Docker Networks**

Docker supports multiple types of networks that will accommodate most potential needs of containers. It is based on a pluggable architecture, so third-party options can be used if none of the included options will work.

- Bridge networking is the default plugin that is set up for networking. It allows containers to have their own isolated network spaces and interact based on the routing that is configured on the Docker host.
- Host-based networking shares the same network stack as the host operating system. This provides no isolation between the host and any containers that are running, so things like port conflicts need to be considered carefully.
- Overlay networks allow seamless (and optionally encrypted) network connectivity between multiple containerized applications running in a swarm across multiple hosts.
- MacVLAN and IPvlan are available and provide access to lower levels of the networking stack (at the Layer 1 and Layer 2 levels). This acts more like the networking that a virtual machine would offer and is usually chosen based on a specific need of an application.
- Finally, there’s the option to tell a container to use _none_, which obviously disables all network capabilities inside the container instance.

## Advanced Docker Architecture

### **Docker Orchestration**

Container orchestration is a key capability that allows containers to scale up and down to handle peaks and valleys in demand, as well as automatically recover on a new node if the node they are running on crashes.

Essentially, container orchestration is a management activity that involves playing Tetris with all of the containers in a Kubernetes cluster (or a Docker swarm) to make sure they are running within their defined parameters.

### **Docker in Production**

Docker (the company) has moved its focus toward providing the best possible experience for developers, while another company, Mirantis, acquired Docker’s enterprise systems.

This doesn’t mean that you can’t run Docker in production (Docker still has Swarm capabilities), but there are other solutions (primarily Kubernetes) that have become more widely used within the industry to run Docker containers in multi-server production environments.

### **Scaling and Orchestrating Docker Containers**

Thanks to Docker’s commitment to working with standards bodies to ensure consistency within the industry, organizations can use Docker tools where they are best to build, test, and publish container images, then leverage the strengths of Kubernetes and its ecosystem to run those Docker images essentially anywhere.

Regardless of whether it is on a three-node cluster running 5G radios at a remote site or an application running across thousands of nodes within a Kubernetes cluster supporting a large e-commerce giant, all those instances are running the exact same image which was built by the developer and verified by QA.