FROM node:20
# FROM node:20.18.3-alpine3.21 AS builder
WORKDIR /opt/backend
COPY package.json .
COPY *.js .
RUN npm install
ENV DB_HOST="mysql"
# ENV DB_HOST="localhost"  when we use network as host      
CMD ["node", "index.js"]