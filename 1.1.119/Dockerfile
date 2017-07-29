FROM java:7

# A merge of:
#  https://github.com/zhilvis/docker-h2
#  https://github.com/zilvinasu/h2-dockerfile

MAINTAINER Oscar Fonts <oscar.fonts@geomati.co>

ENV DOWNLOAD https://storage.googleapis.com/google-code-archive-downloads/v2/code.google.com/h2database/h2-2009-09-26.zip
ENV DATA_DIR /opt/h2-data

RUN curl ${DOWNLOAD} -o h2.zip \
    && unzip h2.zip -d /opt/ \
    && rm h2.zip \
    && mkdir -p ${DATA_DIR}

EXPOSE 81 1521

RUN /usr/sbin/groupadd -g 1001 -f h2user
RUN ["/usr/sbin/useradd", "-m", "-g 1001", "-u 1001", "h2user"]
RUN /bin/bash -c 'echo "h2user:changeme" | /usr/sbin/chpasswd'

RUN chown -R 1001:1001 ${DATA_DIR}

USER 1001

CMD java -cp /opt/h2/bin/h2*.jar org.h2.tools.Server \
 	-web -webAllowOthers -webPort 8081 \
 	-tcp -tcpAllowOthers -tcpPort 1521 \
 	-baseDir ${DATA_DIR}
