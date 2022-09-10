FROM node:latest

WORKDIR /app

COPY package.json /app

COPY package-lock.json /app

RUN npm ci

COPY . /app

ARG DEFAULT_PORT=3000

ENV PORT ${DEFAULT_PORT}

EXPOSE ${PORT}

CMD [ "npm", "start" ]


# Networks with containers
# Depending on how your application works - sometimes adding the application to a network is not needed

# The backend code is a server, it listens on a port and executes http requests via listening on the port, thus we can leverage docekrs network and place the db and backend onto the same network - this will allow docker to transform container names with the correct connection string

# The same is not said for the frontend, like an SPA. The JS dev server is spun up on a localhost which is intended to be used in a browser - thus it is not like the backend - and cannot leverage docker container name transformation in connection strings.

# So quite literally make sure to publish a port for the backend, and for the frontend - for your connection string make it localhost as you would normally when you run an SPA and a backend API

# http://localhost/api/...

# see how a port was not mentioned, there is no need for that anymore. Just remember this - if you place a port on http://localhost your SPA won't work - I don't know why, but that's just how it is