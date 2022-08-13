FROM node:latest

WORKDIR /app

COPY package.json /app

RUN npm install

COPY . /app

EXPOSE 80

CMD [ "node", "server.js" ]

# volumes
# there are anonymous and named variants

# running - docker volume ls
# will list all named and anonymous volumes on the system

# anonymous are define in the dockerfile as:
#   VOLUME [work dir/the folder you want to save ]
#   VOLUME [ "/app/feedback" ]

# caveat is that they are not persistented, once the container has stopped, the volume is removed and all of its associating data.

# named volumes are not written in the dockerfile, they are part of the cmd when generating the image - they are persistent and the data is still there even after the container has shutdown/ removed

# in the run command, we add the -v flag
#   -v name_of_volume:work dir/the folder you want to save
#   * example is shorten down to show only the -v flag
#   docker run -v feedback:/app/feedback

# Everytime you restart the container the previous commands should still be there anyway

# but if you rerun the same image, but using the same volume name and path as before, the data that was persisted from the previous session will be available in this new container instance