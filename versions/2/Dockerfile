# Gradle v2.14
# docker run --rm pottava/gradle:2 gradle -version
# docker run --rm -v /path/to/app:/app pottava/gradle:2 gradle build
# docker run --rm -v /path/to/app:/app pottava/gradle:2 sh -c "gradle build && gradle clean"

FROM pottava/java:8

ENV GRADLE_VERSION=2.14

RUN set -ex \
      && apk --no-cache add --virtual build-dependencies curl unzip \
      && apk --no-cache add bash \
      && cd /usr/lib \
      && curl -O --location --silent --show-error https://services.gradle.org/distributions/gradle-${GRADLE_VERSION}-bin.zip \
      && unzip -q gradle-${GRADLE_VERSION}-bin.zip \
      && ln -s /usr/lib/gradle-${GRADLE_VERSION}/bin/gradle /usr/bin/ \
      && rm -rf gradle-${GRADLE_VERSION}-bin.zip \
          gradle-${GRADLE_VERSION}/bin/gradle.bat \
          gradle-${GRADLE_VERSION}/getting-started.html \
          gradle-${GRADLE_VERSION}/media \
          /opt/jdk/*src.zip \
      && apk del --purge build-dependencies

VOLUME /app /root/.gradle/caches
WORKDIR /app
