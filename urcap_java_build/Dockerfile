FROM ubuntu:18.04
# docker build -t mohamedghita/build:urcap_java_build /Users/mohamedghita/Devel/dockerfiles/urcap_java_build
# docker push mohamedghita/build:urcap_java_build

# update apt and 
RUN apt-get update \
  && apt install -y wget \
  && apt install -y unzip

# install java 6 and 8
RUN cd /opt \
  && wget https://www.dropbox.com/s/fyi45uruw277nls/jdk-6u45-linux-x64.bin \
  && chmod +x ./jdk-6u45-linux-x64.bin \
  && ./jdk-6u45-linux-x64.bin \
  && rm ./jdk-6u45-linux-x64.bin \
  && wget https://www.dropbox.com/s/gyd06y6lkj1pvum/jdk-8u241-linux-x64.tar \
  && tar -xf ./jdk-8u241-linux-x64.tar \
  && rm ./jdk-8u241-linux-x64.tar \
  && rm -rf /opt/default-jdk \
  && ln -s /opt/jdk1.8.0_241 /opt/default-jdk
#  && rm -rf /opt/default-jdk \
#  && ln -s /opt/jdk1.6.0_45 /opt/default-jdk
  
ENV JAVA_HOME="/opt/default-jdk"
ENV PATH="${JAVA_HOME}/bin:${PATH}"

# maven ${version}
RUN version=3.2.5 \
  && cd /opt \
  && rm -rf /opt/pache-maven* \
  && wget https://downloads.apache.org/maven/maven-3/${version}/binaries/apache-maven-${version}-bin.tar.gz \
  && tar -xf apache-maven-${version}-bin.tar.gz \
  && rm apache-maven-${version}-bin.tar.gz \
  && rm -rf apache-maven \
  && ln -s apache-maven-${version} apache-maven

ENV M2_HOME="/opt/apache-maven" \
    MAVEN_HOME="/opt/apache-maven"
ENV PATH="${M2_HOME}/bin:${PATH}"

# URCAP
RUN version=1.9.0 \
  && rm -rf /opt/default-jdk \
  && ln -s /opt/jdk1.8.0_241 /opt/default-jdk \
  && cd /opt \
  && rm -rf /opt/sdk-${version}* \
  && wget https://urplus-developer-site.s3-eu-west-1.amazonaws.com/sdk/sdk-${version}.zip \
  && mkdir sdk-${version} && cd sdk-${version} \
  && unzip ../sdk-${version}.zip \
  && cat  ./install.sh | sed -e 's/\<sudo\>//g'> ./install_no_sudo.sh \
  && chmod +x ./install_no_sudo.sh \
  && apt update \
  && apt install -y dialog \
  && apt install -y sshpass \
  && apt install -y python \
  && apt install -y ant \
  && yes | ./install_no_sudo.sh \
  && cd /opt && rm -rf /opt/sdk-${version}* \
  && rm -rf /opt/default-jdk \
  && ln -s /opt/jdk1.6.0_45 /opt/default-jdk \
  && ls ~/.m2
