# Base image with Java 17 and Open Liberty kernel
FROM icr.io/appcafe/open-liberty:kernel-slim-java17-openj9-ubi-minimal

# Metadata for container image
ARG VERSION=1.0
ARG REVISION=SNAPSHOT

LABEL \
  org.opencontainers.image.authors="Your Name" \
  org.opencontainers.image.vendor="Open Liberty" \
  org.opencontainers.image.url="local" \
  org.opencontainers.image.source="https://github.com/OpenLiberty/guide-spring-boot" \
  org.opencontainers.image.version="$VERSION" \
  org.opencontainers.image.revision="$REVISION" \
  vendor="Open Liberty" \
  name="springboot-app" \
  version="$VERSION-$REVISION" \
  summary="Spring Boot application running on Open Liberty" \
  description="This image contains the Spring Boot app running with Open Liberty."

# Copy Spring Boot fat JAR into the container
COPY --chown=1001:0 target/guide-spring-boot-0.1.0.jar /config/app.jar

# Copy Open Liberty server configuration
RUN cp /opt/ol/wlp/templates/servers/springBoot3/server.xml /config/server.xml

# Enable Liberty features
RUN features.sh

# Optional: Configure Liberty server
RUN configure.sh

# Start the Spring Boot app
CMD ["java", "-jar", "/config/app.jar"]

