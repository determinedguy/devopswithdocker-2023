FROM golang:1.16

WORKDIR /app
EXPOSE 8080
ENV REQUEST_ORIGIN=http://localhost:5000
COPY . .

RUN go build

CMD ./server