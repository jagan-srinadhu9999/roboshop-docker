FROM node:20
WORKDIR /app
COPY package*.json ./
COPY . .
RUN npm install
ENV MONGO_URL="mongodb"
EXPOSE 8080
CMD ["node", "server.js"]
