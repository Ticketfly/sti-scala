FROM ticketfly/scala:sbt-0.13-java8-centos7

COPY populate-play-ivy-cache /tmp/populate-play-ivy-cache
RUN /tmp/populate-play-ivy-cache
RUN chown -R 1001:0 /opt/app-root/src/.ivy2; chmod -R g+rw /opt/app-root/src/.ivy2
