FROM jenkins/jenkins:latest

# Required plugins
COPY plugins.txt /usr/share/jenkins/ref/plugins.txt
RUN /usr/local/bin/install-plugins.sh < /usr/share/jenkins/ref/plugins.txt

# Manually add the plugins
COPY usr/share/jenkins/ref/plugins/github-autostatus.hpi /usr/share/jenkins/ref/plugins/github-autostatus.hpi