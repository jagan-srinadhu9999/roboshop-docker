FROM node:20
WORKDIR /app
ENV MONGO="true"\
    MONGO_URL="mongodb://mongodb:27017/catalogue"\
    REDIS_URL="redis://redis:6379"
COPY package*.json ./
COPY *.js ./
RUN npm install
CMD ["node", "server.js"]
