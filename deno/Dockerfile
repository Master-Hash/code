FROM rust:latest

# 吾未见其明也
# ENV V8_FROM_SOURCE=1

ENV RUSTFLAGS="-C target-feature=-crt-static"
# 如果在本地构建，可以加入为本地优化的参数

RUN cargo install -vv deno \
 # 懂的都懂
 && strip /usr/local/cargo/bin/deno && strip /usr/local/cargo/bin/denort \
 # 用于 debug
 && ls /usr/local/cargo/bin \
 && deno --version

FROM debian:buster-slim

COPY --from=0 ["/usr/local/cargo/bin/deno", "/usr/local/cargo/bin/denort", "/usr/local/bin/"]

CMD [ "deno" ]
