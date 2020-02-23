FROM ubuntu:18.04
# docker build -t cpp_build_linux -f /Users/mohamedghita/Devel/conan-radalytica/conan-config/cpp_build.dockerfile .

# gcc-9
RUN apt update -y
RUN apt install -y software-properties-common
RUN add-apt-repository -y ppa:ubuntu-toolchain-r/test
RUN apt install -y gcc-9 && apt install -y g++-9 && update-alternatives --install /usr/bin/gcc gcc /usr/bin/gcc-9 20 && update-alternatives --install /usr/bin/g++ g++ /usr/bin/g++-9 20
RUN apt install -y gcc-9-multilib
RUN apt install -y git

# conan
RUN apt install -y python3-pip
RUN pip3 install conan
RUN conan config install -sf=linux https://mohamed_ghita@bitbucket.org/radalytica/conan-config.git

# cmake
RUN apt install -y wget
RUN wget -O - https://apt.kitware.com/keys/kitware-archive-latest.asc 2>/dev/null | apt-key add -
RUN apt-add-repository 'deb https://apt.kitware.com/ubuntu/ bionic main'
RUN apt update
RUN apt install -y cmake



