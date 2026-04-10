FROM golang:1.21-alpine AS builder

WORKDIR /app
COPY app/go.mod .
RUN go mod download

COPY app/
RUN go build -o app

FROM alpine:3.18

WORKDIR /app
COPY --from=builder /app/app .

EXPOSE 8080

CMD ["./app"]
