FROM maven:3.9.9-eclipse-temurin-17 AS builder

WORKDIR /app

COPY pom.xml .
COPY src ./src

RUN mvn clean package -DskipTests


FROM eclipse-temurin:17-jre-alpine
RUN addgroup -S roboshop && \
    adduser -S roboshop -G roboshop
WORKDIR /app

COPY --from=builder --chown=roboshop:roboshop /app/target/shipping-1.0.jar shipping.jar

ENV CART_ENDPOINT=cart:8080 \
    DB_HOST=mysql

CMD ["java", "-jar", "shipping.jar"]



# FROM maven:3.10.2-eclipse-temurin-17
# WORKDIR /app
# COPY src ./src
# COPY pom.xml .
# RUN mvn clean package 
# RUN mv target/shipping-1.0.jar shipping.jar 
# ENV CART_ENDPOINT=cart:8080 \
#     DB_HOST=mysql
# CMD ["java","-jar","shipping.jar"]