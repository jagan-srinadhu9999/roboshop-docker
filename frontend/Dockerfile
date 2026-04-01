FROM nginx:1.24
WORKDIR /usr/share/nginx/html
RUN rm -rf /usr/share/nginx/html/* 
RUN rm -f /etc/nginx/nginx.conf
RUN rm -f /etc/nginx/conf.d/default.conf
COPY nginx.conf  /etc/nginx/nginx.conf
COPY static /usr/share/nginx/html
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]