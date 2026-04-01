FROM nginx:1.24
WORKDIR /usr/share/nginx/html
RUN rm -rf /usr/share/nginx/html/* 
COPY nginx.conf  /usr/share/nginx/html/nginx.conf
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]