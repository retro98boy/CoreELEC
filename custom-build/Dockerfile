# docker buildx build -t retro98boy/coreelec-dev:latest .

# Ubuntu Focal无法编译CoreELEC 22
# linux-libc-dev版本低导致`/usr/include/linux/fsverity.h`中不含`struct fsverity_read_metadata_arg`的定义
# 从而导致编译host:e2fsprogs-1.47.3报错
FROM ubuntu:noble

ARG DEBIAN_FRONTEND=noninteractive
SHELL ["/usr/bin/bash", "-c"]

# 安装语系、时区、sudo等基础包
RUN sed -i 's/archive.ubuntu.com/mirrors.ustc.edu.cn/g' /etc/apt/sources.list \
 && apt update \
 && apt upgrade -y \
 && apt install -y locales tzdata sudo

# 设置时区和语系
RUN if [ -e /etc/localtime ]; then rm /etc/localtime; fi; ln -svf /usr/share/zoneinfo/Asia/Shanghai /etc/localtime \
 && echo -e 'en_US.UTF-8 UTF-8\nzh_CN.UTF-8 UTF-8' >> /etc/locale.gen \
 && locale-gen \
 && echo 'LANG=en_US.UTF-8' > /etc/locale.conf
ENV LANG=en_US.UTF-8

# 设置用户，Ubuntu Noble自带ubuntu用户
RUN usermod -aG sudo ubuntu \
 && passwd -d ubuntu \
 && echo '%sudo ALL=(ALL) NOPASSWD: ALL' >> /etc/sudoers \
 && echo 'ubuntu ALL=(ALL) NOPASSWD: ALL' >> /etc/sudoers

# 安装构建工具
# https://wiki.coreelec.org/coreelec:build_ce
RUN apt install -y build-essential git python3 xfonts-utils xsltproc default-jre libxml-parser-perl libjson-perl \
libncurses5-dev bc gawk xfonts-utils wget zip zstd libparse-yapp-perl gperf lzop unzip patchutils rdfind cpio rsync curl \
file xxd

# 清理
RUN apt autopurge -y && apt autoclean

RUN mkdir -p /workspace && chown ubuntu /workspace

WORKDIR /workspace
USER ubuntu
