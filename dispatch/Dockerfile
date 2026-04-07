# ---------- Builder Stage ----------
FROM golang:1.25-alpine AS builder

WORKDIR /app

# Install git (required for go modules sometimes)
RUN apk add --no-cache git

# Copy go mod files first (for caching)
COPY go.mod go.sum ./

RUN go mod download

# Copy source code
COPY . .

# Build binary (static build)
RUN CGO_ENABLED=0 GOOS=linux go build -o dispatch

# ---------- Runtime Stage ----------
FROM alpine:3.19

WORKDIR /app

# Install minimal runtime deps (optional)
RUN apk add --no-cache ca-certificates

# Copy binary from builder
COPY --from=builder /app/dispatch /app/dispatch

# Create user
RUN addgroup -S roboshop && adduser -S roboshop -G roboshop \
    && chown -R roboshop:roboshop /app

USER roboshop

CMD ["/app/dispatch"]






# FROM golang:1.25-alpine
# WORKDIR /app
# COPY main.go .
# RUN go mod init dispatch || true
# RUN go mod tidy
# RUN go build -o dispatch .
# COPY . .
# CMD ["/app/dispatch"]
