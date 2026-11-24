FROM python:3.9.25-alpine3.22
WORKDIR /app
COPY *.py .
COPY *.ini .
COPY *.txt .
RUN apk add --no-cache build-base linux-headers pcre-dev 
RUN pip3 install -r requirements.txt
ENV CART_HOST=cart \
    CART_PORT=8080 \
    USER_HOST=user \
    USER_PORT=8080 \
    AMQP_HOST=rabbitmq \
    AMQP_USER=roboshop \
    AMQP_PASS=roboshop123
CMD ["uwsgi","--ini","payment.ini"]