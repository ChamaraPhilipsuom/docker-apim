FROM docker.wso2.com/wso2am:2.1.0

COPY pattern-3/keymanager/carbon/ /mnt/wso2-artifacts

COPY artifacts/mysql-connector-java-5.1.34-bin.jar /mnt/wso2-artifacts/repository/components/lib/

USER root

RUN rm -r /mnt/wso2am-2.1.0/repository/deployment/server/synapse-configs/default/inbound-endpoints/WebSocketInboundEndpoint.xml

RUN chmod 755 /mnt/wso2-artifacts/bin
RUN chmod -R 755 /mnt/wso2-artifacts/repository

COPY pattern-3/scripts/image-init.sh /usr/local/bin
RUN chmod +x /usr/local/bin/image-init.sh
RUN sed -ie 's^#!/bin/bash^ ^g' /usr/local/bin/init.sh
RUN cat /usr/local/bin/init.sh >> /usr/local/bin/image-init.sh
RUN rm /usr/local/bin/init.sh
RUN mv /usr/local/bin/image-init.sh /usr/local/bin/init.sh
