FROM centos:centos7 as base

WORKDIR /usr/local

ARG RELEASE_URL

RUN yum install -y wget python-requests \
    && wget --no-check-certificate --no-cache --no-cookies -O - "https://download.splunk.com/products/universalforwarder/releases/${RELEASE_URL}" | tar -xzf - \
    && package-cleanup --leaves --all \
    && yum clean all \
    && rm -rf /var/cache

WORKDIR /usr/local/splunkforwarder/etc

COPY deploymentclient.conf apps/conf_deployment/default/
COPY splunk-launch.conf .
COPY outputs.conf system/local/


FROM centos:centos7

WORKDIR /usr/local/splunkforwarder

COPY --from=base /usr/local/splunkforwarder .

CMD ./bin/splunk start --answer-yes --accept-license --no-prompt && tail -f /dev/null