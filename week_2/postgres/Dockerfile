FROM golang:1.24.3-alpine3.21 AS builder

COPY . /github.com/mfisher1411/microservices_course/week_2/grpc/source/
WORKDIR /github.com/mfisher1411/microservices_course/week_2/grpc/source/

RUN go mod download
RUN go build -o ./bin/crud_server cmd/grpc_server/main.go

FROM alpine:latest

WORKDIR /root/
COPY --from=builder /github.com/mfisher1411/microservices_course/week_2/grpc/source/bin/crud_server .

CMD ["./crud_server"]