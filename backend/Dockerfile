FROM golang:1.26-alpine AS builder
WORKDIR /app

COPY go.mod go.sum ./
RUN go mod download

COPY . .
RUN go build -o skillpulse

FROM alpine:3.23
WORKDIR /app

COPY --from=builder /app/skillpulse .

EXPOSE 8080
CMD ["./skillpulse"]