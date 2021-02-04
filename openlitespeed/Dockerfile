FROM alpine:latest

ARG OLS_VERSION=1.7.8

# 安装依赖
# 获取源代码
# 安装

RUN apk add --no-cache --virtual .build-deps-ols \
    # 安装依赖
    build-base \
        libtool \
        linux-headers \
        bsd-compat-headers \
        automake autoconf \
        pkgconf \
        cmake \
        go \
        git \
        curl \
        expat-dev zlib-dev \
    # 获取源代码
    && git clone -b ${OLS_VERSION} --depth=1 https://github.com/litespeedtech/openlitespeed.git \
    && 来日填坑



    