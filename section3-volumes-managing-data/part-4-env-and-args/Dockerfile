FROM node:latest

WORKDIR /app

COPY package.json /app

RUN npm install

COPY . /app

ARG DEFAULT_PORT=80

ENV PORT ${DEFAULT_PORT}

EXPOSE $PORT

CMD [ "npm", "start" ]

# environment and argument variables
# You want to place these variables very much below package installers etc. - that way the package installer is not ran everytime - but uses the cache

# in the docker files we can provide the enviornment variable via the ENV keyword, followed by its key then value

# ENV key value
# ENV PORT 80

# We can then use this ENV variable in the docker file, using the $VAR_NAME syntax

# ENV PORT 80
# EXPOSE $PORT 

# env in command line
# We can use the --env or -e followed by key=value
# -e PORT=80

# Do note, that if ENV is specificed in the image, the command line will not override the image's interal exposed port

# EXAMPLE
# If you have specified PORT 80 in the docker file, but you in the command line you change it to 8000, then you want to still expose poret 80 in the -p option
# -p 3000:80 -e PORT=8000

# Its hard to tell, but server.js is listening on port 8000 now, as opposed to port 80

# you can also reference .env files for enviornment variables - keeps the command cleaner
# --env-file file
# --env-file ./.env

# args
# basically defined constants

# ARG NAME=VALUE
# ARG DEFAULT_PORT=80

# ENV PORT ${DEFAULT_PORT}
#   or
# ENV PORT $DEFAULT_PORT

# We can use the default port in the build command, wehn building the image - we can give it a default - one for prod and then another for dev enviorments

# The argument name has to be spelt correctly

# docker build --build-arg ARG_NAME=value
# docker build --build-arg DEFAULT_PORT=8000