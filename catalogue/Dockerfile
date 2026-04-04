FROM node:20
WORKDIR /app
COPY package*.json ./

RUN npm install
COPY . .
#ENV MONGO_URL="mongodb://mongodb:27017/catalogue"\
 #   MONGO="true"
#ENV MONGO_URL=mongodb://mongodb:27017/catalogue
#ENV MONGO=true
 EXPOSE 8080
CMD ["node", "server.js"]
