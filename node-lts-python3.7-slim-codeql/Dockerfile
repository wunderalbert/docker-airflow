# AUTHOR: Anna Railton
# DESCRIPTION: Container to use codeQL to build JavaScript and Python projects
# BUILD: docker build --rm -t puckel/docker-airflow .
# SOURCE: https://github.com/puckel/docker-airflow

FROM annarailton/node-lts-python3.7-slim

# Never prompts the user for choices on installation/configuration of packages
ENV DEBIAN_FRONTEND noninteractive
ENV TERM linux

RUN pip install packaging virtualenv \
    && apt-get update \
    && apt-get install -y wget unzip git curl git-core build-essential openssl libssl-dev\
    && apt-get purge --auto-remove -yqq $buildDeps \
    && apt-get autoremove -yqq --purge \
    && apt-get clean \
    && mkdir /usr/local/codeql-home \
    && git clone https://github.com/Semmle/ql /usr/local/codeql-home/codeql-repo \
    && wget -P /usr/local https://github.com/github/codeql-cli-binaries/releases/download/v2.0.0/codeql.zip \
    && unzip -o /usr/local/codeql.zip -d /usr/local/codeql-home && rm /usr/local/codeql.zip \
    && ln -s /usr/local/codeql-home/codeql/codeql /usr/bin

CMD ["codeql version"]
