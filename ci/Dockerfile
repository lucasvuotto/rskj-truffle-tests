FROM node:14-buster-slim

RUN apt-get update && apt-get install -yqq --no-install-recommends \
    build-essential ca-certificates git netcat-openbsd python3

ENV JAVA_HOME=/opt/java/openjdk
COPY --from=eclipse-temurin:11-jre $JAVA_HOME $JAVA_HOME
ENV PATH="${JAVA_HOME}/bin:${PATH}"

USER node
WORKDIR /home/node

COPY --chown=node:node package*.json ./
RUN npm install && npm install truffle@5.6.8
COPY --chown=node:node . ./

# Eases interoperatibility with resources, inputs and outputs.
USER root
