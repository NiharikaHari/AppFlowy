# Dockerfile
FROM rust:latest AS builder
WORKDIR /app
COPY . .
RUN apt update && apt install -y protobuf-compiler
RUN cd collab-server && cargo build --release

FROM debian:buster-slim
WORKDIR /app
COPY --from=builder /app/target/release/collab-server /usr/local/bin/collab-server
CMD ["collab-server"]
