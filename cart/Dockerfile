FROM node:22-alpine3.22 as builder
WORKDIR /app
COPY package*.json ./
RUN npm install
COPY . .

FROM node:22-alpine3.22
WORKDIR /app
COPY --from=builder /app /app
RUN addgroup -S roboshop && adduser -S roboshop -G roboshop
RUN chown -R roboshop:roboshop /app
USER roboshop
CMD ["node", "server.js"]




# FROM node:20
# WORKDIR /app
# # ENV REDIS_HOST="redis"\
# #     REDIS_PORT="6379"\
# #     CATALOGUE_HOST="catalogue"\
# #     CATALOGUE_PORT="8080"

# COPY package*.json ./
# COPY *.js ./
# RUN npm install
# EXPOSE 8080
# CMD ["node", "server.js"]