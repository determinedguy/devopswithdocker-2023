FROM golang:1.16 AS build-env

WORKDIR /app

COPY . .
ENV CGO_ENABLED=0

RUN go build

FROM alpine

WORKDIR /app

EXPOSE 8080
ENV REQUEST_ORIGIN=http://localhost:5000

COPY --from=build-env /app /app

RUN apk update && apk add ca-certificates && rm -rf /var/cache/apk/* && \
    adduser -D appuser && \
    chmod +x server

USER appuser

CMD ./server 