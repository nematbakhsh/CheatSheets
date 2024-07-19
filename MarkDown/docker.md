# Installation

Install docker engine step by step from Docker docs.

If using docker as a non-root user, add your user to the docker group with `sudo usermod -aG docker <user>`

Check installation
```shell
docker --version
sudo docker run hello-world
```

Look for new images (containers are instances of images) in [Docker Hub]{hub.docker.com}.

- `docker ps` show running containers
    - `-a` see all available containers on you machine
- `docker images` or `docke image ls` show all images
- `docker rm` remove container
- `docker rmi <image-ID>` remove image
- `docker image`
  - `ls` list images
  - `pull <software-name:tag>` pulling the image from the hub
- `docker run <image-name|image-id> <command>` create and start a container
  - `-i` (or `--interactive`): Keeps STDIN open, allowing you to interact with the container.
  - `-t` (or --tty): Allocates a pseudo-TTY, which allows for interactive terminal sessions.
  - `-it` usuallly used together
