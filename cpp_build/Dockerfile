FROM ubuntu:18.04
# docker build -t mohamedghita/build:cpp_build /Users/mohamedghita/Devel/dockerfiles/cpp_build/
# docker push mohamedghita/build:cpp_build

# packages
RUN apt update -y \
 && apt install -y wget \
 && apt install -y git

# gcc-9
RUN apt update -y \
 && apt install -y software-properties-common \
 && add-apt-repository -y ppa:ubuntu-toolchain-r/test \
 && apt update -y \
 && apt install -y gcc-9 \
 && apt install -y g++-9 \
 && update-alternatives --install /usr/bin/gcc gcc /usr/bin/gcc-9 20 \
 && update-alternatives --install /usr/bin/g++ g++ /usr/bin/g++-9 20 \
 && apt install -y gcc-9-multilib \
 && apt install -y g++-9-multilib

 # llvm-9
 RUN version=9\
 && cd /tmp \
 && wget https://apt.llvm.org/llvm.sh \
 && chmod +x llvm.sh \
 && ./llvm.sh ${version}\
 && rm ./llvm.sh


# conan
RUN apt install -y python3-pip \
  && pip3 install conan \
  && conan config install -sf=linux https://mohamed_ghita@bitbucket.org/radalytica/conan-config.git

# cmake
RUN apt install -y wget \
  && wget -O - https://apt.kitware.com/keys/kitware-archive-latest.asc 2>/dev/null | apt-key add - \
  && apt-add-repository 'deb https://apt.kitware.com/ubuntu/ bionic main' \
  && apt update \
  && apt install -y cmake

RUN apt autoremove -y


