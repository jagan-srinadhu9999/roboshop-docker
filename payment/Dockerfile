
FROM python:3.11-alpine AS builder
WORKDIR /app
# Install build dependencies
RUN apk add --no-cache \
    gcc \
    musl-dev \
    libffi-dev \
    postgresql-dev
COPY requirements.txt .
#install dependices into custom location to avoid installing them in the final image
RUN pip install --no-cache-dir --prefix=/install -r requirements.txt

FROM python:3.11-alpine
WORKDIR /app
# Install only runtime libraries (lighter)
RUN apk add --no-cache \
    libpq \
    libffi
COPY --from=builder /install /usr/local
COPY . .
RUN addgroup -S roboshop && adduser -S roboshop -G roboshop \
    && chown -R roboshop:roboshop /app
USER roboshop
CMD ["uwsgi", "--ini", "payment.ini"]

# FROM python:3
# WORKDIR /app
# # ENV CART_HOST="cart"\
# #     CART_PORT="8080"\
# #     USER_HOST="user"\
# #     USER_PORT="8080"\
# #     RABBITMQ_HOST="rabbitmq"\
# #     RABBITMQ_PORT="5672"\
# #     RABBITMQ_USER="roboshop"\
# #     RABBITMQ_PASSWORD="roboshop123"
# COPY payment.ini .
# COPY *.py .
# COPY requirements.txt .
# RUN pip3  install -r requirements.txt
# EXPOSE 8080
# CMD ["uwsgi", "--ini", "payment.ini"]
