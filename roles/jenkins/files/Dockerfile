FROM jenkins/jenkins:lts-alpine

ENV JENKINS_SLAVE_AGENT_PORT 50001


ENV JENKINS_OPTS --httpPort=8000
EXPOSE 8443 8000

USER root
RUN apt-get update && apt-get install -y jq
RUN curl -O https://download.docker.com/linux/static/stable/x86_64/docker-18.03.1-ce.tgz \
&& tar xzfv docker-18.03.1-ce.tgz docker/docker \
&& mv docker/docker /bin/ \
&& rm docker-18.03.1-ce.tgz
RUN curl -L "https://api.bintray.com/content/jfrog/jfrog-cli-go/\$latest/jfrog-cli-linux-amd64/jfrog?bt_package=jfrog-cli-linux-amd64" -o jfrog \
&& chmod +x jfrog \
&& mv jfrog /bin
COPY config/plugins.txt /usr/share/jenkins/ref/plugins.txt
RUN /usr/local/bin/install-plugins.sh < /usr/share/jenkins/ref/plugins.txt
