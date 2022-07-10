FROM node:latest

WORKDIR /app

COPY package.json /app

RUN npm install

COPY . /app

EXPOSE 80

CMD [ "node", "server.js" ]

# running the --rm command with docker run will automatically remove the container, so we don't need to remove it manually - or we can prune it will later on

# docker cp source dest
# copying from your local machine is specifying the path to it, but to the container, you do the container_name:/path_you_want

#  docker cp dummy/. compassionate_wilson:/test

# this will copy all the contents of the dummy folder to the compassionate_wilson container, and it will place the contents of the dummy folder into a existing/new test folder

# localhost
# dummy
# |_
#   test.txt

# compassionate_wilson
# |_
#   test
#       |_
#         test.txt

# naming 
# docker run --name container_name
#   docker run --name goalsapp
# docker build -t name:tag
#   docker build -t goals:latest .