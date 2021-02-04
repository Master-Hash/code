FROM rust:latest

#WORKDIR /usr/local/cargo/bin

RUN cargo install deno \
 # 用于 debug
 && ls /usr/local/cargo/bin

FROM busybox:latest

RUN mkdir -p /usr/local/bin

COPY --from=0 ["/usr/local/cargo/bin/deno", "/usr/local/cargo/bin/denort", "/usr/local/bin/"]

CMD [ "deno" ]
