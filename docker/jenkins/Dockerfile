# 2) grab apline linux base image
FROM alpine:3.14

# 3) install needed tools
RUN apk add wget \
      && apk add sudo \
      && apk add openrc \
      && apk add fontconfig \
      && apk add freetype \
      && apk add openjdk11 \
      && apk add ttf-dejavu \
      && apk add git \
      && apk add xvfb \
      && apk add go \
      && apk add curl \
      && apk add maven

# 3a) update all the packages 
RUN apk update \
      && apk upgrade \
      && rm -rf /var/lib/apt/lists/*

# 4) expose port 8080
EXPOSE 8080

# 5) add and change to new user
ARG USER=myuser
ENV HOME /home/$USER

RUN adduser -D $USER
USER $USER
WORKDIR $HOME

# 6) add an entrypoint instruction to run jenkins
RUN wget https://get.jenkins.io/war-stable/2.303.2/jenkins.war
ENTRYPOINT ["java", "-jar", "jenkins.war"]
