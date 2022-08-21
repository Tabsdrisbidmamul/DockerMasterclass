FROM node

WORKDIR /app

COPY package.json .

RUN npm install

COPY . .

CMD ["node", "app.js"]

# Container communication and networking

# Container to External
# Out of the box, containers can make external HTTP calls, this means that we can communicate to web apis and websites - which are completely independent from the container

# Container to Host machine
# If we want to connect to a local hosted db, the connection string is all we need to change, instead of localhost or the machine name, we change it to:

# Original
#     mongodb://localhost:27017/swfavorites

# After
#     mongodb://host.docker.interal:27017/swfavorites 

# docker containers understand what host.docker.internal means to point to your local machine


# Container to Container
# In this example we want to run the mongodb and the node app in separate containers.

# very simple - we run
#   docker run -d --name mongodb mongo

# To pull down the mongo image, from docker hub, and this will run a mongodb within a container - listening on the default port 27017

# How to connet our node container to mongodb container?
# The not best practice way
# We can run docker inspect mongodb, this will return back the json config of the container, and in the NetworkSettings property, you can see what port(s) it is listening on etc, but you can also see the IP its on.

# So place the IP address string into your connection string in your app.js
#   'mongodb://172.17.0.2:27017/swfavorites'

# It works, but the issue is you have to always change the code and run docker inspect to find out what the IP is always - not ideal for staging and production

# The best practice way
# You can run docker run --network network_name

# This will create a wrapper around all containers to be in the same group, that way - the containers are not isolated anymore, but can see who's in the group, and this allow us to let Docker do the communication

# Steps
# 1. You have to create the network manually, docker does not do it automatically - like ti does with volumes
#   docker network create network_name
#   docker network create fav-net

# 2. Run a container with the --network option, supplying the network name for the container to be added into the network
#   docker run --network network_name
#   docker run -d --name mongodb --network fav-net mongo

# 3. To connect, change the connection string to point to the container name - always give a container a namem, its just easier.
#   'mongodb://exampledb:27017/swfavorites'
#   'mongodb://mongodb:27017/swfavorites'

# 4. profit from the container communication, as docker will transform all connection strings to the correct IP names
# Make sure to add the --network fav-net to the node-app, for its container to be part of the same group as the mongodb container

# Both containers are in the same group, docker enables croos-communication between containers
# Because of this, we don't need to publish any ports for the mongodb container - because Docker can freely connect containers with one another, you only need to publish ports if you are trying to gain access from host machine/ external to container

#-------------------------------
#| ======fav-net network=====|  |
#| |                         |  |
#| |  mongodb     node-app   |  |
#| |=========================|  |
#--------------------------------