FROM eclipse-temurin:17-jre

RUN useradd -m newuser
WORKDIR /app

COPY target/myapp-*.jar app.jar
RUN chown newuser:newuser app.jar
USER newuser

ENTRYPOINT ["java","-jar","/app/app.jar"]