FROM debian:jessie
MAINTAINER Josh Williams <theprime@codingprime.com>

ENV GRADLE_VERSION 2.0
ENV DEBIAN_FRONTEND noninteractive

WORKDIR /usr/local/

RUN apt-get update && apt-get install -y --no-install-recommends \
		curl \
		unzip \
		default-jdk \
		ca-certificates \
	&& curl -sSL \
		https://services.gradle.org/distributions/gradle-${GRADLE_VERSION}-bin.zip \
		-o /gradle-${GRADLE_VERSION}-bin.zip \
	&& unzip /gradle-${GRADLE_VERSION}-bin.zip \
	&& ln -sf "/usr/local/gradle-${GRADLE_VERSION}/bin/gradle" /usr/bin/gradle \
	&& rm /gradle-${GRADLE_VERSION}-bin.zip \
	&& rm -rf /var/lib/apt/lists/* \
	&& apt-get purge -y --auto-remove

VOLUME /usr/src/app
VOLUME /root/.gradle/caches

WORKDIR /usr/src/app

ENTRYPOINT ["gradle"]
