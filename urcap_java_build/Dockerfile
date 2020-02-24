FROM ubuntu:18.04
# docker build -t mohamedghita/build:urcap_java_build /Users/mohamedghita/Devel/dockerfiles/urcap_java_build
# docker push mohamedghita/build:urcap_java_build

# update apt and 
RUN apt-get update \
  && apt install -y wget \
  && apt install -y unzip

# install java 8 and maven
RUN apt update -y \
 && apt install -y software-properties-common \
 && add-apt-repository ppa:openjdk-r/ppa \
 && apt update \
 && apt install -y openjdk-8-jdk \
 && apt install -y maven

# URCAP
RUN version=1.9.0 \
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
  && cd /opt && rm -rf /opt/sdk-${version}*
  
