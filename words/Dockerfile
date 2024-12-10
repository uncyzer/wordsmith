# STAGE 1 - Build - 
FROM maven:3-jdk-8-alpine AS builder
WORKDIR /build
COPY pom.xml .
COPY src src
RUN mvn verify

# STAGE 2 - Image app
FROM openjdk:8-jre-alpine 
WORKDIR /app
COPY --from=builder /build/target/ /app
CMD ["java", "-Xmx8m", "-Xms8m", "-jar", "./words.jar"]