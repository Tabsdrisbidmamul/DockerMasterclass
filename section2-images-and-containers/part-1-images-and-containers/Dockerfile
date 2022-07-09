FROM node:latest

WORKDIR /app

COPY package.json /app

RUN npm install

COPY . /app

EXPOSE 80

CMD [ "node", "server.js" ]

# docker run -p [localhost_port:docker_exposed_port] [image_name]

# docker start [container_name]

# docker start will re-run a stopped a container - the previous command to run the image will be remembered, and simply running the "start" command is enough