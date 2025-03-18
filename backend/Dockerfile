#FROM node:20
FROM node:20.18.3-alpine3.21 AS builder
WORKDIR /opt/backend
COPY package.json ./
COPY *.js ./
RUN npm install


FROM node:20.18.3-alpine3.21
RUN addgroup -S expense && adduser -S expense -G expense && \
    mkdir /opt/backend && \
    chown -R expense:expense /opt/backend
ENV DB_HOST="mysql"
WORKDIR /opt/backend
USER expense
COPY --from=builder /opt/backend /opt/backend
CMD ["node", "index.js"]



# First without these lines try - Below lines for user add access
# FROM node:20.18.3-alpine3.21   -- to decrease size
# RUN addgroup -S expense && adduser -S expense -G expense
# RUN mkdir /opt/backend 
# RUN chown -R expense:expense /opt/backend
# USER expense

# First we are installing NPM packages with name as Builder and copying into specified work directory 
# path and using that path we are copying in second step and using it 