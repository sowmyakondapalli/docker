#multi stage builds
# FROM maven AS build

# RUN apt-get update -y && apt-get -y install maven
FROM maven:3.9.6-eclipse-temurin-17-alpine AS build

WORKDIR /opt/shipping

COPY pom.xml /opt/shipping/
RUN mvn dependency:resolve
COPY src /opt/shipping/src/
RUN mvn package


#Run

FROM eclipse-temurin:17-jdk-alpine

EXPOSE 8080

WORKDIR /opt/shipping

ENV CART_ENDPOINT=cart:8080
ENV DB_HOST=mysql

COPY --from=build /opt/shipping/target/shipping-1.0.jar shipping.jar

CMD [ "java", "-Xmn256m", "-Xmx768m", "-jar", "shipping.jar" ]

# FROM maven

# WORKDIR /opt/shipping

# COPY pom.xml /opt/shipping/
# RUN mvn dependency:resolve
# COPY src /opt/shipping/src/
# RUN mvn package
# ENV CART_ENDPOINT=cart:8080
# ENV DB_HOST=mysql
# CMD [ "java", "-Xmn256m", "-Xmx768m", "-jar", "/opt/shipping/target/shipping-1.0.jar" ]
