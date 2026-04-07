FROM maven:3.9.6-eclipse-temurin-8-alpine AS builder
WORKDIR /app
COPY pom.xml ./
COPY src ./src
RUN mvn clean package -DskipTests

FROM maven:3.9.6-eclipse-temurin-8-alpine
WORKDIR /app
COPY --from=builder /app/target/shipping-1.0.jar shipping.jar
RUN addgroup -S roboshop && adduser -S roboshop -G roboshop \
    && chown -R roboshop:roboshop /app
USER roboshop
CMD ["java","-jar","shipping.jar"]

# FROM maven:3.5
# WORKDIR /app
# ENV CART_ENDPOINT="http://cart:8080"\
#     DB_HOST="mysql"
# COPY pom.xml ./
# COPY src ./src

# RUN mvn clean package
# RUN mv target/shipping-1.0.jar shipping.jar 
# EXPOSE 8080
# CMD ["java","-jar","shipping.jar"]

