FROM node:13.10.1-alpine

WORKDIR /usr/src/app

# add /usr/src/app/node_modules/.bin to $PATH
ENV PATH /usr/src/app/node_modules/.bin:$PATH

# install and cache app dependencies
COPY package.json /usr/src/app/package.json
COPY package-lock.json /usr/src/app/package-lock.json
RUN apk add --no-cache --virtual .gyp python make g++ \
    && npm ci \
    && apk del .gyp

# start server in dev mode
CMD ["npm", "run", "dev"]