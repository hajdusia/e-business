# Pull base image
FROM ubuntu:14.04

RUN apt-get update
RUN apt-get install -y software-properties-common

# Java
RUN add-apt-repository -y ppa:webupd8team/java
RUN apt-get update
RUN echo "oracle-java8-installer shared/accepted-oracle-license-v1-1 select true" | debconf-set-selections
RUN apt-get install -y --allow-unauthenticated oracle-java8-installer
RUN apt-get install -y oracle-java8-set-default

# Scala
RUN apt-get remove scala-library scala
RUN wget http://scala-lang.org/files/archive/scala-2.12.1.deb
RUN dpkg -i scala-2.12.1.deb
RUN apt-get install -y scala

# SBT
RUN echo "deb https://dl.bintray.com/sbt/debian /" | tee -a /etc/apt/sources.list.d/sbt.list
RUN apt-get install -y apt-transport-https
RUN apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv 2EE0EA64E40A89B84B2DF73499E82A75642AC823
RUN apt-get update
RUN apt-get install -y sbt

# Set port
EXPOSE 9000

# Set the working directory to /app
WORKDIR /app

RUN git clone https://github.com/taiwotman/play-slick-mysql.git
WORKDIR /app/play-slick-mysql
CMD sbt run
