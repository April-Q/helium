# Please use command below to build the image:
# docker build -f Dockerfile -t <image_name>:<version> .

FROM he2-centos7-jdk8:0.1

# SPARK
ENV SPARK_VERSION 2.1.1
ENV HADOOP_VERSION hadoop2.7
ENV SPARK_PREFIX spark-${SPARK_VERSION}
ENV SPARK_PACKAGE=spark-${SPARK_VERSION}-bin-${HADOOP_VERSION}

# Download Apache Spark, untar and clean up
RUN set -x && \
    curl -L -C - "http://www.apache.org/dist/spark/${SPARK_PREFIX}/${SPARK_PACKAGE}.tgz" | \
         tar -xz -C /opt && \
    cd /opt && \
    ln -s ${SPARK_PACKAGE} spark

ENV SPARK_HOME /opt/spark
ENV PATH $PATH:${SPARK_HOME}/bin:${SPARK_HOME}/sbin
ENV SPARK_CONF_DIR ${SPARK_HOME}/conf

WORKDIR /opt

ENTRYPOINT ["tail", "-f", "/var/log/lastlog"]
