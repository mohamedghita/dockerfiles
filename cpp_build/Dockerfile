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

 # llvm-9 && libc++-dev
 RUN version=9\
 && cd /tmp \
 && wget https://apt.llvm.org/llvm.sh \
 && chmod +x llvm.sh \
 && ./llvm.sh ${version}\
 && rm ./llvm.sh\
 && apt install -y libc++-dev\
 && apt install -y libc++abi-dev\
 && update-alternatives --install /usr/bin/clang clang /usr/bin/clang-9 20 \
 && update-alternatives --install /usr/bin/clang++ clang++ /usr/bin/clang++-9 20


# conan
RUN apt install -y python3-pip \
  && pip3 install conan --upgrade

# cmake
RUN apt install -y wget \
  && wget https://github.com/Kitware/CMake/releases/download/v3.19.3/cmake-3.19.3-Linux-x86_64.sh \
  && chmod +x ./cmake-3.19.3-Linux-x86_64.sh \
  && ./cmake-3.19.3-Linux-x86_64.sh --prefix=/usr --skip-license

RUN apt autoremove -y


