FROM jenkins/jenkins:lts

USER root

# Add docker to the jenkins image to allow for docker-workflow plugin https://github.com/jenkinsci/docker-workflow-plugin
RUN apt update && apt install -y \
    apt-transport-https \
    ca-certificates \
    curl \
    gnupg-agent \
    software-properties-common

RUN curl -fsSL https://download.docker.com/linux/debian/gpg | apt-key add -
RUN add-apt-repository \
   "deb [arch=amd64] https://download.docker.com/linux/debian \
   $(lsb_release -cs) \
   stable"
RUN apt update && apt install -y docker-ce docker-ce-cli containerd.io

RUN usermod -aG docker jenkins

# Required plugins
COPY plugins.txt /usr/share/jenkins/ref/plugins.txt
RUN /usr/local/bin/install-plugins.sh < /usr/share/jenkins/ref/plugins.txt

# Config Override
COPY usr/share/jenkins/ref/org.jenkinsci.plugins.githubautostatus.BuildStatusConfig.xml /usr/share/jenkins/ref/org.jenkinsci.plugins.githubautostatus.BuildStatusConfig.xml.override