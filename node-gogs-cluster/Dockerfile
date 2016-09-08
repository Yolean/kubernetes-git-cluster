FROM node:6

WORKDIR /usr/src/app

ADD package.json /usr/src/app/

RUN npm install

ADD src usr/src/app/src

ENTRYPOINT ["npm", "start"]
