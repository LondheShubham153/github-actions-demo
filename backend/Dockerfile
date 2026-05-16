# Stage 1: Build
FROM golang:1.26-alpine AS builder

WORKDIR /app

COPY . .
RUN go mod tidy
RUN CGO_ENABLED=0 GOOS=linux go build -trimpath -ldflags='-s -w' -o /skillpulse .

# Stage 2: Run
FROM scratch

COPY --from=builder /skillpulse /skillpulse

EXPOSE 8080
ENTRYPOINT ["/skillpulse"]
