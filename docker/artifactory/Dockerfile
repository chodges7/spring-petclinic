FROM centos:7.9.2009 AS centos 

RUN yum -y update

RUN yum install -y java-1.8.0-openjdk-devel

RUN echo "export JAVA_HOME=/usr/lib/jvm/java-1.8.0-openjdk-1.8.0.292.b10-1.el7_9.x86_64" >> /etc/profile
RUN . /etc/profile

RUN yum install -y net-tools rsync wget curl
RUN wget https://releases.jfrog.io/artifactory/bintray-artifactory/org/artifactory/oss/jfrog-artifactory-oss/7.23.3/jfrog-artifactory-oss-7.23.3-linux.tar.gz
RUN rm -rf /var/lib/apt/lists/*

EXPOSE 8081
EXPOSE 8082

RUN mkdir jfrog
RUN mv jfrog-artifactory-oss-7.23.3-linux.tar.gz jfrog
WORKDIR /jfrog
RUN tar -xvf jfrog-artifactory-oss-7.23.3-linux.tar.gz
RUN mv artifactory-oss-7.23.3 artifactory
WORKDIR /jfrog/artifactory/app/bin

ENTRYPOINT ["./artifactoryctl"]
