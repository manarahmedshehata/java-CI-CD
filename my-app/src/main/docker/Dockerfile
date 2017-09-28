FROM openjdk:8u111-jdk-alpine 

VOLUME /tmp
ADD my-app-1.0-SNAPSHOT.jar my-app.jar
ENTRYPOINT ["java","-Djava.security.egd=file:/dev/./urandom","-Xmx512M","-jar","/my-app.jar","--debug"]
CMD exec /bin/bash -c "trap : TERM INT; sleep infinity & wait"
