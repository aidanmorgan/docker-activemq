FROM amazoncorretto:21-alpine


ENV ACTIVEMQ_VERSION 6.0.1
ENV ACTIVEMQ apache-activemq-$ACTIVEMQ_VERSION
ENV ACTIVEMQ_TCP=61616 ACTIVEMQ_AMQP=5672 ACTIVEMQ_STOMP=61613 ACTIVEMQ_MQTT=1883 ACTIVEMQ_WS=61614 ACTIVEMQ_UI=8161

ENV ACTIVEMQ_HOME /opt/activemq

RUN wget -O $ACTIVEMQ-bin.tar.gz "https://archive.apache.org/dist/activemq/$ACTIVEMQ_VERSION/$ACTIVEMQ-bin.tar.gz"

RUN tar xzf $ACTIVEMQ-bin.tar.gz -C  /opt
RUN ln -s /opt/$ACTIVEMQ $ACTIVEMQ_HOME
RUN adduser -D -h $ACTIVEMQ_HOME activemq activemq
RUN chown -R activemq:activemq /opt/$ACTIVEMQ
RUN chown -h activemq:activemq $ACTIVEMQ_HOME 

USER activemq

WORKDIR $ACTIVEMQ_HOME
EXPOSE $ACTIVEMQ_TCP $ACTIVEMQ_AMQP $ACTIVEMQ_STOMP $ACTIVEMQ_MQTT $ACTIVEMQ_WS $ACTIVEMQ_UI

CMD ["/bin/sh", "-c", "bin/activemq console"]
