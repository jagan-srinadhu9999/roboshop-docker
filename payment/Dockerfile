FROM python:3
WORKDIR /app
ENV CART_HOST="cart"\
    CART_PORT="8080"\
    USER_HOST="user"\
    USER_PORT="8080"\
    RABBITMQ_HOST="rabbitmq"\
    RABBITMQ_PORT="5672"\
    RABBITMQ_USER="roboshop"\
    RABBITMQ_PASSWORD="roboshop123"
COPY payment.ini .
COPY *.py .
COPY requirements.txt .
RUN pip3  install -r requirements.txt
EXPOSE 8080
CMD ["uwsgi", "--ini", "payment.ini"]
