FROM node:10-alpine

WORKDIR /usr/app

ARG PORT=2000

ENV PORT ${PORT}

EXPOSE ${PORT}

COPY package.json .

RUN npm install

COPY src src
