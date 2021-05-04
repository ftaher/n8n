FROM registry.access.redhat.com/ubi7/ubi

ARG N8N_VERSION=0.36.1

RUN if [ -z "$N8N_VERSION" ] ; then echo "The N8N_VERSION argument is missing!" ; exit 1; fi
USER 0

RUN \
	yum  install -y  gcc-c++ make

RUN \
	curl -sL https://rpm.nodesource.com/setup_12.x | bash -

RUN \
	yum install -y  nodejs

# Set a custom user to not have n8n run as root
USER root

RUN npm_config_user=root npm install -g n8n@${N8N_VERSION}

WORKDIR /data

USER 1001

CMD "n8n"
