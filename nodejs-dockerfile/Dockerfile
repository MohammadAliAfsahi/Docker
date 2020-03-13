# using node official image
FROM node:alpine
# on default port for nodejs but container runs on port 80
EXPOSE 3000
# install tini package using apk packet manager
RUN apk add --update tini
# create a directory for for app files
RUN mkdir -p /usr/src/app

WORKDIR /usr/src/app

COPY package.json package.json

# run npm to install dependencies from package.json file and clean up 
RUN npm install 

RUN npm cache clean --force
# copy everythin from current directory on the host to current directory on the image
COPY . .

# run our container
CMD [ "tini", "--", "node", "./bin/www" ]
