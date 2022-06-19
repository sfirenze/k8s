FROM registry.access.redhat.com/redhat-openjdk-18/openjdk18-openshift:1.12-1.1655301789

COPY passwordapi.jar /usr/src/app/
WORKDIR /usr/src/app/

EXPOSE 8080

CMD ["java", "-jar", "passwordapi.jar"]

