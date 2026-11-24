FROM node:20-alpine AS builder
WORKDIR /app
COPY package*.json ./
RUN npm install

FROM node:20-alpine

RUN addgroup -S roboshop && \
    adduser -S roboshop -G roboshop

WORKDIR /app

COPY --from=builder /app/node_modules ./node_modules
COPY --chown=roboshop:roboshop package*.json ./
COPY --chown=roboshop:roboshop server.js ./

ENV MONGO=true \
    REDIS_URL='redis://redis:6379' \
    MONGO_URL="mongodb://mongodb:27017/users"

USER roboshop

CMD ["node", "server.js"]




# FROM node:20
# WORKDIR /app
# COPY package.json .
# COPY server.js .
# RUN npm install 
# ENV MONGO=true \
#     REDIS_URL='redis://redis:6379' \
#     MONGO_URL="mongodb://mongodb:27017/catalogue"
# CMD ["node", "server.js"]