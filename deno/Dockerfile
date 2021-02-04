FROM rust:latest

WORKDIR /usr/local/cargo/bin

RUN cargo install deno \
 # 用于 debug
 && ls .

FROM busybox:latest

RUN mkdir -p /usr/local/bin

COPY --from=0 {deno,denort} /usr/local/bin

CMD [ "deno" ]
