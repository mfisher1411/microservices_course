FROM golang:1.24.3-alpine3.21 AS builder
WORKDIR /app
COPY . .
RUN go build -o grpc_server cmd/grpc_server/main.go

FROM alpine:latest
WORKDIR /app
COPY --from=builder /app/grpc_server .
COPY prod.env .
COPY local.env .