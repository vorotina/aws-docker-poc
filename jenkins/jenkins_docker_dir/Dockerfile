FROM jenkins

USER root

RUN cd /opt  && \
wget https://archive.apache.org/dist/maven/maven-3/3.3.1/binaries/apache-maven-3.3.1-bin.tar.gz && \
tar xzf apache-maven-3.3.1-bin.tar.gz

USER jenkins

ENV PATH=$PATH:/opt/apache-maven-3.3.1/bin/
ENV M2_HOME=/opt/apache-maven-3.3.1/
