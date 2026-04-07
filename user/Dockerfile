FROM node:22-alpine3.22 as builder
WORKDIR /app
COPY package*.json ./
RUN npm install
COPY *.js . 

FROM node:22-alpine3.22
WORKDIR /app
COPY --from=builder /app /app
RUN addgroup -S roboshop && adduser -S roboshop -G roboshop \
    && chown -R roboshop:roboshop /app
USER roboshop
CMD ["node", "server.js"]


# FROM node:20
# WORKDIR /app
# ENV MONGO="true"\
#     MONGO_URL="mongodb://mongodb:27017/catalogue"\
#     REDIS_URL="redis://redis:6379"
# COPY package*.json ./
# COPY *.js ./
# RUN npm install
# CMD ["node", "server.js"]
