FROM golang:1.25-alpine
WORKDIR /app
COPY main.go .
RUN go mod init dispatch || true
RUN go mod tidy
RUN go build -o dispatch .
COPY . .
CMD ["/app/dispatch"]
