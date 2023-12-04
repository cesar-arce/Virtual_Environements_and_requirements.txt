# Dockercraft

source: https://github.com/docker/dockercraft

# How to run Dockercraft

1. Install Minecraft: minecraft.net

The Minecraft client hasn't been modified, just get the official release.

2. Pull or build Dockercraft image: (an official image will be available soon)

$ docker pull gaetan/dockercraft

or

$ git clone git@github.com:docker/dockercraft.git

$ docker build -t gaetan/dockercraft dockercraft

3.Run Dockercraft container:

docker run -t -i -d -p 25565:25565 \
-v /var/run/docker.sock:/var/run/docker.sock \
--name dockercraft \
gaetan/dockercraft
Mounting /var/run/docker.sock inside the container is necessary to send requests to the Docker remote API.

The default port for a Minecraft server is 25565, if you prefer a different one: -p <port>:25565

4. Open Minecraft > Multiplayer > Add Server

The server address is the IP of Docker host. No need to specify a port if you used the default one.

If you're using Docker Machine: docker-machine ip <machine_name>




