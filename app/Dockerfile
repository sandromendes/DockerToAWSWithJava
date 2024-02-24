FROM openjdk:11-jdk-slim
VOLUME /tmp
ARG JAR_FILE=app/target/*.jar
COPY ${JAR_FILE} app.jar
COPY --chown=node:node ./package*.json ./
EXPOSE 8080
RUN bash -c 'touch /app.jar'
ENTRYPOINT ["java", "-Djava.security.egd=file:/dev/./urandom", "-jar", "/app.jar"]