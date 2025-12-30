# Stage 1
FROM maven:3.9.9-eclipse-temurin-17 AS buildstage

WORKDIR /build
COPY pom.xml .
RUN mvn dependency:go-offline
COPY src ./src
RUN mvn clean package -DskipTests 

#Stage 2
FROM eclipse-temurin:17-jre

RUN useradd -m newuser
WORKDIR /app
ARG JAR=target/myapp-*.jar
COPY --from=buildstage /build/${JAR} app.jar
RUN chown newuser:newuser app.jar
USER newuser
ENTRYPOINT ["java","-jar","/app/app.jar"]