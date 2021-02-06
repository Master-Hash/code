FROM node:lts-alpine as element-web

# element-web
# https://github.com/vector-im/element-web/tree/master

RUN apk add --no-cache --virtual .build-deps git \
 && cd /opt \
 && git clone --depth=1 -bmaster https://github.com/vector-im/element-web.git \
 && cd element-web \
 && yarn 
 # 配置文件——待补充

COPY config.json /opt/element-web/
WORKDIR /opt/element-web
RUN yarn build && apk del .build-deps
# 毕竟这个阶段都完了，git 就不删了吧（不是

FROM httpd:alpine

# 静态站点：
# element-web
# adarkroom（不过这个不在这里装，而是自己手动 fetch？）

COPY --from=element-web /opt/element-web/webapp /var/www/