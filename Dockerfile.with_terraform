FROM amazon/aws-cli

ENV AWS_REGION=ap-southeast-2
ENV AWS_PROFILE=default

RUN yum update -y \
  && yum install -y less groff yum-utils openssh-clients\
  && yum clean all

RUN yum-config-manager --add-repo https://rpm.releases.hashicorp.com/AmazonLinux/hashicorp.repo
RUN yum install -y terraform

RUN curl "https://s3.amazonaws.com/session-manager-downloads/plugin/latest/linux_64bit/session-manager-plugin.rpm" -o "session-manager-plugin.rpm"

RUN yum install -y session-manager-plugin.rpm

RUN session-manager-plugin

RUN mkdir -p /root/.ssh
ADD config /root/.ssh/
RUN chmod 400 /root/.ssh/config

WORKDIR /aws
ENTRYPOINT ["bash","-c"]