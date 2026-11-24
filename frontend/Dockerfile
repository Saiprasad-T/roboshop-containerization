FROM nginx:1.24
RUN rm -rf /usr/share/nginx/html/* 
RUN rm /etc/nginx/nginx.conf
RUN rm /etc/nginx/conf.d/*
COPY all /usr/share/nginx/html/
COPY nginx.conf /etc/nginx/nginx.conf