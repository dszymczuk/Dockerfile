FROM jenkins/jenkins:lts
MAINTAINER Damian Szymczuk
USER root

# Install prerequisites stuff
RUN apt-get update && \
    apt-get -y install apt-transport-https \
      ca-certificates \
      curl \
      gnupg2 \
      software-properties-common 

RUN curl -fsSL https://download.docker.com/linux/$(. /etc/os-release; echo "$ID")/gpg > /tmp/dkey; apt-key add /tmp/dkey 

RUN  add-apt-repository \
      "deb [arch=amd64] https://download.docker.com/linux/$(. /etc/os-release; echo "$ID") \
      $(lsb_release -cs) \
      stable"

# Install the latest Docker CE binaries   
RUN apt-get update && \
   apt-get -y install docker-ce
   
# Get latest docker compose released tag
RUN COMPOSE_VERSION=$(curl -s https://api.github.com/repos/docker/compose/releases/latest | grep 'tag_name' | cut -d\" -f4)

# Install docker-compose
RUN sh -c "curl -L https://github.com/docker/compose/releases/download/${COMPOSE_VERSION}/docker-compose-`uname -s`-`uname -m` > /usr/local/bin/docker-compose"
RUN chmod +x /usr/local/bin/docker-compose

# Clean up
RUN rm -rf /var/lib/apt/lists/*
