FROM node:20
WORKDIR /app
COPY package*.json ./

RUN npm install
COPY . .
ENV MONGO_URL="mongodb"
EXPOSE 8080
CMD ["node", "server.js"]
