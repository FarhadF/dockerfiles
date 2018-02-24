FROM debian:stable-slim

ENV JAVA_VERSION_MAJOR=7 \
    JAVA_VERSION_MINOR=80 \
    JAVA_VERSION_BUILD=15 \
    JAVA_PACKAGE=jdk \
    JAVA_HOME=/opt/jdk1.${JAVA_VERSION_MAJOR}.0_${JAVA_VERSION_MINOR} \
    JVM_OPTS="" \
    LANG=C.UTF-8
COPY ./jdk-7u80-linux-x64.tar.gz /jdk-7u80-linux-x64.tar.gz
COPY ./UnlimitedJCEPolicyJDK7.zip /UnlimitedJCEPolicyJDK7.zip
RUN apt-get update -q && \
    tar xvzf /jdk-7u80-linux-x64.tar.gz -C /opt/ && \
    apt-get install -q -y --no-install-recommends ca-certificates curl unzip && \
    unzip -jo -d ${JAVA_HOME}/jre/lib/security /UnlimitedJCEPolicyJDK7.zip && \
    rm -rf ${JAVA_HOME}/*src.zip \
           ${JAVA_HOME}/lib/missioncontrol \
           ${JAVA_HOME}/lib/visualvm \
           ${JAVA_HOME}/lib/*javafx* \
           ${JAVA_HOME}/jre/plugin \
           ${JAVA_HOME}/jre/bin/javaws \
           ${JAVA_HOME}/jre/bin/jjs \
           ${JAVA_HOME}/jre/bin/keytool \
           ${JAVA_HOME}/jre/bin/orbd \
           ${JAVA_HOME}/jre/bin/pack200 \
           ${JAVA_HOME}/jre/bin/policytool \
           ${JAVA_HOME}/jre/bin/rmid \
           ${JAVA_HOME}/jre/bin/rmiregistry \
           ${JAVA_HOME}/jre/bin/servertool \
           ${JAVA_HOME}/jre/bin/tnameserv \
           ${JAVA_HOME}/jre/bin/unpack200 \
           ${JAVA_HOME}/jre/lib/javaws.jar \
           ${JAVA_HOME}/jre/lib/deploy* \
           ${JAVA_HOME}/jre/lib/desktop \
           ${JAVA_HOME}/jre/lib/*javafx* \
           ${JAVA_HOME}/jre/lib/*jfx* \
           ${JAVA_HOME}/jre/lib/amd64/libdecora_sse.so \
           ${JAVA_HOME}/jre/lib/amd64/libprism_*.so \
           ${JAVA_HOME}/jre/lib/amd64/libfxplugins.so \
           ${JAVA_HOME}/jre/lib/amd64/libglass.so \
           ${JAVA_HOME}/jre/lib/amd64/libgstreamer-lite.so \
           ${JAVA_HOME}/jre/lib/amd64/libjavafx*.so \
           ${JAVA_HOME}/jre/lib/amd64/libjfx*.so \
           ${JAVA_HOME}/jre/lib/ext/jfxrt.jar \
           ${JAVA_HOME}/jre/lib/ext/nashorn.jar \
           ${JAVA_HOME}/jre/lib/oblique-fonts \
           ${JAVA_HOME}/jre/lib/plugin.jar \
           /tmp/* /var/cache/apk/* && \
    apt-get remove --purge -y ca-certificates curl unzip && \
    apt-get autoremove --purge -y && \
    apt-get clean && \
rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* /UnlimitedJCEPolicyJDK7.zip /jdk-7u80-linux-x64.tar.gz
ENV PATH $PATH:$JAVA_HOME/bin
