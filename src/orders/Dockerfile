# ----------- Build Stage -----------
FROM public.ecr.aws/amazonlinux/amazonlinux:2023 AS build-env

# Install only required dependencies without weak suggestions
RUN dnf --setopt=install_weak_deps=False install -q -y \
    maven \
    java-21-amazon-corretto-headless \
    which \
    tar \
    gzip \
    && dnf clean all

VOLUME /tmp
WORKDIR /

COPY .mvn .mvn
COPY mvnw .
COPY pom.xml .

# Preload dependencies
RUN ./mvnw dependency:go-offline -B -q

# Copy app source
COPY ./src ./src

# Build app
RUN ./mvnw -DskipTests package -q && \
    mv /target/orders-0.0.1-SNAPSHOT.jar /app.jar

# ----------- Package Stage -----------
FROM public.ecr.aws/amazonlinux/amazonlinux:2023

# Install only needed runtime packages
RUN dnf --setopt=install_weak_deps=False install -q -y \
    java-21-amazon-corretto-headless \
    shadow-utils \
    && dnf clean all

# Enable curl with telnet support
RUN dnf -q -y swap libcurl-minimal libcurl-full \
    && dnf -q -y swap curl-minimal curl-full

# Setup app user
ENV APPUSER=appuser
ENV APPUID=1000
ENV APPGID=1000

RUN useradd \
    --home "/app" \
    --create-home \
    --user-group \
    --uid "$APPUID" \
    "$APPUSER"

ENV JAVA_TOOL_OPTIONS=
ENV SPRING_PROFILES_ACTIVE=prod

WORKDIR /app
USER appuser

# Copy built app
COPY --chown=appuser:appuser --from=build-env /app.jar .

EXPOSE 8080

ENTRYPOINT ["sh", "-c", "java $JAVA_OPTS -jar /app/app.jar"]
