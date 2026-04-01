FROM maven:3.5
WORKDIR /app
ENV CART_ENDPOINT="http://cart:8080"\
    DB_HOST="mysql"
COPY pom.xml ./
COPY src ./src

RUN mvn clean package
RUN mv target/shipping-1.0.jar shipping.jar 
EXPOSE 8080
CMD ["java","-jar","shipping.jar"]

