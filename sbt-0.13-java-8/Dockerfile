FROM openshift/base-centos7
# TODO: Take a look at https://github.com/heroku/sbt-pkg-builder and https://github.com/heroku/heroku-buildpack-scala for pre-caching

MAINTAINER Patrick Tescher <patrickt@ticketfly.com>

ENV SBT_VERSION 0.13.8
ENV JAVA_VERSION 1.8.0

LABEL io.k8s.description="Build and run Scala applications" \
      io.k8s.display-name="SBT 0.13.8" \
      io.openshift.expose-services="9000:http" \
      io.openshift.tags="builder,scala,sbt"

ADD bintray-sbt-rpm.repo /etc/yum.repos.d/bintray-sbt-rpm.repo

RUN yum install -y --enablerepo=centosplus \
    java-${JAVA_VERSION}-openjdk java-${JAVA_VERSION}-openjdk-devel sbt-${SBT_VERSION} && \
    yum clean all -y

RUN cd /tmp; sbt about

RUN echo 1 | alternatives --config java
RUN echo 2 | alternatives --config javac

COPY ./.sti/bin/ /usr/local/sti

EXPOSE 9000

USER 1001

CMD ["usage"]
