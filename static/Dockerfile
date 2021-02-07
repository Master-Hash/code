FROM node:lts-alpine as element-web

# element-web
# https://github.com/vector-im/element-web/tree/master

RUN apk add --no-cache --virtual .build-deps git \
 && cd /opt \
 && git clone --depth=1 -bmaster https://github.com/vector-im/element-web.git

COPY config.json /opt/element-web/
WORKDIR /opt/element-web
RUN yarn && yarn build && apk del .build-deps
# 毕竟这个阶段都完了，git 就不删了吧（不是

FROM httpd:alpine

# 静态站点：
# element-web
# adarkroom（不过这个不在这里装，而是自己手动 fetch？）

# 动态站点：还不清楚自己想装什么呢，WP 已经有点烦了（

COPY --from=element-web /opt/element-web/webapp /var/www/element-web
