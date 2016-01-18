# Gradle v2.9
# docker run --rm pottava/gradle:2.9 gradle -version
# docker run --rm -v /path/to/app:/app pottava/gradle:2.9 gradle

FROM pottava/java:8

ENV GRADLE_VERSION=2.9

RUN set -ex \
      && apk --no-cache add --virtual build-dependencies curl unzip \
      && apk --no-cache add bash \
      && cd /usr/lib \
      && curl -O --location --silent --show-error https://downloads.gradle.org/distributions/gradle-${GRADLE_VERSION}-bin.zip \
      && unzip -q gradle-${GRADLE_VERSION}-bin.zip \
      && ln -s /usr/lib/gradle-${GRADLE_VERSION}/bin/gradle /usr/bin/ \
      && rm -rf gradle-${GRADLE_VERSION}-bin.zip \
          /opt/jdk/*src.zip \
      && apk del --purge build-dependencies

VOLUME /app /root/.gradle/caches
WORKDIR /app
