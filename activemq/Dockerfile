FROM openjdk:8-jre-alpine

# define activemq version and workdir
ENV ACTIVEMQ_VERSION 5.15.11
ENV ACTIVEMQ_WORKDIR /app

# create the work dir
RUN mkdir -p $ACTIVEMQ_WORKDIR

# copy activemq
COPY activemq/apache-activemq-5.15.11-bin.tar.gz .

# download active mq and extract
RUN tar -xzf apache-activemq-5.15.11-bin.tar.gz -C $ACTIVEMQ_WORKDIR

# create link
RUN ln -s $ACTIVEMQ_WORKDIR/apache-activemq-$ACTIVEMQ_VERSION $ACTIVEMQ_WORKDIR/activemq

# change work dir
WORKDIR $ACTIVEMQ_WORKDIR/activemq

COPY activemq/activemq.xml $ACTIVEMQ_WORKDIR/activemq/conf

# EXPOSE PORTS
# ACTIVEMQ UI
EXPOSE 8161
# ACTIVEMQ TCP
EXPOSE 61613
EXPOSE 61616

# start
CMD ["/bin/sh", "-c", "bin/activemq console"]