# Instructions from the app developer
# - you should use the 'node' official image, with the alpine branch
FROM node:15-alpine

# - this app listens on port 3000, but the container should launch on port 80
# - so it will respond to http://localhost:80 on your computer
EXPOSE 3000

# - then it should use alpine package manager to install tini: 'apk add --update tini'
RUN apk add --update tini

# - then it should create directory /usr/src/app for app files with 'mkdir -p /usr/src/app'
RUN mkdir -p /usr/src/app

# - Node uses a "package manager", so it needs to copy in package.json file
WORKDIR /usr/src/app
COPY package.json package.json

# - then it needs to run 'npm install' to install dependencies from that file
RUN npm install

# - to keep it clean and small, run 'npm cache clean' after above
# - then it needs to copy in all files from current directory
# - "COPY . ." means "copy all files of my current folder on host to the current folder at the container"
COPY . .

# - then it needs to start container with command 'tini -- node ./bin/www'
CMD ["tini", "--", "node", "./bin/www"]
# - in the end you should be using FROM, RUN, WORDIR, COPY, EXPOSE, and CMD commands