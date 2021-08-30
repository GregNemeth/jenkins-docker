FROM clearlinux:latest
LABEL maintainer="gregmix88@gmail.com"

ENV LANG C.UTF-8

RUN swupd update && swupd bundle-add \
  zip \
  wget \
  curl \
  openssh-client \
  unzip \
  java11-basic \


ARG user=jenkins
ARG group=jenkins
ARG uid=1000
ARG gid=1000
ARG http_port=8080
ARG agent_port=50000
ARG JENKINS_VERSION=2.289
ARG TINI_VERSION=v0.17.0

# jenkins.war checksum, download will be validated using it
ARG JENKINS_SHA=085f597edeb0d49d54d7653f3742ba31ed72b8a1a2b053d2eb23fd806c6a5393

# Can be used to customize where jenkins.war get downloaded from
ARG JENKINS_URL=https://repo.jenkins-ci.org/public/org/jenkins-ci/main/jenkins-war/${JENKINS_VERSION}/jenkins-war-${JENKINS_VERSION}.war

ENV JENKINS_VERSION ${JENKINS_VERSION}
ENV JENKINS_HOME /var/jenkins_home
ENV JENKINS_SLAVE_AGENT_PORT ${agent_port}
ENV JENKINS_UC https://updates.jenkins.io
ENV JENKINS_UC_EXPERIMENTAL=https://updates.jenkins.io/experimental
ENV JAVA_OPTS="-Xmx8192m"
ENV JENKINS_OPTS="--handlerCountMax=300 --logfile=/var/log/jenkins/jenkins.log  --webroot=/var/cache/jenkins/war"
ENV COPY_REFERENCE_FILE_LOG $JENKINS_HOME/copy_reference_file.log

