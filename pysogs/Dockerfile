FROM debian:bullseye-slim

WORKDIR /app
ARG PUBLICIP
ARG SESSIONID
ENV DEBIAN_FRONTEND=noninteractive

RUN apt update && apt -y upgrade
RUN apt -y install curl lsb-release apt-utils nano ucf python3-pip crudini
RUN apt-get -y install systemctl

RUN curl -so /etc/apt/trusted.gpg.d/oxen.gpg https://deb.oxen.io/pub.gpg
# Add the Oxen apt repository to your package configuration:
RUN echo "deb https://deb.oxen.io $(lsb_release -sc) main" | tee /etc/apt/sources.list.d/oxen.list

RUN apt -y update

RUN pip install requests
RUN apt -y install sogs-standalone
RUN python3 -msogs --initialize


ENTRYPOINT uwsgi --ini uwsgi.ini




