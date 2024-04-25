FROM node:21-alpine

ARG IMAGE_CREATE_DATE
ARG IMAGE_VERSION
ARG IMAGE_SOURCE_REVISION


LABEL org.opencontainers.image.title="CaaS PoC Fujitsu!" \
      org.opencontainers.image.description="Provides a demo app to deploy to a Kubernetes cluster. It displays a message, the name of the pod and details of the node it is deployed to." \
      org.opencontainers.image.created=$IMAGE_CREATE_DATE \
      org.opencontainers.image.version=$IMAGE_VERSION \
      org.opencontainers.image.authors="Fujitsu Team" \
      org.opencontainers.image.url="http://harbor.frontedge.net/caas-poc-fujitsu/caas-poc-fujitsu" \
      org.opencontainers.image.documentation="https://github.com/eduhuelva/caas-poc-fujitsu/README.md" \
      org.opencontainers.image.vendor="Fujitsu Team" \
      org.opencontainers.image.licenses=" - " \
      org.opencontainers.image.source="https://github.com/eduhuelva/caas-poc-fujitsu.git" \
      org.opencontainers.image.revision=$IMAGE_SOURCE_REVISION 

# Create app directory
RUN mkdir -p /usr/src/app
WORKDIR /usr/src/app

# Install app dependencies
COPY package.json /usr/src/app/
RUN npm install

# Bundle app source
COPY . /usr/src/app

USER node
CMD [ "npm", "start" ]
