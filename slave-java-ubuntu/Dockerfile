FROM docker.io/fhwendy/jenkins-slave-base-ubuntu:latest

MAINTAINER Adam Saleh <asaleh@redhat.com>

USER root

ENV MAVEN_VERSION=3.1.1

RUN (curl -v https://www.apache.org/dist/maven/maven-3/$MAVEN_VERSION/binaries/apache-maven-$MAVEN_VERSION-bin.tar.gz | \
    tar -zx -C /usr/local) && \
    ln -sf /usr/local/apache-maven-$MAVEN_VERSION/bin/mvn /usr/local/bin/mvn && \
    mkdir -p /var/log/feedhenry/core/ && \
    chown -R 1001:0 /var/log/feedhenry/core/ && \
    chmod -R g+w /var/log/feedhenry/core/ && \
    mkdir -p /etc/feedhenry/ && \
    chown -R 1001:0 /etc/feedhenry/ && \
    chmod -R g+w /etc/feedhenry/ && \
    apt-get install -y mysql-client && \
    apt-get install -y netcat

USER 1001
RUN mkdir -p /home/jenkins/.m2
ADD ./contrib/settings.xml $HOME/.m2/