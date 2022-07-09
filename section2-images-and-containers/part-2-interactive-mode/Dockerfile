FROM python:latest

WORKDIR /app

COPY . /app

CMD [ "python", "rng.py" ]

# docker run -it [image_name]

# docker start -ai [container_name]

# We need to specify in the start command to attach to the container and start in interactive mode as well, unlike where we ran the image in interactive mode, we also ran it in a psudeo terminal.

# Docker container will remmeber the psudo terminal, but it needs explicit flags to tell it to start in interactive and attached mode