FROM centos:centos7 as base

WORKDIR /usr/local

ARG RELEASE_URL

RUN yum install -y wget python-requests \
	&& wget --no-check-certificate --no-cache --no-cookies -O - "https://download.splunk.com/products/splunk/releases/${RELEASE_URL}" | tar -xzf - \
	&& package-cleanup --leaves --all \
	&& yum clean all \
	&& rm -rf /var/cache

WORKDIR /usr/local/splunk/etc

COPY inputs.conf system/local/
COPY splunk-launch.conf .


FROM centos:centos7

WORKDIR /usr/local/splunk

COPY --from=base /usr/local/splunk .

EXPOSE 8000
EXPOSE 8089
EXPOSE 9997

CMD ./bin/splunk start --answer-yes --accept-license --no-prompt --seed-passwd admin1234 && tail -f /dev/null