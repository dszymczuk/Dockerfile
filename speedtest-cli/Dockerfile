FROM ubuntu

RUN apt-get update && apt-get install -y curl

RUN curl -s https://install.speedtest.net/app/cli/install.deb.sh | bash

RUN apt-get install -y speedtest

ENTRYPOINT ["/usr/bin/speedtest", "--accept-license", "--accept-gdpr"]
