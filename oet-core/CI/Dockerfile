FROM ubuntu

MAINTAINER oet-team

RUN apt-get update && apt-get install -y \
    git \
    curl \
    openjdk-8-jdk \
    ruby && \
    curl -sL https://deb.nodesource.com/setup_7.x | bash && apt-get install -y nodejs  && \
    npm install -g grunt
