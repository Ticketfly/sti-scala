FROM ticketfly/sbt-0.13-java8-centos7

RUN curl https://downloads.typesafe.com/typesafe-activator/1.3.6/typesafe-activator-1.3.6-minimal.zip > /tmp/typesafe-activator-1.3.6-minimal.zip; \
    unzip /tmp/typesafe-activator-1.3.6-minimal.zip; \
    activator-1.3.6-minimal/activator -ivy /opt/app-root/src/.ivy2 about 2> /dev/null; \
    chown -R 1001:0 /opt/app-root/src/.ivy2; chmod -R g+rw /opt/app-root/src/.ivy2
