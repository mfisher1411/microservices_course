FROM golang:1.24.3-alpine3.21 AS builder

COPY . /github.com/mfisher1411/microservices_course/week_2/config/source/

WORKDIR /github.com/mfisher1411/microservices_course/week_2/config/source/

RUN go mod download
RUN go build -o ./bin/main ./cmd/main.go

FROM alpine:latest

WORKDIR /root/
COPY --from=builder /github.com/mfisher1411/microservices_course/week_2/config/source/bin/main ./main
# COPY --from=builder /github.com/mfisher1411/microservices_course/week_2/config/source/local.env ./.env

# <-- передаём .env как build-аргумент
ARG ENV_FILE=.env
COPY --from=builder /github.com/mfisher1411/microservices_course/week_2/config/source/${ENV_FILE} ./.env

CMD ["./main"]