
# ---------- Builder ----------
FROM node:20-alpine AS builder

WORKDIR /app

COPY package*.json ./
RUN npm install

COPY . .
RUN npm run build

# ---------- Runtime ----------
FROM nginx:1.24-alpine

RUN rm -f /etc/nginx/conf.d/default.conf

COPY nginx.conf /etc/nginx/conf.d/default.conf

COPY --from=builder /app/build /usr/share/nginx/html

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]


#FROM nginx:1.24
# WORKDIR /usr/share/nginx/html
# RUN rm -rf /usr/share/nginx/html/* 
# RUN rm -f /etc/nginx/nginx.conf
# RUN rm -f /etc/nginx/conf.d/default.conf
# COPY nginx.conf  /etc/nginx/nginx.conf
# COPY static /usr/share/nginx/html
# EXPOSE 80
# CMD ["nginx", "-g", "daemon off;"]