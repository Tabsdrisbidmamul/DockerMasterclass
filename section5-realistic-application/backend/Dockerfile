FROM node:latest

WORKDIR /app

COPY package.json /app

COPY package-lock.json /app

RUN npm ci

COPY . /app

ARG DEFAULT_PORT=80

ENV PORT ${DEFAULT_PORT}

EXPOSE ${PORT}

CMD [ "node", "app.js" ]