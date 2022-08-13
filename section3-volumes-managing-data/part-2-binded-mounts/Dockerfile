FROM node:latest

WORKDIR /app

COPY package.json /app

RUN npm install

COPY . /app

EXPOSE 80

CMD [ "npm", "start" ]

# bind mounts
# these are managed by us, and not by docker, thus we can choose the path on our host machine where to save the configuation

# These are great for persistent, EDITABLE, data. i.e. source code
# so we can add a watcher to the source code by doing so

# this is added not to the dockerfile but to do the container when running

# the -v can be used to name a volume and can also be used to bind a mount

# difference between them is that binding will take an absolute path - to where the directory or file to watch, and then the docker working directory to where the changes should be reflected to

# docker -v "absolute_path:work dir"
# docker -v "E:\Docker-Masterclass\section3-volumes-managing-data\part-2-binded-mounts\:/app"

# docker -v "%cd%":/app - for windows
# docker -v $(pwd):/app - for linux

# binded mounts
# We ran into an issue by doing this

# Why?
# Your local host machine files overwrite the docker container files, this would be great if the local machine had node_modules installed, but it didn't and all the dependencies were deleted.

# Overcome
# We use anonymous volumes - volumes which only exist with the container lifecycle, i.e. if the container is removed so is the volume.

# These can be created either in the docker file: VOLUME ["path"]
# or in the cmd line as another -v flag: -v /path without the colon - colon will define the name

# conflicts
# the longer the path, the higer precende it gets
# so us binding the whole local folder of part-2 to the /app will replace all the files as it sees fit

# but the /app/node_modules is more specific, and will not be overwritten during the above process

# Changes
# We would need to reload the page to the see the change

# On Windows the above won't work, just do your projects in WSL2, so in linux.
# There is the WSL remote extension for VSCODE, which will open up the file system in VSCODE GUI

# Performance
# We can use anonymous volumes to imporve container performance, but outsourcing bits of data - like node_module or maybe the tmp/ folder
# it means less overhead that the container has to manage