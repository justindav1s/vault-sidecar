FROM centos

RUN yum -y update && yum -y install epel-release && yum -y install jq wget curl unzip

RUN groupadd vault && \
    adduser -g vault vault && \
    mkdir /vault && \
    chown -R vault:vault /vault && \
    chmod -R 777 /vault


WORKDIR /vault

RUN wget https://github.com/openshift/origin/releases/download/v3.11.0/openshift-origin-client-tools-v3.11.0-0cbc58b-linux-64bit.tar.gz

RUN tar zxvf openshift-origin-client-tools-v3.11.0-0cbc58b-linux-64bit.tar.gz && \
    cp openshift-origin-client-tools-v3.11.0-0cbc58b-linux-64bit/oc .

RUN wget https://releases.hashicorp.com/vault/1.1.2/vault_1.1.2_linux_amd64.zip && \
    unzip vault_1.1.2_linux_amd64.zip && ls -ltr


ADD getsecrets.sh /vault

ADD remote_test.sh /vault

USER vault

CMD ["./getsecrets.sh"]