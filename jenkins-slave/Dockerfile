FROM jenkinsci/jnlp-slave
USER root


#Installing Maven

RUN apt-get update &&\
    apt-get install -y --no-install-recommends \
    	maven \
	wget \
	curl &&\
    apt-get clean &&\
    apt-get autoclean &&\
    rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* /var/cache/*


#Installing Docker
ENV DOCKER_VERSION 17.06.0-ce
RUN wget https://download.docker.com/linux/static/stable/x86_64/docker-${DOCKER_VERSION}.tgz &&\
	tar -xvf docker-${DOCKER_VERSION}.tgz &&\
	cp docker/docker* /usr/bin/ &&\
	chown jenkins:jenkins /usr/bin/docker*

#Installing kubectl
RUN wget https://storage.googleapis.com/kubernetes-release/release/v1.7.2/bin/linux/amd64/kubectl && \
	chmod +x kubectl && \
	mv kubectl /usr/bin/

#Install Helm
RUN wget https://storage.googleapis.com/kubernetes-helm/helm-v2.10.0-linux-amd64.tar.gz && \
	tar -zxvf helm-v2.10.0-linux-amd64.tar.gz && \
	mv linux-amd64//helm /usr/local/bin/helm && \
	rm -rf linux-amd64 helm-v2.10.0-linux-amd64.tar.gz
	

#End of Dockerfile
USER jenkins

