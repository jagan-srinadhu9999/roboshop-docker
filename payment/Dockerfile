
FROM python:3.9.25-alpine3.22 AS builder
WORKDIR /app
# Install build dependencies
# RUN apk add --no-cache \
#     gcc \
#     musl-dev \
#     libffi-dev \
#     postgresql-dev
RUN apk add --no-cache build-base linux-headers pcre-dev
COPY requirements.txt .
#install dependices into custom location to avoid installing them in the final image
#RUN pip3.11 install --no-cache-dir --prefix=/install -r requirements.txt
RUN pip3.9 install --prefix=/install -r requirements.txt

FROM python:3.9.25-alpine3.22
EXPOSE 8080
WORKDIR /app
# Install only runtime libraries (lighter)
# RUN apk add --no-cache \
#     libpq \
#     libffi
RUN apk add --no-cache pcre

RUN addgroup -S roboshop && adduser -S roboshop -G roboshop \
    && chown -R roboshop:roboshop /app
COPY --from=builder /install /usr/local
COPY --chown=roboshop:roboshop payment.ini *.py requirements.txt /app/
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
