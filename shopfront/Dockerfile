# Use an official OpenJDK runtime as a parent image
FROM openjdk:8-jre-alpine

# Set the working directory to /app
WORKDIR /app

# Copy the all the files to the container
COPY . .

# Build the application with Maven
RUN apk add --no-cache openjdk8 && apk add maven \
    && mvn clean install \
    && rm -rf /root/.m2/repository \
    && apk del maven

# Set the application entry point
ENTRYPOINT ["java", "-Djava.security.egd=file:/dev/./urandom", "-jar", "target/shopfront-0.0.1-SNAPSHOT.jar", "server"]

# Expose the port the application is listening on
EXPOSE 8010
