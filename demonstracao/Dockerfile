FROM eclipse-temurin:21-jdk

ARG ANT_VERSION=1.10.15
ADD https://archive.apache.org/dist/ant/binaries/apache-ant-${ANT_VERSION}-bin.tar.gz /tmp/ant.tar.gz
RUN tar -xzf /tmp/ant.tar.gz -C /opt \
 && mv /opt/apache-ant-${ANT_VERSION} /opt/ant \
 && rm /tmp/ant.tar.gz

ENV ANT_HOME=/opt/ant
ENV PATH="${ANT_HOME}/bin:${PATH}"

WORKDIR /demo
CMD ["bash"]
