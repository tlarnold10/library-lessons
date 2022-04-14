# Docker Deep Dive: Zero to Docker in a single book
__By: Nigel Poulton__
## Lessons Learned:
- When you install Docker, you get two major components: the Docker client the Docker daemon (sometimes called the “Docker engine”) The daemon implements the runtime, API and everything else required to run Docker.
- Docker image as an object that contains an OS filesystem, an application, and all application dependencies. If you work in operations, it’s like a virtual machine template.
- manifest list is exactly what it sounds like: a list of architectures supported by a particular image tag.
- At a high level, hypervisors perform hardware virtualization — they carve up physical hardware resources into virtual versions called VMs. On the other hand, containers perform OS virtualization — they carve OS resources into virtual versions called containers.
- This is because a container cannot exist without it’s designated main process. This is true of Linux and Windows containers — killing the main process in the container will kill the container.
- Some instructions create new layers, whereas others just add metadata to the image config file. Examples of instructions that create new layers are FROM, RUN, and COPY. Examples that create metadata include EXPOSE, WORKDIR, ENV, and ENTRYPOINT. The basic premise is this — if an instruction is adding content such as files and programs to the image, it will create a new layer. If it is adding instructions on how to build the image and run the application, it will create metadata.
- A common example is that every RUN instruction adds a new layer. As a result, it’s usually considered a best practice to include multiple commands as part of a single RUN instruction — all glued together with double-ampersands (&&) and backslash (\) line-breaks. While this isn’t rocket science, it requires time and discipline.
- Multi-stage builds have a single Dockerfile containing multiple FROM instructions. Each FROM instruction is a new build stage that can easily COPY artefacts from previous stages.
- Try and write them in a way that places instructions that are likely to invalidate the cache towards the end of the Dockerfile.
- build: . This tells Docker to build a new image using the instructions in the Dockerfile in the current directory (.). The newly built image will be used in a later step to create the container for this service.
- Docker Compose is a Python application that you install on top of the Docker Engine.
- clustering front, a swarm consists of one or more Docker nodes. These can be physical servers, VMs, Raspberry Pi’s, or cloud instances. The only requirement is that all nodes have Docker installed and can communicate over reliable networks.
- Technically speaking, swarm implements a form of active-passive multi-manager HA. This means that although you have multiple managers, only one of them is active at any given moment. This active manager is called the “leader”, and the leader is the only one that will ever issue live commands against the swarm. So, it’s only ever the leader that changes the config, or issues tasks to workers. If a follower manager (passive) receives commands for the swarm, it proxies them across to the leader.
- On the topic of HA, the following two best practices apply: Deploy an odd number of managers. Don’t deploy too many managers (3 or 5 is recommended)
- Docker networking is based on an open-source pluggable architecture called the Container Network Model (CNM).
- At the highest level, Docker networking comprises three major components: The Container Network Model (CNM) libnetwork Drivers The CNM is the design specification. It outlines the fundamental building blocks of a Docker network. libnetwork is a real-world implementation of the CNM, and is used by Docker. It’s written in Go, and implements the core components outlined in the CNM. Drivers extend the model by implementing specific network topologies such as VXLAN overlay networks.
- Containers are designed to be immutable. This is just a buzzword that means read-only — it’s a best practice not to change the configuration of a container after it’s deployed. If something breaks or you need to change something, you should create a new container with the fixes/updates and deploy it in place of the old container. You shouldn’t log into a running container and make configuration changes!
- At a high-level, you create a volume, then you create a container and mount the volume into it. The volume is mounted into a directory in the container’s filesystem, and anything written to that directory is stored in the volume. If you delete the container, the volume and its data will still exist.