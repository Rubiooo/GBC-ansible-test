FROM jenkins/jenkins:lts-alpine

ENV JENKINS_SLAVE_AGENT_PORT 50001

COPY config/ssl/georgebrown.ca.crt /var/lib/jenkins/crt
COPY config/ssl/georgebrown.ca.key /var/lib/jenkins/key
ENV JENKINS_OPTS --httpPort=8000 --httpsPort=8443 --httpsCertificate=/var/lib/jenkins/crt --httpsPrivateKey=/var/lib/jenkins/key
EXPOSE 8443 8000

USER root
RUN apk update && apk add docker
COPY config/plugins.txt /usr/share/jenkins/ref/plugins.txt
RUN /usr/local/bin/install-plugins.sh < /usr/share/jenkins/ref/plugins.txt
