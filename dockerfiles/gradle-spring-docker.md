---
description: Dockerfile to host Java web app with .WAR files
---

# Gradle Spring Docker

```docker
FROM gradle:6.8.3-jdk11 AS build
COPY --chown=gradle:gradle . /home/gradle/src
WORKDIR /home/gradle/src

RUN gradle bootWar --no-daemon

RUN mkdir /app

COPY ./build/libs /app/libs

FROM tomcat:10.1.0-jre11-temurin

COPY --from=build /app/libs /usr/local/tomcat/webapps/

EXPOSE 8080

CMD ["catalina.sh", "run"]
```
