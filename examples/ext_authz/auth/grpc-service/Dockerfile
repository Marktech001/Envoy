FROM golang:1.24.6-bullseye@sha256:2cdc80dc25edcb96ada1654f73092f2928045d037581fa4aa7c40d18af7dd85a as builder

COPY . /app
RUN make -C /app/grpc-service

FROM debian:bullseye-slim

COPY --from=builder /app/grpc-service/server /app/server
CMD ["/app/server", "-users", "/etc/users.json"]
