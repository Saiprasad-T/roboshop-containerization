FROM python:3.9.25-alpine3.22
WORKDIR /app
COPY *.py .
COPY *.ini .
COPY *.txt .
RUN apk add --no-cache build-base linux-headers pcre-dev 
RUN pip3 install -r requirements.txt
ENV CART_HOST=<CART-SERVER-IPADDRESS> \
    CART_PORT=8080 \
    USER_HOST=<USER-SERVER-IPADDRESS> \
    USER_PORT=8080 \
    AMQP_HOST=<RABBITMQ-SERVER-IPADDRESS> \
    AMQP_USER=roboshop \
    AMQP_PASS=roboshop123
CMD ["uwsgi","--ini","payment.ini"]