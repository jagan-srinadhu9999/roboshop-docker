FROM nginx:1.24
RUN rm -rf /usr/share/nginx/html/* 
WORKDIR /usr/share/nginx/html
COPY /etc/nginx/nginx.conf .
CMD ["nginx", "-g", "daemon off;"]