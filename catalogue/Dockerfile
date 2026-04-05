# FROM node:20
# WORKDIR /app
# COPY package*.json ./

# RUN npm install
# COPY . .
# #ENV MONGO_URL="mongodb://mongodb:27017/catalogue"\
#  #   MONGO="true"
# #ENV MONGO_URL=mongodb://mongodb:27017/catalogue
# #ENV MONGO=true 
# #to keep the env variables in the container, we can set them in the docker-compose file instead of the Dockerfile
#  EXPOSE 8080
# CMD ["node", "server.js"]

#following docker best practices
FROM node:22-alpine3.22 as builder
WORKDIR /app
COPY package*.json ./
COPY . .
#RUN npm ci
RUN npm install

FROM node:22-alpine3.22
WORKDIR /app
#COPY --from=builder /app /app
COPY --from=builder /app /app
RUN addgroup -S roboshop && adduser -S roboshop -G roboshop
RUN chown -R roboshop:roboshop /app
USER roboshop 
#COPY . . no need to copy the files again as we have already copied them in the builder stage
ENTRYPOINT ["node"]
CMD ["server.js"]