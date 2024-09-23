[Source](https://courses.dometrain.com/courses/take/from-zero-to-hero-docker-for-developers)


# Core Concepts
### Containers
- A container tends to only have one primary software running i.e. SQL Server, an API, RabbitMQ etc.
- They each have their own filesystem, network stack, specific shell for that container.
- Required software is all inside the container. The underlying machine does not need these installed in order for the container to work as it's all inside the container.

### Images
- Static file on disk
- Image is like a template
- Container is an instance of an image
- Each container instance is isolated from one another in that a change in one container does not effect another.
![[Pasted image 20240923084128.png|400]]
- When you have an application that you want to package up and send to a colleague, you would not send a container. Instead, you would create an image and upload that image to a container registry so your colleague can download it. Then your colleague would create their own containers from that image.
- Docker Hub is an example of a container registry but there are others.

### Container Registries and Docker Hub
- Other examples of container registries
	- Azure container registry
	- Amazon Elastic container registry
	- Google Artifact Registry
- Docker uses terminology `push` and `pull` instead of terms like `upload` and `download`.

# Interacting with Docker
### Docker CLI
- `docker run` will implicitly perform `docker pull` if the image does not exist locally.
	- It also runs a container from that image.

# Let's Play
### Port Mapping
- ???

### Detached mode and logs
- ???

### Detached mode and logs
- ???

### Shell access and makes changes inside containers
- ???

### More example 3rd party images
- ???


