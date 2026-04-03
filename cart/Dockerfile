FROM node:20
WORKDIR /app
ENV REDIS_HOST="redis"\
    REDIS_PORT="6379"\
    CATALOGUE_HOST="catalogue"\
    CATALOGUE_PORT="8080"

COPY package*.json ./
COPY *.js ./
RUN npm install
EXPOSE 8080
CMD ["node", "server.js"]