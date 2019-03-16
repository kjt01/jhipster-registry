# Start with a base image containing Java runtime
FROM openjdk:8-jdk-alpine

# Add Maintainer Info
LABEL maintainer="engineering@wondersco.com"

# Add a volume pointing to /tmp
VOLUME /tmp

# Make port available to the world outside this container
EXPOSE 8761

# Add the application's jar to the container
ADD *.war app.war

RUN apk update && apk add --no-cache tzdata && apk add --no-cache paxctl && paxctl -cm /usr/lib/jvm/java-1.8-openjdk/jre/bin/java && apk del paxctl
ENV TZ America/New_York

# Run the jar file
ENTRYPOINT ["java", "-Djava.security.egd=file:/dev/./urandom", "-jar", "/app.war"]
