FROM node:latest

WORKDIR /app

COPY package.json /app

RUN npm install

COPY . /app

EXPOSE 80

CMD [ "npm", "start" ]

# readonly volumes
# We can make a volume read-only previelege

# we add another colon with ro afterwards
# -v [/path:]/path:ro
# -v "%cd%":/app:ro

# again conflicts will be taken higher precednece for paths that are longer